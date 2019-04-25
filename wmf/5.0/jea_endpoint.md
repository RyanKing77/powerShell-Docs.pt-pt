---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3acd266a75bc61ffe4bce467cfb804ac7865c629
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057252"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a><span data-ttu-id="9e19a-102">Criar e Estabelecer Ligação a um Ponto Final da JEA</span><span class="sxs-lookup"><span data-stu-id="9e19a-102">Creating and Connecting to a JEA Endpoint</span></span>

<span data-ttu-id="9e19a-103">Para criar um ponto final JEA, terá de criar e registar um ficheiro de configuração de sessão do PowerShell especialmente configurado, o que pode ser gerado com o **New-PSSessionConfigurationFile** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e19a-103">To create a JEA endpoint, you need to create and register a specially-configured PowerShell Session Configuration file, which can be generated with the **New-PSSessionConfigurationFile** cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

<span data-ttu-id="9e19a-104">Isto irá criar um ficheiro de configuração de sessão parecido com este:</span><span class="sxs-lookup"><span data-stu-id="9e19a-104">This will create a session configuration file that looks like this:</span></span>

```powershell
@{

    # Version number of the schema used for this document
    SchemaVersion = '2.0.0.0'

    # ID used to uniquely identify this document
    GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
    SessionType = 'RestrictedRemoteServer'

    # Directory to place session transcripts for this session configuration
    TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

    # Whether to run this session configuration as the machine's (virtual) administrator account
    RunAsVirtualAccount = $true

    # Groups associated with machine's (virtual) administrator account
    # RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
    RoleDefinitions = @{ 'CONTOSO\NonAdmin_Operators' = @{ 'RoleCapabilities' = 'Maintenance' } }
}
```

<span data-ttu-id="9e19a-105">Ao criar um ponto final JEA, tem de definir os seguintes parâmetros do comando (e as chaves correspondentes no arquivo):</span><span class="sxs-lookup"><span data-stu-id="9e19a-105">When creating a JEA endpoint, the following parameters of the command (and corresponding keys in the file) must be set:</span></span>

1. <span data-ttu-id="9e19a-106">SessionType para RestrictedRemoteServer</span><span class="sxs-lookup"><span data-stu-id="9e19a-106">SessionType to RestrictedRemoteServer</span></span>
2. <span data-ttu-id="9e19a-107">RunAsVirtualAccount para **$true**</span><span class="sxs-lookup"><span data-stu-id="9e19a-107">RunAsVirtualAccount to **$true**</span></span>
3. <span data-ttu-id="9e19a-108">TranscriptPath para o diretório em que "por cima do ombro" transcrições serão guardadas depois de cada sessão</span><span class="sxs-lookup"><span data-stu-id="9e19a-108">TranscriptPath to the directory where "over the shoulder" transcripts will be saved after each session</span></span>
4. <span data-ttu-id="9e19a-109">RoleDefinitions para uma tabela de hash que define os grupos que têm acesso para qual "funcionalidades de função".</span><span class="sxs-lookup"><span data-stu-id="9e19a-109">RoleDefinitions to a hashtable that defines which groups have access to which "Role Capabilities."</span></span> <span data-ttu-id="9e19a-110">Este campo define **quem** pode fazer **o que** neste ponto final.</span><span class="sxs-lookup"><span data-stu-id="9e19a-110">This field defines **who** can do **what** on this endpoint.</span></span> <span data-ttu-id="9e19a-111">Funcionalidades de função são arquivos especiais que serão explicados brevemente.</span><span class="sxs-lookup"><span data-stu-id="9e19a-111">Role Capabilities are special files that will be explained shortly.</span></span>

<span data-ttu-id="9e19a-112">O campo de RoleDefinitions define os grupos que tinham acesso para as funcionalidades de função.</span><span class="sxs-lookup"><span data-stu-id="9e19a-112">The RoleDefinitions field defines which groups had access to which Role Capabilities.</span></span> <span data-ttu-id="9e19a-113">Um recurso de função é um ficheiro que define um conjunto de recursos que vão ser expostas para conectar usuários.</span><span class="sxs-lookup"><span data-stu-id="9e19a-113">A Role Capability is a file that defines a set of capabilities that will be exposed to connecting users.</span></span>
<span data-ttu-id="9e19a-114">Pode criar capacidades de função com o **New-PSRoleCapabilityFile** comando.</span><span class="sxs-lookup"><span data-stu-id="9e19a-114">You can create Role Capabilities with the **New-PSRoleCapabilityFile** command.</span></span>

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

