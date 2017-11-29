---
ms.date: 2017-10-31
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Proteger o ficheiro MOF
ms.openlocfilehash: ed9d259e2cd963560ad6f5b60702c54e2fa36900
ms.sourcegitcommit: cd5a1f054cbf9eb95c5242a995f9741e031ddb24
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/28/2017
---
# <a name="securing-the-mof-file"></a>Proteger o ficheiro MOF

>Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

DSC gere a configuração de nós de servidor, aplicando as informações armazenadas num ficheiro MOF, onde o Gestor de configuração Local (MMC) implementa o estado final pretendido.
Uma vez que este ficheiro contém os detalhes da configuração, é importante manter segura.
Este tópico descreve como garantir que o nó de destino tiver encriptados o ficheiro.

A partir do PowerShell na versão 5.0, todo o ficheiro MOF é encriptado por predefinição quando é aplicada para o nó utilizando o **início DSCConfiguration** cmdlet.
O processo descrito neste artigo, é necessário apenas quando implementar uma solução utilizando o protocolo de serviço de solicitação, se os certificados não são geridos, para garantir que as configurações transferidas pelo nó de destino podem ser desencriptadas e ler pelo sistema antes de estes serem aplicadas (por exemplo, o serviço de solicitação disponível no Windows Server).
Nós registado para [Automation DSC do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) serão automaticamente certificados instalou e geridas pelo serviço de com nenhuma sobrecarga administrativa necessária.

>**Nota:** este tópico descreve os certificados utilizados para a encriptação.
>Para a encriptação, um certificado auto-assinado é suficiente, porque a chave privada é sempre é mantida segredo e a encriptação não implica a confiança do documento.
>Certificados autoassinados devem *não* ser utilizados para fins de autenticação.
>Deve utilizar um certificado de um fidedigna autoridade de certificação (AC) para quaisquer fins de autenticação.

## <a name="prerequisites"></a>Pré-requisitos

Para encriptar com êxito as credenciais utilizadas para proteger uma configuração de DSC, certifique-se de que tem o seguinte:

