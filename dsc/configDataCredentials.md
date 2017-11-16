---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Opções de credenciais nos dados de configuração"
ms.openlocfilehash: 94ff541fc517254ef2876c424307513eaf1d362a
ms.sourcegitcommit: 28e71b0ae868014523631fec3f5417de751944f3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2017
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="d7eb2-103">Opções de credenciais nos dados de configuração</span><span class="sxs-lookup"><span data-stu-id="d7eb2-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="d7eb2-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d7eb2-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="d7eb2-105">As palavras-passe de texto simples e os utilizadores de domínio</span><span class="sxs-lookup"><span data-stu-id="d7eb2-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="d7eb2-106">Configurações de DSC que contém uma credencial sem encriptação irão gerar uma mensagem de erro sobre palavras-passe de texto simples.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="d7eb2-107">Além disso, DSC irá gerar um aviso ao utilizar as credenciais do domínio.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="d7eb2-108">Para suprimir estas mensagens de aviso de erro e utilizam as palavras-chave do DSC configuração dados:</span><span class="sxs-lookup"><span data-stu-id="d7eb2-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="d7eb2-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="d7eb2-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="d7eb2-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="d7eb2-110">**PsDscAllowDomainUser**</span></span>

><span data-ttu-id="d7eb2-111">**Notas:**</span><span class="sxs-lookup"><span data-stu-id="d7eb2-111">**Notes:**</span></span> <p><span data-ttu-id="d7eb2-112">Armazenar/transmitir palavras-passe de texto simples não encriptadas é geralmente não segura.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-112">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="d7eb2-113">É recomendado proteger credenciais através de técnicas tratadas mais à frente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-113">Securing credentials by using the techniques covered later in this topic is recommended.</span></span></p> <p><span data-ttu-id="d7eb2-114">O serviço do Automation DSC do Azure permite-lhe gerir centralmente as credenciais para ser compilado em configurações e armazenadas em segurança.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-114">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>  <span data-ttu-id="d7eb2-115">Para informações, consulte: [compilar configurações de DSC / ativos de credenciais](https://docs.microsoft.com/en-in/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="d7eb2-115">For information, see: [Compiling DSC Configurations / Credential Assets](https://docs.microsoft.com/en-in/azure/automation/automation-dsc-compile#credential-assets)</span></span></p>

<span data-ttu-id="d7eb2-116">Segue-se um exemplo de transmitir as credenciais de texto simples:</span><span class="sxs-lookup"><span data-stu-id="d7eb2-116">The following is an example of passing plain text credentials:</span></span>

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

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="d7eb2-117">Processamento de credenciais no DSC</span><span class="sxs-lookup"><span data-stu-id="d7eb2-117">Handling Credentials in DSC</span></span>

