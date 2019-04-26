---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Opções de credenciais nos dados de configuração
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080157"
---
# <a name="credentials-options-in-configuration-data"></a>Opções de credenciais nos dados de configuração

>Aplica-se a: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>As palavras-passe de texto sem formatação e utilizadores de domínio

Configurações de DSC que contém uma credencial sem encriptação irão gerar uma mensagem de erro sobre palavras-passe de texto sem formatação.
Além disso, DSC irá gerar um aviso ao utilizar as credenciais de domínio.
Para suprimir estas mensagens de aviso de erro e utilizam as palavras-chave da data do configuração de DSC:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Armazenar/transmitir palavras-passe de texto sem formatação não encriptados, normalmente, não é seguro. É recomendado proteger credenciais usando as técnicas abordadas mais adiante neste tópico.
> O serviço de DSC de automatização do Azure permite-lhe gerir centralmente as credenciais para ser compilado em configurações e armazenado em segurança.
> Para obter informações, consulte: [Compilar configurações do DSC / recursos de credencial](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>Processamento de credenciais no DSC

Recursos de configuração de DSC executam como `Local System` por predefinição.
No entanto, alguns recursos tem uma credencial, por exemplo quando o `Package` recursos tem de instalar software numa conta de utilizador específico.

Recursos anteriores utilizados codificados `Credential` nome da propriedade de lidar com isso.
WMF 5.0 adicionado um automático `PsDscRunAsCredential` propriedade para todos os recursos.
Para obter informações sobre como utilizar `PsDscRunAsCredential`, consulte [executar o DSC com as credenciais de utilizador](runAsUser.md).
Recursos mais recentes e recursos personalizados podem utilizar esta propriedade automática em vez de criar sua própria propriedade credenciais.

> [!NOTE]
> O design de alguns recursos estão a utilizar várias credenciais por um motivo específico, e eles terão suas próprias propriedades de credencial.

Para localizar a credencial disponível propriedades num recurso de usam `Get-DscResource -Name ResourceName -Syntax` ou o Intellisense no ISE (`CTRL+SPACE`).

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Este exemplo utiliza um [grupo](../resources/resources.md) recursos do `PSDesiredStateConfiguration` módulo de recursos de DSC incorporado.
Pode criar grupos locais e adicionar ou remover membros.
Ela aceita ambos os `Credential` propriedade e o automático `PsDscRunAsCredential` propriedade.
No entanto, o recurso utiliza apenas o `Credential` propriedade.

Para obter mais informações sobre o `PsDscRunAsCredential` propriedade, veja [executar o DSC com as credenciais de utilizador](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Exemplo: O recurso do grupo de propriedade de credencial

DSC é executado sob `Local System`, pelo que já tem permissões para alterar os utilizadores e grupos locais.
Se o membro adicionado é uma conta local, não existem credenciais é necessário.
Se o `Group` recurso adiciona uma conta de domínio ao grupo local, em seguida, é necessária uma credencial.

Anónimas consultas ao Active Directory não são permitidas.
O `Credential` propriedade o `Group` recurso é a conta de domínio utilizada para consultar o Active Directory.
Para a maioria das finalidades possível uma conta de utilizador genérica, que por padrão, os utilizadores podem *ler* maioria dos objetos no Active Directory.

## <a name="example-configuration"></a>Exemplo de configuração

O código de exemplo seguinte utiliza DSC para preencher um grupo local com um utilizador de domínio:

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

Esse código gera um erro e a mensagem de aviso:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

Neste exemplo tem dois problemas:

1. Um erro explica de que as palavras-passe de texto simples não são recomendadas
2. Um aviso aconselha-se contra a utilização de uma credencial de domínio

Os sinalizadores **PSDSCAllowPlainTextPassword** e **PSDSCAllowDomainUser** suprimir o erro e aviso a informar o utilizador do risco envolvido.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

A primeira mensagem de erro tem um URL com a documentação.
Esta ligação explica como encriptar palavras-passe utilizando um [ConfigurationData](./configData.md) estrutura e um certificado.
Para obter mais informações sobre certificados e DSC [leia esta postagem](http://aka.ms/certs4dsc).

Para forçar uma palavra-passe de texto sem formatação, o recurso requer o `PsDscAllowPlainTextPassword` secção de palavra-chave nos dados de configuração da seguinte forma:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost.mof

O **PSDSCAllowPlainTextPassword** sinalizador requer que o utilizador reconhece o risco de armazenar as palavras-passe de texto sem formatação num arquivo MOF. No ficheiro MOF gerado, mesmo que um **PSCredential** objeto que contém um **SecureString** foi usada, as palavras-passe continuarão a ser apresentados como texto simples. Este é o único momento em que as credenciais são expostas. Obter acesso a isso permite o ficheiro MOF alguém aceder à conta de administrador.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>Credenciais em trânsito e em inatividade

- O **PSDscAllowPlainTextPassword** sinalizador permite que a compilação de arquivos MOF, que contêm as palavras-passe em texto não criptografado.
  Tome medidas ao armazenar ficheiros MOF que contém as palavras-passe de texto não encriptado.
- Quando o ficheiro MOF é entregue a um nó **Push** modo, o WinRM encripta a comunicação para proteger a palavra-passe de texto não criptografado, a menos que substituir a predefinição com o **AllowUnencrypted** parâmetro.
  - Encriptar o MOF com um certificado protege o ficheiro MOF em repouso antes que tenha sido aplicada a um nó.
- Na **Pull** modo, pode configurar o servidor de solicitação do Windows para utilizar HTTPS para criptografar o tráfego utilizando o protocolo especificado no servidor de informações da Internet. Para obter mais informações, consulte os artigos [como configurar um cliente de solicitação de DSC](../pull-server/pullclient.md) e [ficheiros MOF proteger com certificados](../pull-server/secureMOF.md).
  - Na [configuração de estado de automatização do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) serviço Pull de tráfego é sempre encriptado.
- No nó, ficheiros MOF são encriptados em inatividade a partir do PowerShell 5.0.
  - No PowerShell 4.0 MOF ficheiros são encriptados em inatividade, a menos que eles são criptografados com um certificado quando enviada por push ou obtidas para o nó.

**Microsoft solicitará para evitar palavras-passe de texto sem formatação devido ao risco de segurança significativo.**

## <a name="domain-credentials"></a>Credenciais de domínio

Ainda executar novamente o script de configuração de exemplo (com ou sem encriptação), gera o aviso que conta para uma credencial não é recomendada utilizar um domínio.
Com uma conta local elimina a exposição potencial das credenciais de domínio que poderiam ser usadas em outros servidores.

**Ao utilizar as credenciais com recursos de DSC, prefira uma conta local através de uma conta de domínio, sempre que possível.**

Se existir um '\\'ou'\@' no `Username` propriedade de credencial, em seguida, o DSC irá processá-lo como uma conta de domínio.
Existe uma exceção para "localhost", "127.0.0.1", e ":: 1" na parte do domínio do nome do utilizador.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

Na DSC `Group` exemplo de recurso acima, consultar o domínio do Active Directory *requer* uma conta de domínio.
Neste caso adicione a `PSDscAllowDomainUser` propriedade o `ConfigurationData` bloquear da seguinte forma:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

Agora, o script de configuração irá gerar o ficheiro MOF sem erros ou avisos.