* **Algum meio de emissão e distribuição de certificados**. Este tópico e respetivos exemplos partem do princípio de que está a utilizar autoridade de certificação do Active Directory. Para obter mais informações de fundo sobre serviços de certificados do Active Directory, consulte [Active Directory descrição geral do serviços de certificados do](https://technet.microsoft.com/library/hh831740.aspx) e [serviços de certificados do Active Directory no Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
* **Acesso administrativo para o nó de destino ou nós**.
* **Cada nó de destino tem um certificado com capacidade de encriptação, guardar o seu arquivo pessoal**. No Windows PowerShell, o caminho para o arquivo é Cert: \LocalMachine\My. Os exemplos neste tópico utilizam o modelo de "autenticação de estação de trabalho", que pode encontrar (juntamente com outros modelos de certificado) em [modelos de certificado predefinido](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
* Se executar esta configuração num computador diferente do nó de destino, **exportar a chave pública do certificado**e, em seguida, importá-lo para o computador irá executar a configuração a partir. Certifique-se de que exporta apenas o **pública** chave; manter a chave privada segura.

## <a name="overall-process"></a>Processo geral

 1. Configure os certificados, chaves e os thumbprints, certificando-se de que cada nó de destino tem cópias do certificado e o computador de configuração possui a chave pública e o thumbprint.
 2. Crie um bloco de dados de configuração que contém o caminho e o thumbprint da chave pública.
 3. Crie um script de configuração que define a configuração pretendida para o nó de destino e configura a desencriptação em nós de destino por commanding a configuração Local manager para desencriptar os dados de configuração utilizando o certificado e o respetivo thumbprint.
 4. Execute a configuração, o que irá configurar as definições do Gestor de configuração locais e iniciar a configuração de DSC.

![Diagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Requisitos de certificado

Para enact encriptação de credenciais, um certificado de chave pública tem de estar disponível no _o nó de destino_ que é **fidedigna** pelo computador que está a ser utilizado para criar a configuração de DSC.
Este certificado de chave pública tem requisitos específicos para que seja utilizado para encriptação de credenciais do DSC:
 1. **Utilização da chave**:
   - Tem de conter: 'KeyEncipherment' e 'DataEncipherment'.
   - Deve _não_ conter: 'Assinatura Digital'.
 2. **Utilização de chave avançada**:
   - Tem de conter: encriptação de documentos (1.3.6.1.4.1.311.80.1).
   - Deve _não_ conter: autenticação de cliente (1.3.6.1.5.5.7.3.2) e a autenticação de servidor (1.3.6.1.5.5.7.3.1).
 3. A chave privada do certificado está disponível na * Node_ de destino.
 4. O **fornecedor** para o certificado tem de ser "Microsoft RSA SChannel fornecedor de criptografia".
 
>**Uma melhor prática recomendada:** apesar de poder utilizar um certificado com que contém uma chave de utilização de 'Assinatura Digital' ou um da EKU de autenticação, esta operação permitirá a chave de encriptação ser mais facilmente utilizado indevidamente e vulnerável a ataque. Por isso, é recomendado utilizar um certificado criado especificamente para o objetivo de proteger as credenciais de DSC omite estes utilização da chave e EKUs.
  
Qualquer certificado existente no _o nó de destino_ que cumpre os estes critérios podem ser utilizadas para credenciais seguras do DSC.

## <a name="certificate-creation"></a>Criação do certificado

Existem duas abordagens que pode tomar para criar e utilizar o certificado de encriptação necessário (par de chaves públicas-privadas).

1. Criá-la no **o nó de destino** e exporte a chave pública para o **criação nó**
2. Criá-la no **criação nó** e exporte o par de chaves todo o **o nó de destino**

Método 1 é recomendado porque a chave privada utilizada para desencriptar as credenciais no MOF permanece no nó de destino permanente.


### <a name="creating-the-certificate-on-the-target-node"></a>Criar o certificado no nó de destino

A chave privada tem de ser mantida em segredo, porque é utilizado para desencriptar o MOF no **o nó de destino** a forma mais fácil de fazê-lo é ao criar o certificado de chave privado no **nó de destino**e copie o  **certificado de chave pública** para o computador que está a ser utilizado para criar a configuração de DSC num ficheiro MOF.
O exemplo seguinte:
 1. cria um certificado no **o nó de destino**
 2. Exporta o certificado de chave público no **o nó de destino**.
 3. importa o certificado de chave público para o **meu** arquivo de certificados o **criação nó**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>No nó de destino: criar e exportar o certificado
>Nó criação: Windows Server 2016 e o Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
Uma vez exportado, o ```DscPublicKey.cer``` teria de ser copiados para o **criação nó**.

>Nó de criação: Windows Server 2012 R2/Windows 8.1 e versões anteriores

Porque o cmdlet New-SelfSignedCertificate em sistemas operativos Windows antes do Windows 10 e Windows Server 2016 não suportam o **tipo** parâmetro, um método alternativo de criar este certificado é necessária a estes sistemas operativos.
Neste caso, pode utilizar ```makecert.exe``` ou ```certutil.exe``` para criar o certificado.

É um método alternativo para [transferir o script New-SelfSignedCertificateEx.ps1 a partir do Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e utilizá-la para criar o certificado em vez disso:
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
    -StoreName 'My' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
Uma vez exportado, o ```DscPublicKey.cer``` teria de ser copiados para o **criação nó**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>No nó de criação: importar a chave pública do certificado
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Criar o certificado no nó de criação
Em alternativa, o certificado de encriptação pode ser criado no **criação nó**, exportado com a **chave privada** como um PFX de ficheiros e, em seguida, importar no **nó de destino**.
Este é o atual método para implementar a encriptação de credenciais do DSC na _Nano servidor_.
Embora o PFX está protegido com uma palavra-passe, deve ser mantido seguro durante trânsito.
O exemplo seguinte:
 1. cria um certificado no **criação nó**.
 2. Exporta o certificado, incluindo a chave privada no **criação nó**.
 3. Remove a chave privada do **criação nó**, mas mantém o certificado de chave público no **meu** armazenar.
 4. importa o certificado de chave privado para o arquivo de certificados de raiz no **o nó de destino**.
   - tem de ser adicionado ao arquivo de raiz para que irá ser considerado fidedigno pelo **o nó de destino**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>No nó de criação: criar e exportar o certificado
>Nó de destino: Windows Server 2016 e o Windows 10

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
Uma vez exportado, o ```DscPrivateKey.pfx``` teria de ser copiados para o **nó de destino**.

>Nó de destino: Windows Server 2012 R2/Windows 8.1 e versões anteriores

Porque o cmdlet New-SelfSignedCertificate em sistemas operativos Windows antes do Windows 10 e Windows Server 2016 não suportam o **tipo** parâmetro, um método alternativo de criar este certificado é necessária a estes sistemas operativos.
Neste caso, pode utilizar ```makecert.exe``` ou ```certutil.exe``` para criar o certificado.

É um método alternativo para [transferir o script New-SelfSignedCertificateEx.ps1 a partir do Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e utilizá-la para criar o certificado em vez disso:
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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>No nó de destino: importar a chave privada do certificado como uma raiz fidedigna
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>Dados de configuração

O bloco de dados de configuração define os nós de destino a funcionar, se deve ou não para encriptar as credenciais, os meios de encriptação e outras informações. Para obter mais informações sobre o bloco de dados de configuração, consulte [separação de configuração e dados de ambiente](configData.md).

Os elementos que podem ser configurados para cada nó que estão relacionados com a encriptação de credenciais são:
* **NodeName** -o nome do nó de destino que está a ser configurado para a encriptação de credenciais.
* **PsDscAllowPlainTextPassword** - se sem encriptação de credenciais terá permissão para ser transmitido a este nó. Este é **não recomendado**.
* **Thumbprint** -o thumbprint do certificado que será utilizado para desencriptar as credenciais na configuração de DSC no _o nó de destino_. **Este certificado tem de existir no arquivo de certificados do computador Local no nó de destino.**
* **CertificateFile** - o ficheiro de certificado (contendo a chave pública apenas) que deve ser utilizada para encriptar as credenciais para o _o nó de destino_. Isto deve ser codificado de uma DER x. 509 binário ou ficheiro de certificado no formato x. 509 com codificação Base 64.

Este exemplo mostra um bloco de dados de configuração que especifica um nó de destino para agir em targetNode com nome, o caminho para o ficheiro de certificado de chave pública (denominado targetNode.cer) e o thumbprint para a chave pública.

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

O script de configuração em si, utilize o `PsCredential` parâmetro para se certificar de que as credenciais são armazenadas pelo período de tempo mais curto possível. Quando executar o exemplo fornecido, DSC irá solicitar credenciais de e, em seguida, encriptar o ficheiro MOF utilizando CertificateFile que está associado ao nó de destino no bloco de dados de configuração. Este exemplo de código copia um ficheiro a partir de uma partilha que esteja protegida para um utilizador.

```
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

## <a name="setting-up-decryption"></a>Configurar a desencriptação

Antes de [ `Start-DscConfiguration` ](https://technet.microsoft.com/en-us/library/dn521623.aspx) pode funcionar, terá de saber o Gestor de configuração Local em cada nó de destino de certificado a utilizar para desencriptar as credenciais, utilizando o recurso de CertificateID para verificar o thumbprint do certificado. Esta função de exemplo irá encontrar o certificado adequado a local (poderá ter de personalizá-lo, pelo que irá encontrar o certificado exato que pretende utilizar):

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

Com o certificado identificado pelo respetivo thumbprint, o script de configuração pode ser atualizado para utilizar o valor:

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

Neste momento, pode executar a configuração, que será a saída dois ficheiros:

 * A *. ficheiro meta.mof que configura o Gestor de configuração Local para desencriptar as credenciais utilizando o certificado que é armazenado no arquivo computador local e identificado pelo respetivo thumbprint. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx)aplica-se a *. meta.mof ficheiro.
 * Um ficheiro MOF existente, na verdade, aplica-se a configuração. Início DscConfiguration aplica-se a configuração.

Estes comandos irão conseguir esses passos:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

Neste exemplo seria push a configuração de DSC ao nó de destino.
A configuração de DSC também pode ser aplicada utilizando um servidor de solicitação do DSC esteja disponível.

Consulte [configurar um cliente de solicitação do DSC](pullClient.md) para obter mais informações sobre como aplicar configurações de DSC utilizando um servidor de solicitação do DSC.

## <a name="credential-encryption-module-example"></a>Exemplo de módulo de encriptação de credenciais

Eis um exemplo completo que incorpora todos estes passos, mais um cmdlet de programa auxiliar que exporta e copia as chaves públicas:

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

