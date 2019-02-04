---
ms.date: 10/31/2017
keywords: DSC, powershell, configuração, a configuração
title: Proteger o ficheiro MOF
ms.openlocfilehash: 6c2aadb75ac617d9b845ef387f292b8156bb8889
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688330"
---
# <a name="securing-the-mof-file"></a>Proteger o ficheiro MOF

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC gerencia a configuração de nós do servidor ao aplicar as informações armazenadas num ficheiro MOF, em que o Gestor de configuração Local (LCM) implementa o estado final desejada.
Uma vez que este ficheiro contém os detalhes da configuração, é importante para mantê-lo seguro.
Este tópico descreve como garantir que o nó de destino tiver encriptados o ficheiro.

A partir do PowerShell versão 5.0, todo o arquivo MOF é encriptado por predefinição quando é aplicada para o nó com o `Start-DSCConfiguration` cmdlet.
O processo descrito neste artigo, é necessário apenas quando implementar uma solução utilizando o protocolo de serviço de solicitação, se os certificados não são geridos, para garantir que configurações transferidas pelo nó de destino podem ser desencriptadas e leia pelo sistema antes de estas são aplicadas (por exemplo, o serviço de solicitação disponível no Windows Server).
Nós registados [DSC de automatização do Azure](https://docs.microsoft.com/azure/automation/automation-dsc-overview) terão automaticamente certificados instalado e gerido pelo serviço sem sobrecarga administrativa necessária.

> [!NOTE]
> Este tópico aborda os certificados utilizados para encriptação.
> Para a encriptação, um certificado auto-assinado é suficiente, porque a chave privada é sempre mantida segredo e de encriptação não implica a confiança do documento.
> Certificados autoassinados devem *não* ser utilizados para fins de autenticação.
> Deve utilizar um certificado de uma confiança autoridade de certificação (AC) para efeitos de autenticação.

## <a name="prerequisites"></a>Pré-requisitos

Para encriptar com êxito as credenciais utilizadas para proteger uma configuração de DSC, certifique-se de que tem o seguinte:

- **Alguns meios de emissão e distribuição de certificados**. Este tópico e seus exemplos partem do princípio de que está a utilizar autoridade de certificação do Active Directory. Para obter mais informações sobre os serviços de certificados do Active Directory, consulte [Active Directory certificado serviços descrição geral](https://technet.microsoft.com/library/hh831740.aspx) e [serviços de certificados do Active Directory no Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
- **Acesso administrativo para o nó de destino ou nós**.
- **Cada nó de destino tem um certificado com capacidade de encriptação, guardar Store seu pessoal**. No Windows PowerShell, o caminho para o arquivo é Cert: \LocalMachine\My. Os exemplos neste tópico utilizam o modelo de "autenticação de estação de trabalho", que pode ser encontrado (juntamente com outros modelos de certificado) em [modelos de certificado predefinido](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
- Se executar esta configuração num computador que não seja o nó de destino **exportar a chave pública do certificado**e, em seguida, importe-o para o computador irá executar a configuração a partir de. Certifique-se de que exporta apenas o **público** chave; proteger a chave privada.

## <a name="overall-process"></a>Processo geral

 1. Configure os certificados, chaves e thumbprints, certificar-se de que cada nó de destino tem cópias do certificado e a configuração de computador tem a chave pública e o thumbprint.
 2. Crie um bloco de dados de configuração que contém o caminho e o thumbprint da chave pública.
 3. Crie um script de configuração que define a configuração pretendida para o nó de destino e configura a desencriptação em nós de destino por comandos de configuração Local manager para descriptografar os dados de configuração a utilizar o certificado e sua impressão digital.
 4. Execute a configuração, que irá configurar as definições do Gestor de configuração Local e iniciar a configuração de DSC.

![Diagram1](../images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Requisitos de certificado

Adotar a encriptação de credenciais, um certificado de chave pública tem de estar disponível na _nó de destino_ ou seja **fidedigna** pelo computador que está a ser usado para criar a configuração de DSC.
Este certificado de chave pública tem requisitos específicos para poder ser utilizado para encriptação de credenciais de DSC:

1. **Utilização de chave**:
   - Tem de conter: 'KeyEncipherment' e 'DataEncipherment'.
   - Deve _não_ contêm: Assinatura digital.
2. **Utilização de chave avançada**:
   - Tem de conter: Encriptação de documentos (1.3.6.1.4.1.311.80.1).
   - Deve _não_ contêm: Autenticação de cliente (1.3.6.1.5.5.7.3.2) e autenticação de servidor (1.3.6.1.5.5.7.3.1).
3. A chave privada do certificado está disponível na * Node_ de destino.
4. O **fornecedor** para o certificado tem de ser "Microsoft RSA SChannel fornecedor de criptografia".

> [!IMPORTANT]
> Apesar de poder utilizar um certificado com que contém uma utilização de chave de "Assinatura Digital" ou uma da EKU de autenticação, isso permitirá que a chave de encriptação mais facilmente ser desfeitos e vulnerável a ataques. Portanto, é melhor prática para utilizar um certificado criado especificamente para a finalidade de proteger as credenciais de DSC que omite estes utilização de chave e EKUs.

Qualquer certificado existente no _nó de destino_ que satisfazem esses critérios podem ser utilizadas para proteger credenciais de DSC.

## <a name="certificate-creation"></a>Criação do certificado

Existem duas abordagens que pode seguir para criar e utilizar o certificado de encriptação necessário (par de chaves públicas-privadas).

1. Criá-la no **nó de destino** e exportar a chave pública para o **nó de criação**
2. Criá-la no **nó criação** e exportar o par de chaves completo para o **nó de destino**

Método 1 é recomendado porque a chave privada utilizada para desencriptar credenciais no MOF permanece no nó de destino em todos os momentos.

### <a name="creating-the-certificate-on-the-target-node"></a>Criar o certificado no nó de destino

A chave privada deve ser mantida em sigilo, porque é utilizado para desencriptar o MOF no **nó de destino** a forma mais fácil de fazer isso é criar o certificado de chave privado no **nó de destino**e copie o  **certificado de chave pública** para o computador que está a ser utilizado para criar a configuração de DSC para um ficheiro MOF.
O exemplo seguinte:

1. cria um certificado no **nó de destino**
2. Exporta o certificado de chave público no **nó de destino**.
3. importa o certificado de chave público para o **minha** arquivo de certificados a **criação nó**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>No nó de destino: criar e exportar o certificado

> Nó de destino: Windows Server 2016 e Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

Exportar uma vez, o `DscPublicKey.cer` precisaria ser copiados para o **criação nó**.

> Nó de destino: Windows Server 2012 R2/Windows 8.1 e versões anteriores
> [!WARNING]
> Uma vez que o `New-SelfSignedCertificate` cmdlet no Windows sistemas operativos anteriores ao Windows 10 e Windows Server 2016 não suportam a **tipo** parâmetro, um método alternativo de criar este certificado é necessário nesses sistemas operacionais.
>
> Neste caso, pode utilizar `makecert.exe` ou `certutil.exe` para criar o certificado.
>
>É um método alternativo [transferir o script New-SelfSignedCertificateEx.ps1 a partir do Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e utilizá-lo para criar o certificado em vez disso:

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

Exportar uma vez, o ```DscPublicKey.cer``` precisaria ser copiados para o **criação nó**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>No nó de criação: importar a chave pública do certificado

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Criar o certificado no nó de criação

Em alternativa, o certificado de encriptação pode ser criado no **nó criação**, exportado com o **chave privada** como um PFX do ficheiro e, em seguida, importado no **nó de destino**.
Este é o método atual para a implementação de encriptação de credenciais do DSC na _servidor Nano_.
Embora o PFX é protegido com uma palavra-passe deve ser mantida seguro durante o trânsito.
O exemplo seguinte:

1. cria um certificado no **Authoring nó**.
2. Exporta o certificado, incluindo a chave privada sobre o **Authoring nó**.
3. Remove a chave privada do **nó de criação de conteúdos**, mas mantém o certificado de chave público na **meu** armazenar.
4. importa o certificado de chave privado para o arquivo de certificados My(Personal) sobre o **nó de destino**.
   - tem de ser adicionado ao arquivo de raiz, para que possam confiar nele o **nó de destino**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>No nó de criação: criar e exportar o certificado

> Nó de destino: Windows Server 2016 e Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

Exportar uma vez, o `DscPrivateKey.pfx` precisaria ser copiados para o **nó de destino**.

> Nó de destino: Windows Server 2012 R2/Windows 8.1 e versões anteriores
> [!WARNING]
> Uma vez que o `New-SelfSignedCertificate` cmdlet no Windows sistemas operativos anteriores ao Windows 10 e Windows Server 2016 não suportam a **tipo** parâmetro, um método alternativo de criar este certificado é necessário nesses sistemas operacionais.
>
> Neste caso, pode utilizar `makecert.exe` ou `certutil.exe` para criar o certificado.
>
> É um método alternativo [transferir o script New-SelfSignedCertificateEx.ps1 a partir do Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e utilizá-lo para criar o certificado em vez disso:

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>No nó de destino: importar a chave privada do certificado como uma raiz confiável

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>Dados de configuração

O bloco de dados de configuração define que nós de destino para operar em se deve ou não para encriptar as credenciais, o meio de encriptação e outras informações. Para obter mais informações sobre o bloco de dados de configuração, consulte [separar a configuração e dados de ambiente](../configurations/configData.md).

Os elementos que podem ser configurados para cada nó que estão relacionados com a encriptação de credenciais são:

- **NodeName** -o nome do nó de destino que está a ser configurado para a encriptação de credenciais.
- **PsDscAllowPlainTextPassword** - se as credenciais não encriptadas terá permissão para ser passado para este nó. Isto é **não recomendada**.
- **Thumbprint** -o thumbprint do certificado que será utilizado para desencriptar as credenciais na configuração do DSC na _nó de destino_. **Este certificado tem de existir no arquivo de certificados do computador Local no nó de destino.**
- **CertificateFile** – o ficheiro de certificado (contendo apenas a chave pública) que deve ser utilizada para encriptar as credenciais para o _nó de destino_. Isso tem de ser binário codificado um DER X.509 ou ficheiro de certificado de formato X.509 com codificação Base 64.

Este exemplo mostra um bloco de dados de configuração que especifica um nó de destino para atuar em targetNode com nome, o caminho para o ficheiro de certificado de chave pública (denominado targetNode.cer) e o thumbprint para a chave pública.

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            };
        );
    }
```

## <a name="configuration-script"></a>Script de configuração

O script de configuração em si, utilize o `PsCredential` parâmetro para garantir que as credenciais são armazenadas para o menor tempo possível. Ao executar o exemplo fornecido, DSC irá solicitar-lhe as credenciais e, em seguida, encriptar o ficheiro MOF utilizando o CertificateFile que estão associado com o nó de destino no bloco de dados de configuração. Este exemplo de código copia um ficheiro a partir de um compartilhamento que está protegido para um utilizador.

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a>Configuração de desencriptação

Antes de [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) pode funcionar, é necessário informar ao Gestor de configuração Local em cada nó de destino de certificado a utilizar para desencriptar as credenciais, usando o recurso de CertificateID para verificar o thumbprint do certificado. Esta função de exemplo irá encontrar o certificado local apropriado (poderá ter de personalizá-lo para que ele irá encontrar o certificado exato de que pretende utilizar):

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

Com o certificado identificado por sua impressão digital, o script de configuração pode ser atualizado para utilizar o valor:

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a>Executar a configuração

Neste momento, pode executar a configuração, que vai exportar os dois arquivos:

- A *. ficheiro meta.mof que configura o Gestor de configuração de Local para desencriptar as credenciais a utilizar o certificado que é armazenado no arquivo local e identificado por sua impressão digital. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) aplica-se a *. meta.mof ficheiro.
- Um ficheiro MOF que, na verdade, se aplica a configuração. Start-dscconfiguration para aplica-se a configuração.

Estes comandos irão realizar essas etapas:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

Neste exemplo emitiria a configuração de DSC para o nó de destino.
Também pode ser aplicada a configuração de DSC com um servidor de solicitação de DSC, se disponível.

Ver [como configurar um cliente de solicitação de DSC](pullClient.md) para obter mais informações sobre a aplicação de configurações de DSC com um servidor de solicitação de DSC.

## <a name="credential-encryption-module-example"></a>Exemplo de módulo de encriptação de credenciais

Eis um exemplo completo que incorpora todas essas etapas, além de um cmdlet de programa auxiliar que exporta e copia as chaves públicas:

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```
