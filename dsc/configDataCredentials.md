---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Opções de credenciais nos dados de configuração"
ms.openlocfilehash: 6ddf82c2b63309255ec3187d650677a6c3c2afb0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="credentials-options-in-configuration-data"></a>Opções de credenciais nos dados de configuração
>Aplica-se a: O Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>As palavras-passe de texto simples e os utilizadores de domínio

Configurações de DSC que contém uma credencial sem encriptação irão gerar uma mensagem de erro sobre palavras-passe de texto simples.
Além disso, DSC irá gerar um aviso ao utilizar as credenciais do domínio.
Para suprimir estas mensagens de aviso de erro e utilizam as palavras-chave do DSC configuração dados:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

> [!NOTE]
> Armazenar/transmitir palavras-passe de texto simples não encriptadas é geralmente não segura. É recomendado proteger credenciais através de técnicas tratadas mais à frente neste tópico.
> O serviço do Automation DSC do Azure permite-lhe gerir centralmente as credenciais para ser compilado em configurações e armazenadas em segurança.
> Para informações, consulte: [compilar configurações de DSC / ativos de credenciais](/azure/automation/automation-dsc-compile#credential-assets)

Segue-se um exemplo de transmitir as credenciais de texto simples:

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
        @{
            # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="*"
            PSDscAllowPlainTextPassword = $true
        },
        #however, each node still needs to be explicitly defined for "*" to have meaning
        @{
            NodeName = "TestMachine1"
        },
        #we can also use a property to define node-specific passwords, although this is no more secure
        @{
            NodeName = "TestMachine2";
            UserName = "User2"
            LocalPassword = "ThisIsYetAnotherPlaintextPassword"
        }
        )
}
configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a>Processamento de credenciais no DSC

Recursos de configuração de DSC run `Local System` por predefinição.
No entanto, alguns recursos tem uma credencial, por exemplo quando o `Package` recursos tem de instalar o software com uma conta de utilizador específico.

Recursos anteriores utilizados um hard-coded `Credential` nome da propriedade para lidar com isto.
WMF 5.0 adicionado um automático `PsDscRunAsCredential` propriedade para todos os recursos.
Para obter informações sobre como utilizar `PsDscRunAsCredential`, consulte [DSC em execução com as credenciais de utilizador](runAsUser.md).
Recursos mais recentes e recursos personalizados podem utilizar esta propriedade automática em vez de criar as seus próprios propriedade credenciais.

> [!NOTE]
> A estrutura de alguns recursos estão a utilizar várias credenciais para um motivo específico e terá as seus próprios propriedades de credencial.

Para localizar a credencial disponível propriedades num recurso utilizam `Get-DscResource -Name ResourceName -Syntax` ou o Intellisense no ISE do (`CTRL+SPACE`).

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

Este exemplo utiliza um [grupo](https://msdn.microsoft.com/powershell/dsc/groupresource) recurso do `PSDesiredStateConfiguration` módulo incorporado de recursos de DSC.
Pode criar grupos locais e adicionar ou remover membros.
Aceita ambos o `Credential` propriedade e o automático `PsDscRunAsCredential` propriedade.
No entanto, o recurso utiliza apenas a `Credential` propriedade.

Para obter mais informações sobre o `PsDscRunAsCredential` propriedade, consulte [DSC em execução com as credenciais de utilizador](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Exemplo: O recurso do grupo de propriedade de credencial

É executado DSC `Local System`, pelo que já tem as permissões para alterar os utilizadores e grupos locais.
Se o membro adicionado é uma conta local, não é necessária nenhuma credencial.
Se o `Group` recursos adiciona uma conta de domínio ao grupo local, em seguida, é necessária uma credencial.

Não são permitidas consultas anónimas ao Active Directory.
O `Credential` propriedade o `Group` recurso é a conta de domínio utilizada para a consulta do Active Directory.
Para fins de maioria dos tal poderá dever uma conta de utilizador genérico, por predefinição, os utilizadores podem *ler* maioria dos objetos no Active Directory.

## <a name="example-configuration"></a>Configuração de exemplo

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

Este código gera um erro e a mensagem de aviso:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

Neste exemplo tem dois problemas:
1. Um erro explica de que as palavras-passe de texto simples não são recomendadas
2. Indica um aviso contra a utilização de uma credencial de domínio

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

A primeira mensagem de erro tem um URL com a documentação.
Esta ligação explica como encriptar as palavras-passe a utilizar um [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) estrutura e um certificado.
Para obter mais informações sobre certificados e DSC [ler esta mensagem](http://aka.ms/certs4dsc).

Para forçar uma palavra-passe de texto simples, o recurso requer o `PsDscAllowPlainTextPassword` secção de palavra-chave dos dados de configuração da seguinte forma:

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

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

> [!NOTE]
> `NodeName` não pode ser igual asterisco, um nome de nó específico é obrigatório.

**Microsoft aconselha para evitar palavras-passe de texto simples devido ao risco de segurança significativo.**

Uma exceção seria ao utilizar o serviço do Automation DSC do Azure, apenas porque os dados são armazenados sempre encriptados (em trânsito, Inativos no serviço e o restante no nó).

## <a name="domain-credentials"></a>Credenciais do domínio

Ainda executar novamente o script de configuração de exemplo (com ou sem encriptação), gera o aviso de que a conta para uma credencial não é recomendada utilizar um domínio.
Utilizar uma conta local elimina potencial exposição de credenciais de domínio que possam ser utilizados noutros servidores.

**Ao utilizar as credenciais com recursos de DSC, preferir uma conta local através de uma conta de domínio sempre que possível.**

Se existir um '\' ou ' @' no `Username` propriedade de credencial, DSC irá processá-lo como uma conta de domínio.
Há uma exceção para "localhost", "127.0.0.1" e ":: 1" na parte do domínio do nome de utilizador.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

No DSC `Group` exemplo de recurso acima, consultar um domínio do Active Directory *requer* uma conta de domínio.
Neste caso, adicione o `PSDscAllowDomainUser` propriedade para o `ConfigurationData` bloquear da seguinte forma:

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

Agora, o script de configuração irá gerar o ficheiro MOF com sem erros ou avisos.
