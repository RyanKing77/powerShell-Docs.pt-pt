---
ms.date: 10/17/2017
contributor: keithb
keywords: cmdlet do powershell do galeria, psget
title: Versões de pré-lançamento de scripts
ms.openlocfilehash: 4e7eab682008ed57163c51fe3a61a744b347bef2
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002740"
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="be317-103">Versões de pré-lançamento de scripts</span><span class="sxs-lookup"><span data-stu-id="be317-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="be317-104">A partir da versão 1.6.0, PowerShellGet e da galeria do PowerShell fornecem suporte para versões superiores a 1.0.0 como uma versão de pré-lançamento de marcação.</span><span class="sxs-lookup"><span data-stu-id="be317-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="be317-105">Antes desta funcionalidade, os pacotes de pré-lançamento eram limitado a ter um início de versão com 0.</span><span class="sxs-lookup"><span data-stu-id="be317-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="be317-106">O objetivo desses recursos é oferecem maior suporte para [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) Convenção de controle de versão sem perder com versões anteriores a compatibilidade com o PowerShell versões existentes e 3 ou acima versões do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="be317-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="be317-107">Este tópico foca-se os recursos específicos de script.</span><span class="sxs-lookup"><span data-stu-id="be317-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="be317-108">As funcionalidades equivalentes para módulos estão na [versões do módulo de pré-lançamento](module-prerelease-support.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="be317-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="be317-109">Utilizar estas funcionalidades, os publicadores podem identificar um script como versão 2.5.0-alpha e mais tarde lançar uma versão de prontos para produção 2.5.0 que substitui a versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="be317-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="be317-110">Num alto nível, as funcionalidades de pré-lançamento do script incluem:</span><span class="sxs-lookup"><span data-stu-id="be317-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="be317-111">Adicionando o sufixo PrereleaseString para a cadeia de versão no manifesto do script.</span><span class="sxs-lookup"><span data-stu-id="be317-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="be317-112">Quando os scripts é publicado na galeria do PowerShell, estes dados são extraídos de manifesto e utilizados para identificar pacotes de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="be317-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="be317-113">Aquisição de pacotes de pré-lançamento é necessário adicionar o sinalizador - AllowPrerelease para os comandos do PowerShellGet Find-Script, Script de instalação, Script de atualização e Save-Script.</span><span class="sxs-lookup"><span data-stu-id="be317-113">Acquiring prerelease packages requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="be317-114">Se o sinalizador não for especificado, os pacotes de pré-lançamento não será apresentado.</span><span class="sxs-lookup"><span data-stu-id="be317-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="be317-115">Apresentado por Find-Script, Get-InstalledScript e na galeria do PowerShell de versões de script serão apresentadas com o PrereleaseString, como no 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="be317-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="be317-116">Detalhes para as funcionalidades estão incluídas abaixo.</span><span class="sxs-lookup"><span data-stu-id="be317-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="be317-117">Identificar uma versão do script como uma versão de pré-lançamento</span><span class="sxs-lookup"><span data-stu-id="be317-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="be317-118">Suporte do PowerShellGet para versões de pré-lançamento é mais fácil para os scripts do que módulos.</span><span class="sxs-lookup"><span data-stu-id="be317-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="be317-119">Controle de versão do script só é suportado pelo PowerShellGet, pelo que existem não existem problemas de compatibilidade causados por adicionar a cadeia de caracteres de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="be317-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="be317-120">Para identificar um script na galeria do PowerShell como uma versão de pré-lançamento, adicione um sufixo de pré-lançamento para uma cadeia de versão corretamente formatado nos metadados do script.</span><span class="sxs-lookup"><span data-stu-id="be317-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="be317-121">Uma seção de exemplo de um manifesto de script com uma versão de pré-lançamento seria semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="be317-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

