---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 9065315ef39129e6a28234d972fe350fd5e7e11d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a><span data-ttu-id="dca9f-102">Criar e Estabelecer Ligação a um Ponto Final da JEA</span><span class="sxs-lookup"><span data-stu-id="dca9f-102">Creating and Connecting to a JEA Endpoint</span></span>
<span data-ttu-id="dca9f-103">Para criar um ponto final JEA, tem de criar e registar um ficheiro de configuração de sessão do PowerShell especial configurada, o que pode ser gerado com o **New-PSSessionConfigurationFile** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dca9f-103">To create a JEA endpoint, you need to create and register a specially-configured PowerShell Session Configuration file, which can be generated with the **New-PSSessionConfigurationFile** cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

<span data-ttu-id="dca9f-104">Isto irá criar um ficheiro de configuração de sessão que tem este aspeto:</span><span class="sxs-lookup"><span data-stu-id="dca9f-104">This will create a session configuration file that looks like this:</span></span>
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
RoleDefinitions = @{
    'CONTOSO\NonAdmin_Operators' = @{
        'RoleCapabilities' = 'Maintenance' } }

}
```
<span data-ttu-id="dca9f-105">Ao criar um ponto final JEA, os seguintes parâmetros de comando (e as correspondentes chaves no ficheiro) tem de ser definidos:</span><span class="sxs-lookup"><span data-stu-id="dca9f-105">When creating a JEA endpoint, the following parameters of the command (and corresponding keys in the file) must be set:</span></span>
1.  <span data-ttu-id="dca9f-106">SessionType para RestrictedRemoteServer</span><span class="sxs-lookup"><span data-stu-id="dca9f-106">SessionType to RestrictedRemoteServer</span></span>
2.  <span data-ttu-id="dca9f-107">RunAsVirtualAccount para **$true**</span><span class="sxs-lookup"><span data-stu-id="dca9f-107">RunAsVirtualAccount to **$true**</span></span>
3.  <span data-ttu-id="dca9f-108">TranscriptPath para o diretório onde "ombro o" transcrições serão guardadas após cada sessão</span><span class="sxs-lookup"><span data-stu-id="dca9f-108">TranscriptPath to the directory where “over the shoulder” transcripts will be saved after each session</span></span>
4.  <span data-ttu-id="dca9f-109">RoleDefinitions para uma tabela hash que define quais os grupos têm acesso a quais "capacidades de função".</span><span class="sxs-lookup"><span data-stu-id="dca9f-109">RoleDefinitions to a hashtable that defines which groups have access to which “Role Capabilities.”</span></span>  <span data-ttu-id="dca9f-110">Este campo define **quem** pode fazer **que** neste ponto final.</span><span class="sxs-lookup"><span data-stu-id="dca9f-110">This field defines **who** can do **what** on this endpoint.</span></span>   <span data-ttu-id="dca9f-111">Capacidades de função são ficheiros especiais que serão explicados em breve.</span><span class="sxs-lookup"><span data-stu-id="dca9f-111">Role Capabilities are special files that will be explained shortly.</span></span>


<span data-ttu-id="dca9f-112">O campo de RoleDefinitions define os grupos que tinham acesso que capacidades de função.</span><span class="sxs-lookup"><span data-stu-id="dca9f-112">The RoleDefinitions field defines which groups had access to which Role Capabilities.</span></span>  <span data-ttu-id="dca9f-113">Uma capacidade de função é um ficheiro que define um conjunto de capacidades que irá ser disponibilizado para os utilizadores a ligar.</span><span class="sxs-lookup"><span data-stu-id="dca9f-113">A Role Capability is a file that defines a set of capabilities that will be exposed to connecting users.</span></span>  <span data-ttu-id="dca9f-114">Pode criar capacidades de função com o **New-PSRoleCapabilityFile** comando.</span><span class="sxs-lookup"><span data-stu-id="dca9f-114">You can create Role Capabilities with the **New-PSRoleCapabilityFile** command.</span></span>

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

<span data-ttu-id="dca9f-115">Esta ação irá gerar uma capacidade de função de modelo que tem este aspeto:</span><span class="sxs-lookup"><span data-stu-id="dca9f-115">This will generate a template role capability that looks like this:</span></span>
```
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
<span data-ttu-id="dca9f-116">Para ser utilizado por uma configuração de sessão JEA, capacidades de função tem de ser guardadas como um módulo do PowerShell válido num diretório com o nome "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="dca9f-116">To be used by a JEA session configuration, Role Capabilities must be saved as a valid PowerShell module in a directory named “RoleCapabilities”.</span></span> <span data-ttu-id="dca9f-117">Um módulo pode ter vários ficheiros de capacidade de função, se assim o desejar.</span><span class="sxs-lookup"><span data-stu-id="dca9f-117">A module may have multiple role capability files, if desired.</span></span>

<span data-ttu-id="dca9f-118">Para iniciar a configuração que os cmdlets, funções, aliases e scripts um utilizador pode aceder ao ligar a uma sessão JEA, adicione as suas próprias regras para o ficheiro de capacidade de função, seguindo o comentado os modelos.</span><span class="sxs-lookup"><span data-stu-id="dca9f-118">To start configuring which cmdlets, functions, aliases, and scripts a user may access when connecting to a JEA session, add your own rules to the Role Capability file following the commented out templates.</span></span> <span data-ttu-id="dca9f-119">Para ver mais profundo na forma como pode configurar capacidades de função, veja o completo [experiência guia](http://aka.ms/JEA).</span><span class="sxs-lookup"><span data-stu-id="dca9f-119">For a deeper look into how you can configure Role Capabilities, check out the full [experience guide](http://aka.ms/JEA).</span></span>

<span data-ttu-id="dca9f-120">Por fim, assim que tiver concluído a personalizar a configuração de sessão e as capacidades de função relacionados, registar esta configuração de sessão e criar o ponto final executando **Register-PSSessionConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="dca9f-120">Finally, once you have finished customizing your session configuration and related Role Capabilities, register this session configuration and create the endpoint by running **Register-PSSessionConfiguration**.</span></span>

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a><span data-ttu-id="dca9f-121">Ligar a um ponto final JEA</span><span class="sxs-lookup"><span data-stu-id="dca9f-121">Connect to a JEA Endpoint</span></span>
<span data-ttu-id="dca9f-122">Ligar a um ponto final JEA funciona da mesma forma que a ligação a quaisquer outros trabalhos de ponto final do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dca9f-122">Connecting to a JEA Endpoint works the same way connecting to any other PowerShell endpoint works.</span></span>  <span data-ttu-id="dca9f-123">Basta ter que dar o nome do ponto final JEA o parâmetro "ConfigurationName" **New-PSSession**, **Invoke-Command**, ou **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="dca9f-123">You simply have to give your JEA endpoint name as the “ConfigurationName” parameter for **New-PSSession**, **Invoke-Command**, or **Enter-PSSession**.</span></span>

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
<span data-ttu-id="dca9f-124">Assim que tiver estabelecido ligação à sessão JEA, será limitado em execução na lista de comandos permissões nas capacidades de função que tenha acesso.</span><span class="sxs-lookup"><span data-stu-id="dca9f-124">Once you have connected to the JEA session, you will be limited to running the commands whitelisted in the Role Capabilities that you have access to.</span></span> <span data-ttu-id="dca9f-125">Se tentar executar qualquer comando não permitido para a sua função, irá encontrar um erro.</span><span class="sxs-lookup"><span data-stu-id="dca9f-125">If you try to run any command not allowed for your role, you will encounter an error.</span></span>