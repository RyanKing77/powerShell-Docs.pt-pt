---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Versões de pré-lançamento de scripts
ms.openlocfilehash: 2c7e1cbc352f8dc39fef9cd968b2f0c1964c30b3
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="68ab9-103">Versões de pré-lançamento de scripts</span><span class="sxs-lookup"><span data-stu-id="68ab9-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="68ab9-104">A partir da versão 1.6.0, PowerShellGet e galeria do PowerShell fornecem suporte para marcação maiores 1.0.0 como uma pré-lançamento versões.</span><span class="sxs-lookup"><span data-stu-id="68ab9-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="68ab9-105">Antes desta funcionalidade, os itens de pré-lançamento foram limitadas ao facto de ter um início de versão com 0.</span><span class="sxs-lookup"><span data-stu-id="68ab9-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="68ab9-106">O objetivo destas funcionalidades é oferecem maior suporte para [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) Convenção de controlo de versões sem ultrapassar efeitos de compatibilidade com o PowerShell versões existentes e 3 ou acima versões do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="68ab9-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="68ab9-107">Este tópico centra-se as funcionalidades específicas do script.</span><span class="sxs-lookup"><span data-stu-id="68ab9-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="68ab9-108">As funcionalidades equivalentes para módulos são no [versões do módulo de pré-lançamento](module-prerelease-support.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="68ab9-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="68ab9-109">Utilizar estas funcionalidades, publicadores podem identificar um script como versão 2.5.0-alpha e mais tarde na versão de um prontos para produção 2.5.0 que substitui a versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="68ab9-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="68ab9-110">Um nível elevado, as funcionalidades de pré-lançamento script incluem:</span><span class="sxs-lookup"><span data-stu-id="68ab9-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="68ab9-111">Adicionar um sufixo de PrereleaseString para a cadeia de versão no manifesto de script.</span><span class="sxs-lookup"><span data-stu-id="68ab9-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="68ab9-112">Quando os scripts for publicado na galeria do PowerShell, estes dados são extraídos do manifesto e utilizados para identificar os itens de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="68ab9-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
- <span data-ttu-id="68ab9-113">Adquirir itens pré-lançamento exija a adição de sinalizador - AllowPrerelease para os comandos de PowerShellGet Script localizar, Script de instalação, Script de atualização e o Script de guardar.</span><span class="sxs-lookup"><span data-stu-id="68ab9-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="68ab9-114">Se não for especificado o sinalizador, itens de pré-lançamento não serão apresentados.</span><span class="sxs-lookup"><span data-stu-id="68ab9-114">If the flag is not specified, prerelease items will not be shown.</span></span>
- <span data-ttu-id="68ab9-115">Versões de script apresentadas localizar-o script Get-InstalledScript e na galeria do PowerShell serão apresentadas com PrereleaseString, tal como em 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="68ab9-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="68ab9-116">Detalhes para as funcionalidades são incluídos abaixo.</span><span class="sxs-lookup"><span data-stu-id="68ab9-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="68ab9-117">Identificar uma versão do script como uma pré-lançamento</span><span class="sxs-lookup"><span data-stu-id="68ab9-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="68ab9-118">Suporte de PowerShellGet para versões de pré-lançamento é mais fácil para os scripts de módulos.</span><span class="sxs-lookup"><span data-stu-id="68ab9-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="68ab9-119">Controlo de versões do script só é suportado pelo PowerShellGet, pelo que existem não existem problemas de compatibilidade causados por adicionar a cadeia de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="68ab9-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="68ab9-120">Para identificar um script na galeria do PowerShell como uma pré-lançamento, adicione um sufixo de pré-lançamento para uma cadeia de versão corretamente formatado nos metadados do script.</span><span class="sxs-lookup"><span data-stu-id="68ab9-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="68ab9-121">Uma secção de exemplo de um manifesto de script com uma versão de pré-lançamento deverá ter o seguinte aspeto:</span><span class="sxs-lookup"><span data-stu-id="68ab9-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