<span data-ttu-id="d7eb2-118">Recursos de configuração de DSC run `Local System` por predefinição.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-118">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="d7eb2-119">No entanto, alguns recursos tem uma credencial, por exemplo quando o `Package` recursos tem de instalar o software com uma conta de utilizador específico.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-119">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="d7eb2-120">Recursos anteriores utilizados um hard-coded `Credential` nome da propriedade para lidar com isto.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-120">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="d7eb2-121">WMF 5.0 adicionado um automático `PsDscRunAsCredential` propriedade para todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-121">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="d7eb2-122">Para obter informações sobre como utilizar `PsDscRunAsCredential`, consulte [DSC em execução com as credenciais de utilizador](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="d7eb2-122">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="d7eb2-123">Recursos mais recentes e recursos personalizados podem utilizar esta propriedade automática em vez de criar as seus próprios propriedade credenciais.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-123">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

><span data-ttu-id="d7eb2-124">**Nota:** a estrutura de alguns recursos estão a utilizar várias credenciais para um motivo específico e terá as seus próprios propriedades de credencial.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-124">**Note:** the design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="d7eb2-125">Para localizar a credencial disponível propriedades num recurso utilizam `Get-DscResource -Name ResourceName -Syntax` ou o Intellisense no ISE do (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="d7eb2-125">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="d7eb2-126">Este exemplo utiliza um [grupo](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) recurso do `PSDesiredStateConfiguration` módulo incorporado de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-126">This example uses a [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="d7eb2-127">Pode criar grupos locais e adicionar ou remover membros.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-127">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="d7eb2-128">Aceita ambos o `Credential` propriedade e o automático `PsDscRunAsCredential` propriedade.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-128">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="d7eb2-129">No entanto, o recurso utiliza apenas a `Credential` propriedade.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-129">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="d7eb2-130">Para obter mais informações sobre o `PsDscRunAsCredential` propriedade, consulte [DSC em execução com as credenciais de utilizador](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="d7eb2-130">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="d7eb2-131">Exemplo: O recurso do grupo de propriedade de credencial</span><span class="sxs-lookup"><span data-stu-id="d7eb2-131">Example: The Group resource Credential property</span></span>

<span data-ttu-id="d7eb2-132">É executado DSC `Local System`, pelo que já tem as permissões para alterar os utilizadores e grupos locais.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-132">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="d7eb2-133">Se o membro adicionado é uma conta local, não é necessária nenhuma credencial.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-133">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="d7eb2-134">Se o `Group` recursos adiciona uma conta de domínio ao grupo local, em seguida, é necessária uma credencial.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-134">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="d7eb2-135">Não são permitidas consultas anónimas ao Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-135">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="d7eb2-136">O `Credential` propriedade o `Group` recurso é a conta de domínio utilizada para a consulta do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-136">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="d7eb2-137">Para fins de maioria dos tal poderá dever uma conta de utilizador genérico, por predefinição, os utilizadores podem *ler* maioria dos objetos no Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-137">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="d7eb2-138">Configuração de exemplo</span><span class="sxs-lookup"><span data-stu-id="d7eb2-138">Example Configuration</span></span>

<span data-ttu-id="d7eb2-139">O código de exemplo seguinte utiliza DSC para preencher um grupo local com um utilizador de domínio:</span><span class="sxs-lookup"><span data-stu-id="d7eb2-139">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="d7eb2-140">Este código gera um erro e a mensagem de aviso:</span><span class="sxs-lookup"><span data-stu-id="d7eb2-140">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="d7eb2-141">Neste exemplo tem dois problemas:</span><span class="sxs-lookup"><span data-stu-id="d7eb2-141">This example has two issues:</span></span>
1.  <span data-ttu-id="d7eb2-142">Um erro explica de que as palavras-passe de texto simples não são recomendadas</span><span class="sxs-lookup"><span data-stu-id="d7eb2-142">An error explains that plain text passwords are not recommended</span></span>
2.  <span data-ttu-id="d7eb2-143">Indica um aviso contra a utilização de uma credencial de domínio</span><span class="sxs-lookup"><span data-stu-id="d7eb2-143">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="d7eb2-144">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="d7eb2-144">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="d7eb2-145">A primeira mensagem de erro tem um URL com a documentação.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-145">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="d7eb2-146">Esta ligação explica como encriptar as palavras-passe a utilizar um [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) estrutura e um certificado.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-146">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="d7eb2-147">Para obter mais informações sobre certificados e DSC [ler esta mensagem](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="d7eb2-147">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="d7eb2-148">Para forçar uma palavra-passe de texto simples, o recurso requer o `PsDscAllowPlainTextPassword` secção de palavra-chave dos dados de configuração da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d7eb2-148">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

><span data-ttu-id="d7eb2-149">**Nota:** `NodeName` não pode ser igual asterisco, um nome de nó específico é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-149">**Note:** `NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="d7eb2-150">**Microsoft aconselha para evitar palavras-passe de texto simples devido ao risco de segurança significativo.**</span><span class="sxs-lookup"><span data-stu-id="d7eb2-150">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>
<span data-ttu-id="d7eb2-151">Uma exceção seria ao utilizar o serviço do Automation DSC do Azure, apenas porque os dados são armazenados sempre encriptados (em trânsito, Inativos no serviço e o restante no nó).</span><span class="sxs-lookup"><span data-stu-id="d7eb2-151">An exception would be when using the Azure Automation DSC service, only because the data is always stored encrypted (in transit, at rest in the service, and at rest on the node).</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="d7eb2-152">Credenciais do domínio</span><span class="sxs-lookup"><span data-stu-id="d7eb2-152">Domain Credentials</span></span>

<span data-ttu-id="d7eb2-153">Ainda executar novamente o script de configuração de exemplo (com ou sem encriptação), gera o aviso de que a conta para uma credencial não é recomendada utilizar um domínio.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-153">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="d7eb2-154">Utilizar uma conta local elimina potencial exposição de credenciais de domínio que possam ser utilizados noutros servidores.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-154">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="d7eb2-155">**Ao utilizar as credenciais com recursos de DSC, preferir uma conta local através de uma conta de domínio sempre que possível.**</span><span class="sxs-lookup"><span data-stu-id="d7eb2-155">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="d7eb2-156">Se existir um '\' ou ' @' no `Username` propriedade de credencial, DSC irá processá-lo como uma conta de domínio.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-156">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="d7eb2-157">Há uma exceção para "localhost", "127.0.0.1" e ":: 1" na parte do domínio do nome de utilizador.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-157">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="d7eb2-158">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="d7eb2-158">PSDscAllowDomainUser</span></span>

<span data-ttu-id="d7eb2-159">No DSC `Group` exemplo de recurso acima, consultar um domínio do Active Directory *requer* uma conta de domínio.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-159">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="d7eb2-160">Neste caso, adicione o `PSDscAllowDomainUser` propriedade para o `ConfigurationData` bloquear da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d7eb2-160">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="d7eb2-161">Agora, o script de configuração irá gerar o ficheiro MOF com sem erros ou avisos.</span><span class="sxs-lookup"><span data-stu-id="d7eb2-161">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
