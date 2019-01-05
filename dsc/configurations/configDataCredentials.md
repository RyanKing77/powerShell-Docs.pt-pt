---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Opções de credenciais nos dados de configuração
ms.openlocfilehash: 10cf3456fcc7104b7dd779db30aebace54ba087a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046646"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="74a47-103">Opções de credenciais nos dados de configuração</span><span class="sxs-lookup"><span data-stu-id="74a47-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="74a47-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="74a47-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="74a47-105">As palavras-passe de texto sem formatação e utilizadores de domínio</span><span class="sxs-lookup"><span data-stu-id="74a47-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="74a47-106">Configurações de DSC que contém uma credencial sem encriptação irão gerar uma mensagem de erro sobre palavras-passe de texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="74a47-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="74a47-107">Além disso, DSC irá gerar um aviso ao utilizar as credenciais de domínio.</span><span class="sxs-lookup"><span data-stu-id="74a47-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="74a47-108">Para suprimir estas mensagens de aviso de erro e utilizam as palavras-chave da data do configuração de DSC:</span><span class="sxs-lookup"><span data-stu-id="74a47-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="74a47-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="74a47-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="74a47-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="74a47-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="74a47-111">Armazenar/transmitir palavras-passe de texto sem formatação não encriptados, normalmente, não é seguro.</span><span class="sxs-lookup"><span data-stu-id="74a47-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="74a47-112">É recomendado proteger credenciais usando as técnicas abordadas mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="74a47-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="74a47-113">O serviço de DSC de automatização do Azure permite-lhe gerir centralmente as credenciais para ser compilado em configurações e armazenado em segurança.</span><span class="sxs-lookup"><span data-stu-id="74a47-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="74a47-114">Para obter informações, consulte: [Compilar configurações do DSC / recursos de credencial](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="74a47-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="74a47-115">Segue-se um exemplo de passar credenciais de texto sem formatação:</span><span class="sxs-lookup"><span data-stu-id="74a47-115">The following is an example of passing plain text credentials:</span></span>

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

# We declared the ConfigurationData in a local variable, but we need to pass it
# in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData

# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

<span data-ttu-id="74a47-116">Este é um trecho do arquivo ". MOF" gerado pela configuração de "TestMachine1".</span><span class="sxs-lookup"><span data-stu-id="74a47-116">This is an excerpt from the ".mof" file generated by the configuration for "TestMachine1".</span></span> <span data-ttu-id="74a47-117">O `System.Security.SecureString` utilizados na configuração foi convertida em texto sem formatação e armazenada no arquivo ". MOF" como um `MSF_Credential`.</span><span class="sxs-lookup"><span data-stu-id="74a47-117">The `System.Security.SecureString` used in the configuration was converted to plain text and stored in the ".mof" file as a `MSF_Credential`.</span></span> <span data-ttu-id="74a47-118">A `SecureString` é encriptado com o perfil do utilizador atual.</span><span class="sxs-lookup"><span data-stu-id="74a47-118">A `SecureString` is encrypted with the current users profile.</span></span> <span data-ttu-id="74a47-119">Isso funciona bem com todos os formulários de gestão remota do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74a47-119">This works well with all forms of PowerShell remote management.</span></span> <span data-ttu-id="74a47-120">Um arquivo ". MOF" foi criado para ser um mecanismo de configuração apenas de reserva.</span><span class="sxs-lookup"><span data-stu-id="74a47-120">A ".mof" file is designed to be a stand alone configuration mechanism.</span></span> <span data-ttu-id="74a47-121">A partir do PowerShell 5.0, os ficheiros de ". MOF" num nó são encriptados em repouso, mas não em trânsito para o nó.</span><span class="sxs-lookup"><span data-stu-id="74a47-121">Beginning in PowerShell 5.0, ".mof" files on a Node are encrypted at rest, but not in transit to the Node.</span></span> <span data-ttu-id="74a47-122">Isso significa que as palavras-passe num arquivo ". MOF" são expostas como texto não encriptado ao aplicar a um nó.</span><span class="sxs-lookup"><span data-stu-id="74a47-122">This means that passwords in a ".mof" file are exposed as clear text when you apply them to a Node.</span></span> <span data-ttu-id="74a47-123">Para encriptar as credenciais, tem de utilizar um **servidor de solicitação**.</span><span class="sxs-lookup"><span data-stu-id="74a47-123">To encrypt credentials, you need to use a **Pull Server**.</span></span> <span data-ttu-id="74a47-124">Para obter mais informações, consulte [ficheiros MOF proteger com certificados](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="74a47-124">For more information, see [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>

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

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="74a47-125">Processamento de credenciais no DSC</span><span class="sxs-lookup"><span data-stu-id="74a47-125">Handling Credentials in DSC</span></span>

