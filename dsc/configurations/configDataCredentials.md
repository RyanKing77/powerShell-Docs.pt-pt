---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Opções de credenciais nos dados de configuração
ms.openlocfilehash: c4057457bf6beb2c5fc9dffef9122cd488ccdcd7
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012437"
---
# <a name="credentials-options-in-configuration-data"></a>Opções de credenciais nos dados de configuração
>Aplica-se a: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>As palavras-passe de texto sem formatação e utilizadores de domínio

Configurações de DSC que contém uma credencial sem encriptação irão gerar uma mensagem de erro sobre palavras-passe de texto sem formatação.
Além disso, DSC irá gerar um aviso ao utilizar as credenciais de domínio.
Para suprimir estas mensagens de aviso de erro e utilizam as palavras-chave da data do configuração de DSC:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

> [!NOTE]
> Armazenar/transmitir palavras-passe de texto sem formatação não encriptados, normalmente, não é seguro. É recomendado proteger credenciais usando as técnicas abordadas mais adiante neste tópico.
> O serviço de DSC de automatização do Azure permite-lhe gerir centralmente as credenciais para ser compilado em configurações e armazenado em segurança.
> Para obter informações, consulte: [Compilar configurações do DSC / recursos de credencial](/azure/automation/automation-dsc-compile#credential-assets)

Segue-se um exemplo de passar credenciais de texto sem formatação:

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
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
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
            Credential = $promptedCreds
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

Este é um trecho do arquivo ". MOF" gerado pela configuração de "TestMachine1". O `System.Security.SecureString` utilizados na configuração foi convertida em texto sem formatação e armazenada no arquivo ". MOF" como um `MSF_Credential`. A `SecureString` é encriptado com o perfil do utilizador atual. Isso funciona bem com todos os formulários de gestão remota do PowerShell. Um arquivo ". MOF" foi criado para ser um mecanismo de configuração apenas de reserva. A partir do PowerShell 5.0, os ficheiros de ". MOF" num nó são encriptados em repouso, mas não em trânsito para o nó. Isso significa que as palavras-passe num arquivo ". MOF" são expostas como texto não encriptado ao aplicar a um nó. Para encriptar as credenciais, tem de utilizar um **servidor de solicitação**. Para obter mais informações, consulte [ficheiros MOF proteger com certificados](./pull-server/secureMOF.md).

```syntax
instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsYetAnotherPlaintextPassword";
 UserName = "User2";

};

instance of MSFT_UserResource as $MSFT_UserResource1ref
{
ResourceID = "[User]User2";
 Description = "local account";
 UserName = "User2";
 Ensure = "Present";
 Password = $MSFT_Credential1ref;
 Disabled = False;
 SourceInfo = "::66::9::User";
 PasswordNeverExpires = True;
 ModuleName = "PsDesiredStateConfiguration";
 PasswordChangeRequired = False;

ModuleVersion = "1.0";

 ConfigurationName = "unencryptedPasswordDemo";

};
```

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
2. Um aviso aconselha-se contra a utilização de uma credencial de domínio

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

A primeira mensagem de erro tem um URL com a documentação.
Esta ligação explica como encriptar palavras-passe utilizando um [ConfigurationData](./configData.md) estrutura e um certificado.
Para obter mais informações sobre certificados e DSC [leia esta postagem](http://aka.ms/certs4dsc).

Para forçar uma palavra-passe de texto sem formatação, o recurso requer o `PsDscAllowPlainTextPassword` secção de palavra-chave nos dados de configuração da seguinte forma:

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

**Microsoft solicitará para evitar palavras-passe de texto sem formatação devido ao risco de segurança significativo.**

## <a name="domain-credentials"></a>Credenciais de domínio

Ainda executar novamente o script de configuração de exemplo (com ou sem encriptação), gera o aviso que conta para uma credencial não é recomendada utilizar um domínio.
Com uma conta local elimina a exposição potencial das credenciais de domínio que poderiam ser usadas em outros servidores.

**Ao utilizar as credenciais com recursos de DSC, prefira uma conta local através de uma conta de domínio, sempre que possível.**

Se existir um '\' ou '\@' no `Username` propriedade de credencial, DSC irá processá-lo como uma conta de domínio.
Existe uma exceção para "localhost", "127.0.0.1", e ":: 1" na parte do domínio do nome do utilizador.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

Na DSC `Group` exemplo de recurso acima, consultar o domínio do Active Directory *requer* uma conta de domínio.
Neste caso adicione a `PSDscAllowDomainUser` propriedade o `ConfigurationData` bloquear da seguinte forma:

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

Agora, o script de configuração irá gerar o ficheiro MOF sem erros ou avisos.