<span data-ttu-id="9e19a-115">Esta ação irá gerar um recurso de função de modelo que tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="9e19a-115">This will generate a template role capability that looks like this:</span></span>

```powershell
@{
    # ID used to uniquely identify this document
    GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Company associated with this document
    CompanyName = 'Unknown'

    # Copyright statement for this document
    Copyright = '(c) 2015 Administrator. All rights reserved.'

    # Modules to import when applied to a session
    # ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

    # Aliases to make visible when applied to a session
    # VisibleAliases = 'Item1', 'Item2'

    # Cmdlets to make visible when applied to a session
    # VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # Functions to make visible when applied to a session
    # VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # External commands (scripts and applications) to make visible when applied to a session
    # VisibleExternalCommands = 'Item1', 'Item2'

    # Providers to make visible when applied to a session
    # VisibleProviders = 'Item1', 'Item2'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # Aliases to be defined when applied to a session
    # AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

    # Functions to define when applied to a session
    # FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

    # Variables to define when applied to a session
    # VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

    # Environment variables to define when applied to a session
    # EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

    # Type files (.ps1xml) to load when applied to a session
    # TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

    # Format files (.ps1xml) to load when applied to a session
    # FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

    # Assemblies to load when applied to a session
    # AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

}
```

<span data-ttu-id="9e19a-116">Para ser utilizado por uma configuração de sessão JEA, funcionalidades de função tem de ser guardadas como um módulo do PowerShell válido num diretório chamado "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="9e19a-116">To be used by a JEA session configuration, Role Capabilities must be saved as a valid PowerShell module in a directory named "RoleCapabilities".</span></span> <span data-ttu-id="9e19a-117">Um módulo pode ter vários arquivos de recurso de função, se assim o desejar.</span><span class="sxs-lookup"><span data-stu-id="9e19a-117">A module may have multiple role capability files, if desired.</span></span>

<span data-ttu-id="9e19a-118">Para começar a configurar os cmdlets, funções, aliases e scripts de um utilizador pode aceder ao ligar a uma sessão JEA, adicione suas próprias regras para o ficheiro de recurso de função a seguir o comentado modelos.</span><span class="sxs-lookup"><span data-stu-id="9e19a-118">To start configuring which cmdlets, functions, aliases, and scripts a user may access when connecting to a JEA session, add your own rules to the Role Capability file following the commented out templates.</span></span> <span data-ttu-id="9e19a-119">Para obter uma visão mais profunda sobre como pode configurar funcionalidades de função, verifique o completo [guia de experiência](http://aka.ms/JEA).</span><span class="sxs-lookup"><span data-stu-id="9e19a-119">For a deeper look into how you can configure Role Capabilities, check out the full [experience guide](http://aka.ms/JEA).</span></span>

<span data-ttu-id="9e19a-120">Por fim, quando tiver terminado de personalizar a sua configuração de sessão e as capacidades de função relacionadas, registar esta configuração de sessão e criar o ponto final através da execução `Register-PSSessionConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="9e19a-120">Finally, once you have finished customizing your session configuration and related Role Capabilities, register this session configuration and create the endpoint by running `Register-PSSessionConfiguration`.</span></span>

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a><span data-ttu-id="9e19a-121">Ligar a um ponto final JEA</span><span class="sxs-lookup"><span data-stu-id="9e19a-121">Connect to a JEA Endpoint</span></span>

<span data-ttu-id="9e19a-122">Ligar a um ponto final JEA funciona da mesma forma, ligar a quaisquer outros trabalhos de ponto final do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e19a-122">Connecting to a JEA Endpoint works the same way connecting to any other PowerShell endpoint works.</span></span>
<span data-ttu-id="9e19a-123">Simplesmente tem que dar o parâmetro de "ConfigurationName" para o seu nome de ponto final JEA **New-PSSession**, **Invoke-Command**, ou **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="9e19a-123">You simply have to give your JEA endpoint name as the "ConfigurationName" parameter for **New-PSSession**, **Invoke-Command**, or **Enter-PSSession**.</span></span>

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```

<span data-ttu-id="9e19a-124">Depois de ter ligado à sessão JEA, estará limitada em execução na lista de permissões a comandos nas capacidades de função tem acesso.</span><span class="sxs-lookup"><span data-stu-id="9e19a-124">Once you have connected to the JEA session, you will be limited to running the commands whitelisted in the Role Capabilities that you have access to.</span></span> <span data-ttu-id="9e19a-125">Se tentar executar qualquer comando não é permitido para a sua função, irá encontrar um erro.</span><span class="sxs-lookup"><span data-stu-id="9e19a-125">If you try to run any command not allowed for your role, you will encounter an error.</span></span>