<span data-ttu-id="74a47-126">Recursos de configuração de DSC executam como `Local System` por predefinição.</span><span class="sxs-lookup"><span data-stu-id="74a47-126">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="74a47-127">No entanto, alguns recursos tem uma credencial, por exemplo quando o `Package` recursos tem de instalar software numa conta de utilizador específico.</span><span class="sxs-lookup"><span data-stu-id="74a47-127">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="74a47-128">Recursos anteriores utilizados codificados `Credential` nome da propriedade de lidar com isso.</span><span class="sxs-lookup"><span data-stu-id="74a47-128">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="74a47-129">WMF 5.0 adicionado um automático `PsDscRunAsCredential` propriedade para todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="74a47-129">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="74a47-130">Para obter informações sobre como utilizar `PsDscRunAsCredential`, consulte [executar o DSC com as credenciais de utilizador](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="74a47-130">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="74a47-131">Recursos mais recentes e recursos personalizados podem utilizar esta propriedade automática em vez de criar sua própria propriedade credenciais.</span><span class="sxs-lookup"><span data-stu-id="74a47-131">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="74a47-132">O design de alguns recursos estão a utilizar várias credenciais por um motivo específico, e eles terão suas próprias propriedades de credencial.</span><span class="sxs-lookup"><span data-stu-id="74a47-132">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="74a47-133">Para localizar a credencial disponível propriedades num recurso de usam `Get-DscResource -Name ResourceName -Syntax` ou o Intellisense no ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="74a47-133">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="74a47-134">Este exemplo utiliza um [grupo](../resources/resources.md) recursos do `PSDesiredStateConfiguration` módulo de recursos de DSC incorporado.</span><span class="sxs-lookup"><span data-stu-id="74a47-134">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="74a47-135">Pode criar grupos locais e adicionar ou remover membros.</span><span class="sxs-lookup"><span data-stu-id="74a47-135">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="74a47-136">Ela aceita ambos os `Credential` propriedade e o automático `PsDscRunAsCredential` propriedade.</span><span class="sxs-lookup"><span data-stu-id="74a47-136">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="74a47-137">No entanto, o recurso utiliza apenas o `Credential` propriedade.</span><span class="sxs-lookup"><span data-stu-id="74a47-137">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="74a47-138">Para obter mais informações sobre o `PsDscRunAsCredential` propriedade, veja [executar o DSC com as credenciais de utilizador](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="74a47-138">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="74a47-139">Exemplo: O recurso do grupo de propriedade de credencial</span><span class="sxs-lookup"><span data-stu-id="74a47-139">Example: The Group resource Credential property</span></span>

<span data-ttu-id="74a47-140">DSC é executado sob `Local System`, pelo que já tem permissões para alterar os utilizadores e grupos locais.</span><span class="sxs-lookup"><span data-stu-id="74a47-140">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="74a47-141">Se o membro adicionado é uma conta local, não existem credenciais é necessário.</span><span class="sxs-lookup"><span data-stu-id="74a47-141">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="74a47-142">Se o `Group` recurso adiciona uma conta de domínio ao grupo local, em seguida, é necessária uma credencial.</span><span class="sxs-lookup"><span data-stu-id="74a47-142">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="74a47-143">Anónimas consultas ao Active Directory não são permitidas.</span><span class="sxs-lookup"><span data-stu-id="74a47-143">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="74a47-144">O `Credential` propriedade o `Group` recurso é a conta de domínio utilizada para consultar o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="74a47-144">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="74a47-145">Para a maioria das finalidades possível uma conta de utilizador genérica, que por padrão, os utilizadores podem *ler* maioria dos objetos no Active Directory.</span><span class="sxs-lookup"><span data-stu-id="74a47-145">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="74a47-146">Exemplo de configuração</span><span class="sxs-lookup"><span data-stu-id="74a47-146">Example Configuration</span></span>

<span data-ttu-id="74a47-147">O código de exemplo seguinte utiliza DSC para preencher um grupo local com um utilizador de domínio:</span><span class="sxs-lookup"><span data-stu-id="74a47-147">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="74a47-148">Esse código gera um erro e a mensagem de aviso:</span><span class="sxs-lookup"><span data-stu-id="74a47-148">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="74a47-149">Neste exemplo tem dois problemas:</span><span class="sxs-lookup"><span data-stu-id="74a47-149">This example has two issues:</span></span>
1. <span data-ttu-id="74a47-150">Um erro explica de que as palavras-passe de texto simples não são recomendadas</span><span class="sxs-lookup"><span data-stu-id="74a47-150">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="74a47-151">Um aviso aconselha-se contra a utilização de uma credencial de domínio</span><span class="sxs-lookup"><span data-stu-id="74a47-151">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="74a47-152">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="74a47-152">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="74a47-153">A primeira mensagem de erro tem um URL com a documentação.</span><span class="sxs-lookup"><span data-stu-id="74a47-153">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="74a47-154">Esta ligação explica como encriptar palavras-passe utilizando um [ConfigurationData](./configData.md) estrutura e um certificado.</span><span class="sxs-lookup"><span data-stu-id="74a47-154">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="74a47-155">Para obter mais informações sobre certificados e DSC [leia esta postagem](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="74a47-155">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="74a47-156">Para forçar uma palavra-passe de texto sem formatação, o recurso requer o `PsDscAllowPlainTextPassword` secção de palavra-chave nos dados de configuração da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="74a47-156">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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
> <span data-ttu-id="74a47-157">`NodeName` não pode ser igual asterisco, um nome de nó específico é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="74a47-157">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="74a47-158">**Microsoft solicitará para evitar palavras-passe de texto sem formatação devido ao risco de segurança significativo.**</span><span class="sxs-lookup"><span data-stu-id="74a47-158">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="74a47-159">Credenciais de domínio</span><span class="sxs-lookup"><span data-stu-id="74a47-159">Domain Credentials</span></span>

<span data-ttu-id="74a47-160">Ainda executar novamente o script de configuração de exemplo (com ou sem encriptação), gera o aviso que conta para uma credencial não é recomendada utilizar um domínio.</span><span class="sxs-lookup"><span data-stu-id="74a47-160">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="74a47-161">Com uma conta local elimina a exposição potencial das credenciais de domínio que poderiam ser usadas em outros servidores.</span><span class="sxs-lookup"><span data-stu-id="74a47-161">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="74a47-162">**Ao utilizar as credenciais com recursos de DSC, prefira uma conta local através de uma conta de domínio, sempre que possível.**</span><span class="sxs-lookup"><span data-stu-id="74a47-162">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="74a47-163">Se existir um '\' ou '\@' no `Username` propriedade de credencial, DSC irá processá-lo como uma conta de domínio.</span><span class="sxs-lookup"><span data-stu-id="74a47-163">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="74a47-164">Existe uma exceção para "localhost", "127.0.0.1", e ":: 1" na parte do domínio do nome do utilizador.</span><span class="sxs-lookup"><span data-stu-id="74a47-164">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="74a47-165">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="74a47-165">PSDscAllowDomainUser</span></span>

<span data-ttu-id="74a47-166">Na DSC `Group` exemplo de recurso acima, consultar o domínio do Active Directory *requer* uma conta de domínio.</span><span class="sxs-lookup"><span data-stu-id="74a47-166">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="74a47-167">Neste caso adicione a `PSDscAllowDomainUser` propriedade o `ConfigurationData` bloquear da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="74a47-167">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="74a47-168">Agora, o script de configuração irá gerar o ficheiro MOF sem erros ou avisos.</span><span class="sxs-lookup"><span data-stu-id="74a47-168">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