<span data-ttu-id="68ab9-122">Para utilizar um sufixo de pré-lançamento, a cadeia de versão tem de cumprir os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="68ab9-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="68ab9-123">Só pode ser especificado um sufixo de pré-lançamento quando a versão 3 segmentos para major.</span><span class="sxs-lookup"><span data-stu-id="68ab9-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="68ab9-124">Isto está alinhada com SemVer v1.0.0</span><span class="sxs-lookup"><span data-stu-id="68ab9-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="68ab9-125">O sufixo de pré-lançamento é uma cadeia que começa com um hífen e pode conter ASCII alphanumerics [0-9A-Za - z-]</span><span class="sxs-lookup"><span data-stu-id="68ab9-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="68ab9-126">Cadeias de pré-lançamento apenas SemVer v1.0.0 são suportadas neste momento, por isso, o sufixo de pré-lançamento __tem não__ conter qualquer período ou + [. +], que são permitidos em SemVer 2.0</span><span class="sxs-lookup"><span data-stu-id="68ab9-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix __must not__ contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="68ab9-127">Exemplos de cadeias de PrereleaseString suportadas são:-alpha, - alpha1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="68ab9-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="68ab9-128">__Impacto de controlo de versões de pré-lançamento nas pastas de instalação e a ordem de ordenação__</span><span class="sxs-lookup"><span data-stu-id="68ab9-128">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="68ab9-129">Sequência de ordenação alterações ao utilizar uma versão de pré-lançamento, que é importante quando publicar a galeria do PowerShell, e quando a instalação de scripts com PowerShellGet comandos.</span><span class="sxs-lookup"><span data-stu-id="68ab9-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="68ab9-130">Se dois scripts versões com o número de versão existe, a sequência de ordenação baseia-se na parte de cadeia seguir o hífen.</span><span class="sxs-lookup"><span data-stu-id="68ab9-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="68ab9-131">Por isso, versão 2.5.0-alpha é inferior ao 2.5.0-beta, que é inferior ao 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="68ab9-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="68ab9-132">Se dois scripts têm o mesmo número de versão e apenas um tiver um PrereleaseString, o script __sem__ o sufixo de pré-lançamento é pressupõe-se que a versão de prontos para produção e irá ser ordenado como uma versão superior que o pré-lançamento versão.</span><span class="sxs-lookup"><span data-stu-id="68ab9-132">If two scripts have the same version number, and only one has a PrereleaseString, the script __without__ the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="68ab9-133">Por exemplo, quando a comparação com versões 2.5.0 e 2.5.0-beta, o 2.5.0 versão será considerada superior dos dois.</span><span class="sxs-lookup"><span data-stu-id="68ab9-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="68ab9-134">Quando publicar a galeria do PowerShell, por predefinição a versão do script a ser publicado tem de ter uma versão superior que qualquer versão anteriormente publicado na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68ab9-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="68ab9-135">Um fabricante poderá atualizar versão 2.5.0-alpha 2.5.0-beta ou com 2.5.0 (com o sufixo não pré-lançamento).</span><span class="sxs-lookup"><span data-stu-id="68ab9-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="68ab9-136">Encontrar e adquirir itens pré-lançamento utilizando comandos de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="68ab9-136">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="68ab9-137">Lidar com itens de pré-lançamento utilizando o Script-PowerShellGet localizar Script, Script de instalação, atualização, e os comandos de Script de guardar necessita de adicionar o sinalizador - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="68ab9-137">Dealing with prerelease items using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="68ab9-138">Se não for especificado - AllowPrerelease, itens de pré-lançamento será incluídos, se estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="68ab9-138">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span> <span data-ttu-id="68ab9-139">Se não for especificado o sinalizador - AllowPrerelease, itens de pré-lançamento não serão apresentados.</span><span class="sxs-lookup"><span data-stu-id="68ab9-139">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="68ab9-140">As únicas exceções a este nos comandos de script PowerShellGet são Get-InstalledScript e alguns casos com Script de desinstalação.</span><span class="sxs-lookup"><span data-stu-id="68ab9-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="68ab9-141">Get-InstalledScript sempre automaticamente mostrará as informações de pré-lançamento na cadeia de versão se estiver presente.</span><span class="sxs-lookup"><span data-stu-id="68ab9-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="68ab9-142">Script de desinstalação irá por predefinição desinstalar a versão mais recente de um script, se __nenhuma versão__ está especificado.</span><span class="sxs-lookup"><span data-stu-id="68ab9-142">Uninstall-Script will by default uninstall the most recent version of a script, if __no version__ is specified.</span></span> <span data-ttu-id="68ab9-143">Se o comportamento não foi alterado.</span><span class="sxs-lookup"><span data-stu-id="68ab9-143">That behavior has not changed.</span></span> <span data-ttu-id="68ab9-144">No entanto, se não for especificada uma versão de pré-lançamento utilizando - RequiredVersion, - AllowPrerelease será necessário.</span><span class="sxs-lookup"><span data-stu-id="68ab9-144">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="68ab9-145">Exemplos</span><span class="sxs-lookup"><span data-stu-id="68ab9-145">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

<span data-ttu-id="68ab9-146">Script de desinstalação irá remover a versão atual de um script quando - RequiredVersion não é fornecido.</span><span class="sxs-lookup"><span data-stu-id="68ab9-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="68ab9-147">Se - RequiredVersion for especificado, não sendo uma pré-lançamento, - AllowPrerelease tem de ser adicionado ao comando.</span><span class="sxs-lookup"><span data-stu-id="68ab9-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a><span data-ttu-id="68ab9-148">obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="68ab9-148">More details</span></span>

- [<span data-ttu-id="68ab9-149">Versões de pré-lançamento do módulo</span><span class="sxs-lookup"><span data-stu-id="68ab9-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="68ab9-150">Encontrar o script</span><span class="sxs-lookup"><span data-stu-id="68ab9-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="68ab9-151">Script de instalação</span><span class="sxs-lookup"><span data-stu-id="68ab9-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="68ab9-152">Script de guardar</span><span class="sxs-lookup"><span data-stu-id="68ab9-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="68ab9-153">Script de atualização</span><span class="sxs-lookup"><span data-stu-id="68ab9-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="68ab9-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="68ab9-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="68ab9-155">Script de desinstalação</span><span class="sxs-lookup"><span data-stu-id="68ab9-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)