<span data-ttu-id="be317-122">Para utilizar um sufixo de pré-lançamento, a cadeia de versão tem de cumprir os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="be317-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="be317-123">Só pode ser especificado um sufixo de pré-lançamento quando a versão é 3 segmentos para major.</span><span class="sxs-lookup"><span data-stu-id="be317-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="be317-124">Isso se alinha com SemVer v1.0.0</span><span class="sxs-lookup"><span data-stu-id="be317-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="be317-125">O sufixo de pré-lançamento é uma cadeia que começa com um hífen e pode conter carateres de alfanuméricos ASCII [0-9A-Za - z-]</span><span class="sxs-lookup"><span data-stu-id="be317-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="be317-126">Apenas SemVer v1.0.0 pré-lançamento cadeias de caracteres são suportadas neste momento, por isso, o sufixo de pré-lançamento **não podem** conter qualquer um dos ponto ou + [. +], que é permitido em SemVer 2.0</span><span class="sxs-lookup"><span data-stu-id="be317-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix **must not** contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="be317-127">Exemplos de cadeias de PrereleaseString suportadas são:-alfa, - alpha1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="be317-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="be317-128">Impacto de controlo de versões de pré-lançamento nas pastas de instalação e a ordem de ordenação</span><span class="sxs-lookup"><span data-stu-id="be317-128">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="be317-129">Ordem de classificação é alterado quando utilizar uma versão de pré-lançamento, que é importante durante a publicação na galeria do PowerShell, e durante a instalação de scripts com comandos do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="be317-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="be317-130">Se dois scripts de versões com o número da versão existe, a ordem de classificação baseia-se a parte da cadeia de caracteres a seguir o hífen.</span><span class="sxs-lookup"><span data-stu-id="be317-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="be317-131">Então, versão 2.5.0-alpha é menor que 2.5.0-beta, que é menor que 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="be317-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="be317-132">Se dois scripts têm o mesmo número de versão e apenas um tem um PrereleaseString, o script **sem** o sufixo de pré-lançamento é considerado como a versão de prontos para produção e será classificado como uma versão mais recente do que a versão de pré-lançamento versão.</span><span class="sxs-lookup"><span data-stu-id="be317-132">If two scripts have the same version number, and only one has a PrereleaseString, the script **without** the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="be317-133">Por exemplo, ao comparar versões 2.5.0 e 2.5.0-beta, o 2.5.0 versão será considerada o maior dos dois.</span><span class="sxs-lookup"><span data-stu-id="be317-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="be317-134">Durante a publicação na galeria do PowerShell, por predefinição a versão do script a ser publicado tem de ter uma versão maior do que qualquer versão publicada anteriormente que está na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be317-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="be317-135">Um publicador pode atualizar a versão 2.5.0-alpha 2.5.0-beta ou com 2.5.0 (com sem sufixo pré-lançamento).</span><span class="sxs-lookup"><span data-stu-id="be317-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="be317-136">Encontrar e adquirir os pacotes de pré-lançamento utilizar comandos do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="be317-136">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="be317-137">Lidar com pacotes de pré-lançamento usando o PowerShellGet Find-Script, Script de instalação, atualização-Script, e os comandos de Save-Script é necessário adicionar o sinalizador - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="be317-137">Dealing with prerelease packages using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="be317-138">Se não for especificado - AllowPrerelease, pacotes de pré-lançamento serão incluído, se estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="be317-138">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="be317-139">Se não for especificado o sinalizador - AllowPrerelease, pacotes de pré-lançamento não será apresentado.</span><span class="sxs-lookup"><span data-stu-id="be317-139">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="be317-140">As únicas exceções a esta nos comandos de script do PowerShellGet são Get-InstalledScript e alguns casos com Script de desinstalação.</span><span class="sxs-lookup"><span data-stu-id="be317-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="be317-141">Get-InstalledScript sempre mostrará automaticamente as informações de pré-lançamento na cadeia de versão se estiver presente.</span><span class="sxs-lookup"><span data-stu-id="be317-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="be317-142">Script de desinstalação irá por predefinição desinstalar a versão mais recente de um script, se **nenhuma versão** está especificado.</span><span class="sxs-lookup"><span data-stu-id="be317-142">Uninstall-Script will by default uninstall the most recent version of a script, if **no version** is specified.</span></span> <span data-ttu-id="be317-143">Esse comportamento não mudou.</span><span class="sxs-lookup"><span data-stu-id="be317-143">That behavior has not changed.</span></span> <span data-ttu-id="be317-144">No entanto, se não for especificada uma versão de pré-lançamento usando `-RequiredVersion`, `-AllowPrerelease` será necessária.</span><span class="sxs-lookup"><span data-stu-id="be317-144">However, if a prerelease version is specified using `-RequiredVersion`, `-AllowPrerelease` will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="be317-145">Exemplos</span><span class="sxs-lookup"><span data-stu-id="be317-145">Examples</span></span>

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
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
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

<span data-ttu-id="be317-146">Script de desinstalação irá remover a versão atual de um script quando - RequiredVersion não é fornecido.</span><span class="sxs-lookup"><span data-stu-id="be317-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="be317-147">Se - RequiredVersion for especificada e é uma versão de pré-lançamento, - AllowPrerelease tem de ser adicionado ao comando.</span><span class="sxs-lookup"><span data-stu-id="be317-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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

## <a name="more-details"></a><span data-ttu-id="be317-148">Obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="be317-148">More details</span></span>

- [<span data-ttu-id="be317-149">Versões de pré-lançamento do módulo</span><span class="sxs-lookup"><span data-stu-id="be317-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="be317-150">Find-script</span><span class="sxs-lookup"><span data-stu-id="be317-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="be317-151">Script de instalação</span><span class="sxs-lookup"><span data-stu-id="be317-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="be317-152">Save-script</span><span class="sxs-lookup"><span data-stu-id="be317-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="be317-153">Script de atualização</span><span class="sxs-lookup"><span data-stu-id="be317-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="be317-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="be317-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="be317-155">Script de desinstalação</span><span class="sxs-lookup"><span data-stu-id="be317-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)
