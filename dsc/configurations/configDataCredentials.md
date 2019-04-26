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
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="de100-103">Opções de credenciais nos dados de configuração</span><span class="sxs-lookup"><span data-stu-id="de100-103">Credentials Options in Configuration Data</span></span>

><span data-ttu-id="de100-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="de100-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="de100-105">As palavras-passe de texto sem formatação e utilizadores de domínio</span><span class="sxs-lookup"><span data-stu-id="de100-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="de100-106">Configurações de DSC que contém uma credencial sem encriptação irão gerar uma mensagem de erro sobre palavras-passe de texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="de100-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="de100-107">Além disso, DSC irá gerar um aviso ao utilizar as credenciais de domínio.</span><span class="sxs-lookup"><span data-stu-id="de100-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="de100-108">Para suprimir estas mensagens de aviso de erro e utilizam as palavras-chave da data do configuração de DSC:</span><span class="sxs-lookup"><span data-stu-id="de100-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="de100-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="de100-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="de100-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="de100-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="de100-111">Armazenar/transmitir palavras-passe de texto sem formatação não encriptados, normalmente, não é seguro.</span><span class="sxs-lookup"><span data-stu-id="de100-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="de100-112">É recomendado proteger credenciais usando as técnicas abordadas mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="de100-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="de100-113">O serviço de DSC de automatização do Azure permite-lhe gerir centralmente as credenciais para ser compilado em configurações e armazenado em segurança.</span><span class="sxs-lookup"><span data-stu-id="de100-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="de100-114">Para obter informações, consulte: [Compilar configurações do DSC / recursos de credencial](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="de100-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="de100-115">Processamento de credenciais no DSC</span><span class="sxs-lookup"><span data-stu-id="de100-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="de100-116">Recursos de configuração de DSC executam como `Local System` por predefinição.</span><span class="sxs-lookup"><span data-stu-id="de100-116">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="de100-117">No entanto, alguns recursos tem uma credencial, por exemplo quando o `Package` recursos tem de instalar software numa conta de utilizador específico.</span><span class="sxs-lookup"><span data-stu-id="de100-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="de100-118">Recursos anteriores utilizados codificados `Credential` nome da propriedade de lidar com isso.</span><span class="sxs-lookup"><span data-stu-id="de100-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="de100-119">WMF 5.0 adicionado um automático `PsDscRunAsCredential` propriedade para todos os recursos.</span><span class="sxs-lookup"><span data-stu-id="de100-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="de100-120">Para obter informações sobre como utilizar `PsDscRunAsCredential`, consulte [executar o DSC com as credenciais de utilizador](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="de100-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="de100-121">Recursos mais recentes e recursos personalizados podem utilizar esta propriedade automática em vez de criar sua própria propriedade credenciais.</span><span class="sxs-lookup"><span data-stu-id="de100-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="de100-122">O design de alguns recursos estão a utilizar várias credenciais por um motivo específico, e eles terão suas próprias propriedades de credencial.</span><span class="sxs-lookup"><span data-stu-id="de100-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="de100-123">Para localizar a credencial disponível propriedades num recurso de usam `Get-DscResource -Name ResourceName -Syntax` ou o Intellisense no ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="de100-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="de100-124">Este exemplo utiliza um [grupo](../resources/resources.md) recursos do `PSDesiredStateConfiguration` módulo de recursos de DSC incorporado.</span><span class="sxs-lookup"><span data-stu-id="de100-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="de100-125">Pode criar grupos locais e adicionar ou remover membros.</span><span class="sxs-lookup"><span data-stu-id="de100-125">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="de100-126">Ela aceita ambos os `Credential` propriedade e o automático `PsDscRunAsCredential` propriedade.</span><span class="sxs-lookup"><span data-stu-id="de100-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="de100-127">No entanto, o recurso utiliza apenas o `Credential` propriedade.</span><span class="sxs-lookup"><span data-stu-id="de100-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="de100-128">Para obter mais informações sobre o `PsDscRunAsCredential` propriedade, veja [executar o DSC com as credenciais de utilizador](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="de100-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="de100-129">Exemplo: O recurso do grupo de propriedade de credencial</span><span class="sxs-lookup"><span data-stu-id="de100-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="de100-130">DSC é executado sob `Local System`, pelo que já tem permissões para alterar os utilizadores e grupos locais.</span><span class="sxs-lookup"><span data-stu-id="de100-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="de100-131">Se o membro adicionado é uma conta local, não existem credenciais é necessário.</span><span class="sxs-lookup"><span data-stu-id="de100-131">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="de100-132">Se o `Group` recurso adiciona uma conta de domínio ao grupo local, em seguida, é necessária uma credencial.</span><span class="sxs-lookup"><span data-stu-id="de100-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="de100-133">Anónimas consultas ao Active Directory não são permitidas.</span><span class="sxs-lookup"><span data-stu-id="de100-133">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="de100-134">O `Credential` propriedade o `Group` recurso é a conta de domínio utilizada para consultar o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="de100-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="de100-135">Para a maioria das finalidades possível uma conta de utilizador genérica, que por padrão, os utilizadores podem *ler* maioria dos objetos no Active Directory.</span><span class="sxs-lookup"><span data-stu-id="de100-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="de100-136">Exemplo de configuração</span><span class="sxs-lookup"><span data-stu-id="de100-136">Example Configuration</span></span>

<span data-ttu-id="de100-137">O código de exemplo seguinte utiliza DSC para preencher um grupo local com um utilizador de domínio:</span><span class="sxs-lookup"><span data-stu-id="de100-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="de100-138">Esse código gera um erro e a mensagem de aviso:</span><span class="sxs-lookup"><span data-stu-id="de100-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="de100-139">Neste exemplo tem dois problemas:</span><span class="sxs-lookup"><span data-stu-id="de100-139">This example has two issues:</span></span>

1. <span data-ttu-id="de100-140">Um erro explica de que as palavras-passe de texto simples não são recomendadas</span><span class="sxs-lookup"><span data-stu-id="de100-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="de100-141">Um aviso aconselha-se contra a utilização de uma credencial de domínio</span><span class="sxs-lookup"><span data-stu-id="de100-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="de100-142">Os sinalizadores **PSDSCAllowPlainTextPassword** e **PSDSCAllowDomainUser** suprimir o erro e aviso a informar o utilizador do risco envolvido.</span><span class="sxs-lookup"><span data-stu-id="de100-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="de100-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="de100-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="de100-144">A primeira mensagem de erro tem um URL com a documentação.</span><span class="sxs-lookup"><span data-stu-id="de100-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="de100-145">Esta ligação explica como encriptar palavras-passe utilizando um [ConfigurationData](./configData.md) estrutura e um certificado.</span><span class="sxs-lookup"><span data-stu-id="de100-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="de100-146">Para obter mais informações sobre certificados e DSC [leia esta postagem](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="de100-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="de100-147">Para forçar uma palavra-passe de texto sem formatação, o recurso requer o `PsDscAllowPlainTextPassword` secção de palavra-chave nos dados de configuração da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="de100-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="de100-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="de100-148">localhost.mof</span></span>

<span data-ttu-id="de100-149">O **PSDSCAllowPlainTextPassword** sinalizador requer que o utilizador reconhece o risco de armazenar as palavras-passe de texto sem formatação num arquivo MOF.</span><span class="sxs-lookup"><span data-stu-id="de100-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="de100-150">No ficheiro MOF gerado, mesmo que um **PSCredential** objeto que contém um **SecureString** foi usada, as palavras-passe continuarão a ser apresentados como texto simples.</span><span class="sxs-lookup"><span data-stu-id="de100-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="de100-151">Este é o único momento em que as credenciais são expostas.</span><span class="sxs-lookup"><span data-stu-id="de100-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="de100-152">Obter acesso a isso permite o ficheiro MOF alguém aceder à conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="de100-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="de100-153">Credenciais em trânsito e em inatividade</span><span class="sxs-lookup"><span data-stu-id="de100-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="de100-154">O **PSDscAllowPlainTextPassword** sinalizador permite que a compilação de arquivos MOF, que contêm as palavras-passe em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="de100-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span>
  <span data-ttu-id="de100-155">Tome medidas ao armazenar ficheiros MOF que contém as palavras-passe de texto não encriptado.</span><span class="sxs-lookup"><span data-stu-id="de100-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="de100-156">Quando o ficheiro MOF é entregue a um nó **Push** modo, o WinRM encripta a comunicação para proteger a palavra-passe de texto não criptografado, a menos que substituir a predefinição com o **AllowUnencrypted** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="de100-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="de100-157">Encriptar o MOF com um certificado protege o ficheiro MOF em repouso antes que tenha sido aplicada a um nó.</span><span class="sxs-lookup"><span data-stu-id="de100-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="de100-158">Na **Pull** modo, pode configurar o servidor de solicitação do Windows para utilizar HTTPS para criptografar o tráfego utilizando o protocolo especificado no servidor de informações da Internet.</span><span class="sxs-lookup"><span data-stu-id="de100-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="de100-159">Para obter mais informações, consulte os artigos [como configurar um cliente de solicitação de DSC](../pull-server/pullclient.md) e [ficheiros MOF proteger com certificados](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="de100-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="de100-160">Na [configuração de estado de automatização do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) serviço Pull de tráfego é sempre encriptado.</span><span class="sxs-lookup"><span data-stu-id="de100-160">In the [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="de100-161">No nó, ficheiros MOF são encriptados em inatividade a partir do PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="de100-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="de100-162">No PowerShell 4.0 MOF ficheiros são encriptados em inatividade, a menos que eles são criptografados com um certificado quando enviada por push ou obtidas para o nó.</span><span class="sxs-lookup"><span data-stu-id="de100-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="de100-163">**Microsoft solicitará para evitar palavras-passe de texto sem formatação devido ao risco de segurança significativo.**</span><span class="sxs-lookup"><span data-stu-id="de100-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="de100-164">Credenciais de domínio</span><span class="sxs-lookup"><span data-stu-id="de100-164">Domain Credentials</span></span>

<span data-ttu-id="de100-165">Ainda executar novamente o script de configuração de exemplo (com ou sem encriptação), gera o aviso que conta para uma credencial não é recomendada utilizar um domínio.</span><span class="sxs-lookup"><span data-stu-id="de100-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="de100-166">Com uma conta local elimina a exposição potencial das credenciais de domínio que poderiam ser usadas em outros servidores.</span><span class="sxs-lookup"><span data-stu-id="de100-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="de100-167">**Ao utilizar as credenciais com recursos de DSC, prefira uma conta local através de uma conta de domínio, sempre que possível.**</span><span class="sxs-lookup"><span data-stu-id="de100-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="de100-168">Se existir um '\\'ou'\@' no `Username` propriedade de credencial, em seguida, o DSC irá processá-lo como uma conta de domínio.</span><span class="sxs-lookup"><span data-stu-id="de100-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="de100-169">Existe uma exceção para "localhost", "127.0.0.1", e ":: 1" na parte do domínio do nome do utilizador.</span><span class="sxs-lookup"><span data-stu-id="de100-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="de100-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="de100-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="de100-171">Na DSC `Group` exemplo de recurso acima, consultar o domínio do Active Directory *requer* uma conta de domínio.</span><span class="sxs-lookup"><span data-stu-id="de100-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="de100-172">Neste caso adicione a `PSDscAllowDomainUser` propriedade o `ConfigurationData` bloquear da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="de100-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="de100-173">Agora, o script de configuração irá gerar o ficheiro MOF sem erros ou avisos.</span><span class="sxs-lookup"><span data-stu-id="de100-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
