---
ms.date: 09/26/2017
contributor: keithb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: PrereleaseModule
ms.openlocfilehash: 1fc08cbba90e3eb8ca7d280e4d279af1d8aa279f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="7ce45-103">Versões de pré-lançamento do módulo</span><span class="sxs-lookup"><span data-stu-id="7ce45-103">Prerelease Module Versions</span></span>
<span data-ttu-id="7ce45-104">A partir da versão 1.6.0, PowerShellGet e galeria do PowerShell fornecem suporte para marcação maiores 1.0.0 como uma pré-lançamento versões.</span><span class="sxs-lookup"><span data-stu-id="7ce45-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="7ce45-105">Antes desta funcionalidade, os itens de pré-lançamento foram limitadas ao facto de ter um início de versão com 0.</span><span class="sxs-lookup"><span data-stu-id="7ce45-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="7ce45-106">O objetivo destas funcionalidades é oferecem maior suporte para [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) Convenção de controlo de versões sem ultrapassar efeitos de compatibilidade com o PowerShell versões existentes e 3 ou acima versões do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="7ce45-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="7ce45-107">Este tópico centra-se as funcionalidades específicas do módulo.</span><span class="sxs-lookup"><span data-stu-id="7ce45-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="7ce45-108">As funcionalidades equivalentes para os scripts estão no [versões de pré-lançamento de Scripts](../script/PrereleaseScript.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="7ce45-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](../script/PrereleaseScript.md) topic.</span></span> <span data-ttu-id="7ce45-109">Utilizar estas funcionalidades, publicadores podem identificar um módulo ou script como versão 2.5.0-alpha e mais tarde na versão de um prontos para produção 2.5.0 que substitui a versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="7ce45-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="7ce45-110">Um nível elevado, as funcionalidades de pré-lançamento módulo incluem:</span><span class="sxs-lookup"><span data-stu-id="7ce45-110">At a high level, the prerelease module features include:</span></span>

* <span data-ttu-id="7ce45-111">Adicionar uma cadeia de pré-lançamento à secção PSData do manifesto do módulo identifica o módulo como uma versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="7ce45-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span>
<span data-ttu-id="7ce45-112">Quando o módulo for publicado na galeria do PowerShell, estes dados são extraídos do manifesto e utilizados para identificar os itens de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="7ce45-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
* <span data-ttu-id="7ce45-113">Adquirir itens pré-lançamento exija a adição de sinalizador - AllowPrerelease para os comandos de PowerShellGet módulo de encontrar o módulo de instalação, atualização módulo e o módulo de guardar.</span><span class="sxs-lookup"><span data-stu-id="7ce45-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Module, Install-Module, Update-Module, and Save-Module.</span></span>
<span data-ttu-id="7ce45-114">Se não for especificado o sinalizador, itens de pré-lançamento não serão apresentados.</span><span class="sxs-lookup"><span data-stu-id="7ce45-114">If the flag is not specified, prerelease items will not be shown.</span></span>
* <span data-ttu-id="7ce45-115">Serão apresentadas como uma cadeia única com a cadeia de pré-lançamento anexada, tal como em 2.5.0-alpha versões de módulo apresentadas pelo módulo de localizar, Get-InstalledModule e na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ce45-115">Module versions displayed by Find-Module, Get-InstalledModule, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="7ce45-116">Detalhes para as funcionalidades são incluídos abaixo.</span><span class="sxs-lookup"><span data-stu-id="7ce45-116">Details for the features are included below.</span></span>

<span data-ttu-id="7ce45-117">Estas alterações não afetam o suporte de versão do módulo que está incorporado no PowerShell e são compatíveis com o PowerShell 3.0, 4.0 e 5.</span><span class="sxs-lookup"><span data-stu-id="7ce45-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="7ce45-118">Identificar uma versão do módulo como uma pré-lançamento</span><span class="sxs-lookup"><span data-stu-id="7ce45-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="7ce45-119">O suporte para versões de pré-lançamento PowerShellGet requer a utilização de dois campos no manifesto de módulo:</span><span class="sxs-lookup"><span data-stu-id="7ce45-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

* <span data-ttu-id="7ce45-120">ModuleVersion incluído no manifesto do módulo tem de ser uma versão 3 partes se for utilizada uma versão de pré-lançamento e deve ser compatível com controlo de versões existente do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ce45-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="7ce45-121">O formato de versão seria A.B.C, onde A, B e C estão todos os números inteiros.</span><span class="sxs-lookup"><span data-stu-id="7ce45-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
* <span data-ttu-id="7ce45-122">A cadeia de pré-lançamento é especificada no manifesto do módulo, na secção PSData PrivateData.</span><span class="sxs-lookup"><span data-stu-id="7ce45-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>
<span data-ttu-id="7ce45-123">Os requisitos detalhados na cadeia de pré-lançamento estão abaixo.</span><span class="sxs-lookup"><span data-stu-id="7ce45-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="7ce45-124">Uma secção de exemplo de um manifesto de módulo que define um módulo como uma pré-lançamento seria o seguinte aspeto:</span><span class="sxs-lookup"><span data-stu-id="7ce45-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>
```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="7ce45-125">Os requisitos detalhados para a cadeia de pré-lançamento são:</span><span class="sxs-lookup"><span data-stu-id="7ce45-125">The detailed requirements for Prerelease string are:</span></span>

* <span data-ttu-id="7ce45-126">Cadeia de pré-lançamento só pode ser especificada quando o ModuleVersion é 3 segmentos para major.</span><span class="sxs-lookup"><span data-stu-id="7ce45-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="7ce45-127">Isto está alinhada com SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="7ce45-127">This aligns with SemVer v1.0.0.</span></span>
* <span data-ttu-id="7ce45-128">Um hífen é o delimitador entre o número de compilação e a cadeia de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="7ce45-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="7ce45-129">Um hífen pode ser incluído na cadeia de pré-lançamento, como o primeiro caráter, apenas.</span><span class="sxs-lookup"><span data-stu-id="7ce45-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
* <span data-ttu-id="7ce45-130">A cadeia de pré-lançamento pode conter apenas ASCII alphanumerics [0-9A-Za - z-].</span><span class="sxs-lookup"><span data-stu-id="7ce45-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="7ce45-131">É uma melhor prática para iniciar a pré-lançamento cadeia com um caráter alfa, tal como será mais fácil de identificar que esta é uma versão de pré-lançamento quando efetua a análise de uma lista de itens.</span><span class="sxs-lookup"><span data-stu-id="7ce45-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of items.</span></span>
* <span data-ttu-id="7ce45-132">Apenas SemVer v1.0.0 pré-lançamento cadeias são suportadas neste momento.</span><span class="sxs-lookup"><span data-stu-id="7ce45-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="7ce45-133">Cadeia de pré-lançamento __tem não__ conter qualquer um dos período ou + [. +], que são permitidos em SemVer 2.0.</span><span class="sxs-lookup"><span data-stu-id="7ce45-133">Prerelease string __must not__ contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
* <span data-ttu-id="7ce45-134">Exemplos de cadeias de pré-lançamento suportados são:-alpha, - alpha1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="7ce45-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="7ce45-135">__Impacto de controlo de versões de pré-lançamento nas pastas de instalação e a ordem de ordenação__</span><span class="sxs-lookup"><span data-stu-id="7ce45-135">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="7ce45-136">Sequência de ordenação é alterado quando utilizar uma versão de pré-lançamento, que é importante quando publicar a galeria do PowerShell, e quando instalar módulos com PowerShellGet comandos.</span><span class="sxs-lookup"><span data-stu-id="7ce45-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span>
<span data-ttu-id="7ce45-137">Se a cadeia de pré-lançamento é especificada para dois módulos, a sequência de ordenação baseia-se na parte de cadeia seguir o hífen.</span><span class="sxs-lookup"><span data-stu-id="7ce45-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="7ce45-138">Por isso, versão 2.5.0-alpha é inferior ao 2.5.0-beta, que é inferior ao 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="7ce45-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span>
<span data-ttu-id="7ce45-139">Se dois módulos tem o mesmo ModuleVersion e apenas um tiver uma cadeia de pré-lançamento, o módulo sem a cadeia de pré-lançamento é pressupõe-se que a versão de prontos para produção e irá ser ordenado como uma versão superior à versão de pré-lançamento (que inclui a pré-lançamento cadeia).</span><span class="sxs-lookup"><span data-stu-id="7ce45-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span>
<span data-ttu-id="7ce45-140">Por exemplo, quando a comparação com versões 2.5.0 e 2.5.0-beta, o 2.5.0 versão será considerada superior dos dois.</span><span class="sxs-lookup"><span data-stu-id="7ce45-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="7ce45-141">Quando publicar a galeria do PowerShell, por predefinição a versão do módulo que está a ser publicado tem de ter uma versão superior que qualquer versão anteriormente publicado na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ce45-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="7ce45-142">Encontrar e adquirir itens pré-lançamento utilizando comandos de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="7ce45-142">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="7ce45-143">Lidar com itens de pré-lançamento utilizando PowerShellGet localizar-Module, módulo de instalação, atualização-Module, e necessita de comandos do módulo de guardar o sinalizador - AllowPrerelease a adicionar.</span><span class="sxs-lookup"><span data-stu-id="7ce45-143">Dealing with prerelease items using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span>
<span data-ttu-id="7ce45-144">Se não for especificado - AllowPrerelease, itens de pré-lançamento será incluídos, se estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="7ce45-144">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span>
<span data-ttu-id="7ce45-145">Se não for especificado o sinalizador - AllowPrerelease, itens de pré-lançamento não serão apresentados.</span><span class="sxs-lookup"><span data-stu-id="7ce45-145">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="7ce45-146">As únicas exceções a este nos comandos módulo PowerShellGet são Get-InstalledModule e alguns casos com o módulo de desinstalação.</span><span class="sxs-lookup"><span data-stu-id="7ce45-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

* <span data-ttu-id="7ce45-147">Get-InstalledModule sempre automaticamente mostrará as informações de pré-lançamento na cadeia de versão para módulos.</span><span class="sxs-lookup"><span data-stu-id="7ce45-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
* <span data-ttu-id="7ce45-148">Módulo de desinstalação irá por predefinição desinstalar a versão mais recente de um módulo, se __nenhuma versão__ está especificado.</span><span class="sxs-lookup"><span data-stu-id="7ce45-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="7ce45-149">Se o comportamento não foi alterado.</span><span class="sxs-lookup"><span data-stu-id="7ce45-149">That behavior has not changed.</span></span> <span data-ttu-id="7ce45-150">No entanto, se não for especificada uma versão de pré-lançamento utilizando - RequiredVersion, - AllowPrerelease será necessário.</span><span class="sxs-lookup"><span data-stu-id="7ce45-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="7ce45-151">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7ce45-151">Examples</span></span>
```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="7ce45-152">Não é suportada a instalação lado a lado das versões de um módulo que diferem apenas devido a pré-lançamento especificada.</span><span class="sxs-lookup"><span data-stu-id="7ce45-152">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span>
<span data-ttu-id="7ce45-153">Ao instalar um módulo com o PowerShellGet, versões diferentes do mesmo módulo são instalado do lado do lado a lado através da criação de um nome de pasta com o ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="7ce45-153">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span>
<span data-ttu-id="7ce45-154">ModuleVersion, sem a cadeia de pré-lançamento, é utilizada para o nome da pasta.</span><span class="sxs-lookup"><span data-stu-id="7ce45-154">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span>
<span data-ttu-id="7ce45-155">Se um utilizador instala MyModule versão 2.5.0-alpha, será instalado para a pasta de MyModule\2.5.0.</span><span class="sxs-lookup"><span data-stu-id="7ce45-155">If a user installs MyModule version 2.5.0-alpha, it will be installed to the MyModule\2.5.0 folder.</span></span>
<span data-ttu-id="7ce45-156">Se o utilizador instala, em seguida, 2.5.0-beta, a versão de 2.5.0-beta será __escrita superior__ o conteúdo da pasta MyModule\2.5.0.</span><span class="sxs-lookup"><span data-stu-id="7ce45-156">If the user then installs 2.5.0-beta, the 2.5.0-beta version will __over-write__ the contents of the folder MyModule\2.5.0.</span></span>
<span data-ttu-id="7ce45-157">Uma vantagem para esta abordagem é que não é necessário para desinstalar a versão de pré-lançamento depois de instalar a versão de prontos para produção.</span><span class="sxs-lookup"><span data-stu-id="7ce45-157">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span>
<span data-ttu-id="7ce45-158">O exemplo abaixo mostra o que pode esperar:</span><span class="sxs-lookup"><span data-stu-id="7ce45-158">The example below shows what to expect:</span></span>


``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

<span data-ttu-id="7ce45-159">Módulo de desinstalação irá remover a versão mais recente de um módulo quando - RequiredVersion não é fornecido.</span><span class="sxs-lookup"><span data-stu-id="7ce45-159">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="7ce45-160">Se - RequiredVersion for especificado, não sendo uma pré-lançamento, - AllowPrerelease tem de ser adicionado ao comando.</span><span class="sxs-lookup"><span data-stu-id="7ce45-160">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module



C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```



## <a name="more-details"></a><span data-ttu-id="7ce45-161">obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="7ce45-161">More details</span></span>
### <a name="prerelease-script-versionsscriptprereleasescriptmd"></a>[<span data-ttu-id="7ce45-162">Versões de pré-lançamento do Script</span><span class="sxs-lookup"><span data-stu-id="7ce45-162">Prerelease Script Versions</span></span>](../script/PrereleaseScript.md)
### <a name="find-modulepsgetfind-modulemd"></a>[<span data-ttu-id="7ce45-163">Find-Module</span><span class="sxs-lookup"><span data-stu-id="7ce45-163">Find-Module</span></span>](./psget_find-module.md)
### <a name="install-modulepsgetinstall-modulemd"></a>[<span data-ttu-id="7ce45-164">Install-Module</span><span class="sxs-lookup"><span data-stu-id="7ce45-164">Install-Module</span></span>](./psget_install-module.md)
### <a name="save-modulepsgetsave-modulemd"></a>[<span data-ttu-id="7ce45-165">Save-Module</span><span class="sxs-lookup"><span data-stu-id="7ce45-165">Save-Module</span></span>](./psget_save-module.md)
### <a name="update-modulepsgetupdate-modulemd"></a>[<span data-ttu-id="7ce45-166">Update-Module</span><span class="sxs-lookup"><span data-stu-id="7ce45-166">Update-Module</span></span>](./psget_update-module.md)
### <a name="get-installedmodulepsgetget-installedmodulemd"></a>[<span data-ttu-id="7ce45-167">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="7ce45-167">Get-InstalledModule</span></span>](./psget_get-installedmodule.md)
### <a name="uninstall-modulepsgetuninstall-modulemd"></a>[<span data-ttu-id="7ce45-168">UnInstall-Module</span><span class="sxs-lookup"><span data-stu-id="7ce45-168">UnInstall-Module</span></span>](./psget_uninstall-module.md)