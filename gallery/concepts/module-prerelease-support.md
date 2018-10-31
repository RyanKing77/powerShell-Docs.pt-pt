---
ms.date: 09/26/2017
contributor: keithb
keywords: cmdlet do powershell do galeria, psget
title: Versões de pré-lançamento do módulo
ms.openlocfilehash: f58b5adfeba7ed06d231c76accbd52508c7d67d6
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002774"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="344eb-103">Versões de pré-lançamento do módulo</span><span class="sxs-lookup"><span data-stu-id="344eb-103">Prerelease Module Versions</span></span>

<span data-ttu-id="344eb-104">A partir da versão 1.6.0, PowerShellGet e da galeria do PowerShell fornecem suporte para versões superiores a 1.0.0 como uma versão de pré-lançamento de marcação.</span><span class="sxs-lookup"><span data-stu-id="344eb-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="344eb-105">Antes desta funcionalidade, os pacotes de pré-lançamento eram limitado a ter um início de versão com 0.</span><span class="sxs-lookup"><span data-stu-id="344eb-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="344eb-106">O objetivo desses recursos é oferecem maior suporte para [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) Convenção de controle de versão sem perder com versões anteriores a compatibilidade com o PowerShell versões existentes e 3 ou acima versões do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="344eb-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="344eb-107">Este tópico concentra-se nos recursos específicos de módulo.</span><span class="sxs-lookup"><span data-stu-id="344eb-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="344eb-108">As funcionalidades equivalentes para os scripts estão na [versões de pré-lançamento de Scripts](script-prerelease-support.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="344eb-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="344eb-109">Utilizar estas funcionalidades, os publicadores podem identificar um módulo ou o script como versão 2.5.0-alpha e mais tarde lançar uma versão de prontos para produção 2.5.0 que substitui a versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="344eb-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="344eb-110">Num alto nível, as funcionalidades de pré-lançamento do módulo incluem:</span><span class="sxs-lookup"><span data-stu-id="344eb-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="344eb-111">Adicionar uma cadeia de caracteres de pré-lançamento para a secção de PSData do manifesto do módulo identifica o módulo como uma versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="344eb-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="344eb-112">Quando o módulo é publicado na galeria do PowerShell, estes dados são extraídos de manifesto e utilizados para identificar pacotes de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="344eb-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="344eb-113">Aquisição de pacotes de pré-lançamento exige a inclusão `-AllowPrerelease` sinalizador para os comandos do PowerShellGet `Find-Module`, `Install-Module`, `Update-Module`, e `Save-Module`.</span><span class="sxs-lookup"><span data-stu-id="344eb-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="344eb-114">Se o sinalizador não for especificado, os pacotes de pré-lançamento não será apresentado.</span><span class="sxs-lookup"><span data-stu-id="344eb-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="344eb-115">Versões do módulo exibidas pelo `Find-Module`, `Get-InstalledModule`e na galeria do PowerShell será apresentada como uma única cadeia de caracteres com a cadeia de pré-lançamento anexada, como no 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="344eb-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="344eb-116">Detalhes para as funcionalidades estão incluídas abaixo.</span><span class="sxs-lookup"><span data-stu-id="344eb-116">Details for the features are included below.</span></span>

<span data-ttu-id="344eb-117">Estas alterações não afetam o suporte da versão do módulo que está incorporado no PowerShell e são compatíveis com o PowerShell 3.0, 4.0 e 5.</span><span class="sxs-lookup"><span data-stu-id="344eb-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="344eb-118">Identificar uma versão do módulo como uma versão de pré-lançamento</span><span class="sxs-lookup"><span data-stu-id="344eb-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="344eb-119">Suporte do PowerShellGet para versões de pré-lançamento requer a utilização de dois campos no manifesto do módulo:</span><span class="sxs-lookup"><span data-stu-id="344eb-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="344eb-120">ModuleVersion incluído no manifesto do módulo tem de ser uma versão de 3 partes se é utilizada uma versão de pré-lançamento e deve estar em conformidade com o controle de versão do PowerShell existente.</span><span class="sxs-lookup"><span data-stu-id="344eb-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="344eb-121">O formato de versão seria A.B.C, onde A, B e C estão todos os números inteiros.</span><span class="sxs-lookup"><span data-stu-id="344eb-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="344eb-122">A cadeia de caracteres de pré-lançamento é especificada no manifesto do módulo, na secção PSData PrivateData.</span><span class="sxs-lookup"><span data-stu-id="344eb-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="344eb-123">Os requisitos detalhados sobre a cadeia de caracteres de pré-lançamento estão abaixo.</span><span class="sxs-lookup"><span data-stu-id="344eb-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="344eb-124">Uma seção de exemplo de um manifesto de módulo que define um módulo como uma versão de pré-lançamento seria semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="344eb-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

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

<span data-ttu-id="344eb-125">Os requisitos detalhados para a cadeia de pré-lançamento são:</span><span class="sxs-lookup"><span data-stu-id="344eb-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="344eb-126">Cadeia de caracteres de pré-lançamento só pode ser especificada quando o ModuleVersion é 3 segmentos para major.</span><span class="sxs-lookup"><span data-stu-id="344eb-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="344eb-127">Isso se alinha com SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="344eb-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="344eb-128">Um hífen é o delimitador entre o número de compilação e a cadeia de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="344eb-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="344eb-129">Um hífen pode ser incluído na cadeia de pré-lançamento, como o primeiro caráter, apenas.</span><span class="sxs-lookup"><span data-stu-id="344eb-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="344eb-130">A cadeia de caracteres de pré-lançamento pode conter apenas carateres de alfanuméricos ASCII [0-9A-Za - z-].</span><span class="sxs-lookup"><span data-stu-id="344eb-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="344eb-131">É melhor prática para iniciar a versão de pré-lançamento de cadeias de caracteres com um caractere alfa, como será mais fácil de identificar que esta é uma versão de pré-lançamento quando efetua a análise de uma lista de pacotes.</span><span class="sxs-lookup"><span data-stu-id="344eb-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="344eb-132">Apenas SemVer v1.0.0 pré-lançamento cadeias de caracteres são suportadas neste momento.</span><span class="sxs-lookup"><span data-stu-id="344eb-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="344eb-133">Cadeia de caracteres de pré-lançamento **não podem** conter qualquer um dos ponto ou + [. +], que é permitido em SemVer 2.0.</span><span class="sxs-lookup"><span data-stu-id="344eb-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="344eb-134">Exemplos de cadeia de caracteres de pré-lançamento suportado são:-alfa, - alpha1,-BETA, - update20171020</span><span class="sxs-lookup"><span data-stu-id="344eb-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="344eb-135">Impacto de controlo de versões de pré-lançamento nas pastas de instalação e a ordem de ordenação</span><span class="sxs-lookup"><span data-stu-id="344eb-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="344eb-136">Ordem de classificação é alterado quando utilizar uma versão de pré-lançamento, que é importante durante a publicação na galeria do PowerShell, e ao instalar os módulos com comandos do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="344eb-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="344eb-137">Se a cadeia de caracteres de pré-lançamento é especificada para dois módulos, a ordem de classificação baseia-se na parte de cadeia de caracteres a seguir o hífen.</span><span class="sxs-lookup"><span data-stu-id="344eb-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="344eb-138">Então, versão 2.5.0-alpha é menor que 2.5.0-beta, que é menor que 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="344eb-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="344eb-139">Se dois módulos têm o mesmo ModuleVersion e apenas um tem uma cadeia de caracteres de pré-lançamento, o módulo sem a cadeia de caracteres de pré-lançamento é considerado como a versão de prontos para produção e será classificado como uma versão superior à versão de pré-lançamento (que inclui a versão de pré-lançamento cadeia de caracteres).</span><span class="sxs-lookup"><span data-stu-id="344eb-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="344eb-140">Por exemplo, ao comparar versões 2.5.0 e 2.5.0-beta, o 2.5.0 versão será considerada o maior dos dois.</span><span class="sxs-lookup"><span data-stu-id="344eb-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="344eb-141">Durante a publicação na galeria do PowerShell, por predefinição a versão do módulo a ser publicado tem de ter uma versão maior do que qualquer versão publicada anteriormente que está na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="344eb-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="344eb-142">Encontrar e adquirir os pacotes de pré-lançamento utilizar comandos do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="344eb-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="344eb-143">Lidar com pacotes de pré-lançamento com atualização Find-Module PowerShellGet, Install-Module-Module, e os comandos de Save-Module é necessário adicionar o sinalizador - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="344eb-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="344eb-144">Se não for especificado - AllowPrerelease, pacotes de pré-lançamento serão incluído, se estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="344eb-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="344eb-145">Se não for especificado o sinalizador - AllowPrerelease, pacotes de pré-lançamento não será apresentado.</span><span class="sxs-lookup"><span data-stu-id="344eb-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="344eb-146">As únicas exceções a esta nos comandos de módulo PowerShellGet são Get-InstalledModule e alguns casos com o módulo de desinstalação.</span><span class="sxs-lookup"><span data-stu-id="344eb-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="344eb-147">Get-InstalledModule sempre mostrará automaticamente as informações de pré-lançamento na cadeia de versão para módulos.</span><span class="sxs-lookup"><span data-stu-id="344eb-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="344eb-148">Desinstalar-Module por predefinição desinstalará a versão mais recente de um módulo, se __nenhuma versão__ está especificado.</span><span class="sxs-lookup"><span data-stu-id="344eb-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="344eb-149">Esse comportamento não mudou.</span><span class="sxs-lookup"><span data-stu-id="344eb-149">That behavior has not changed.</span></span> <span data-ttu-id="344eb-150">No entanto, se não for especificada uma versão de pré-lançamento usando - RequiredVersion, - AllowPrerelease será necessária.</span><span class="sxs-lookup"><span data-stu-id="344eb-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="344eb-151">Exemplos</span><span class="sxs-lookup"><span data-stu-id="344eb-151">Examples</span></span>

<span data-ttu-id="344eb-152">Assumir que a galeria do PowerShell tem versões do módulo TestPackage 1.8.0 e 1.9.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="344eb-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="344eb-153">Se `-AllowPrerelease` não é especificado, apenas a versão 1.8.0 será retornado.</span><span class="sxs-lookup"><span data-stu-id="344eb-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="344eb-154">Para instalar uma versão de pré-lançamento, sempre Especifica - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="344eb-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="344eb-155">Especificar uma cadeia de versão de pré-lançamento não é suficiente.</span><span class="sxs-lookup"><span data-stu-id="344eb-155">Specifying a prerelease version string is not sufficient.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

<span data-ttu-id="344eb-156">O comando anterior falhou porque - AllowPrerelease não foi especificado.</span><span class="sxs-lookup"><span data-stu-id="344eb-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="344eb-157">Adicionar `-AllowPrerelease` irá resultar no sucesso.</span><span class="sxs-lookup"><span data-stu-id="344eb-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="344eb-158">Não é suportada a instalação lado a lado das versões de um módulo que diferem apenas devido a versão de pré-lançamento especificado.</span><span class="sxs-lookup"><span data-stu-id="344eb-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="344eb-159">Ao instalar um módulo com o PowerShellGet, versões diferentes do mesmo módulo são instalada lado a lado através da criação de um nome de pasta com o ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="344eb-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="344eb-160">ModuleVersion, sem a cadeia de pré-lançamento, é utilizada para o nome da pasta.</span><span class="sxs-lookup"><span data-stu-id="344eb-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="344eb-161">Se um usuário instala MyModule versão 2.5.0-alpha, esta será instalada para o `MyModule\2.5.0` pasta.</span><span class="sxs-lookup"><span data-stu-id="344eb-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="344eb-162">Se o utilizador, em seguida, instala 2.5.0-beta, poderá ser a versão de 2.5.0-beta **substituir** o conteúdo da pasta `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="344eb-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="344eb-163">Uma vantagem dessa abordagem é que não é necessário desinstalar a versão de pré-lançamento depois de instalar a versão de prontos para produção.</span><span class="sxs-lookup"><span data-stu-id="344eb-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="344eb-164">O exemplo abaixo mostra o que esperar:</span><span class="sxs-lookup"><span data-stu-id="344eb-164">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

<span data-ttu-id="344eb-165">Desinstalar-Module irá remover a versão mais recente de um módulo quando - RequiredVersion não é fornecido.</span><span class="sxs-lookup"><span data-stu-id="344eb-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="344eb-166">Se - RequiredVersion for especificada e é uma versão de pré-lançamento, - AllowPrerelease tem de ser adicionado ao comando.</span><span class="sxs-lookup"><span data-stu-id="344eb-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

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

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a><span data-ttu-id="344eb-167">Obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="344eb-167">More details</span></span>

- [<span data-ttu-id="344eb-168">Versões de pré-lançamento do Script</span><span class="sxs-lookup"><span data-stu-id="344eb-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="344eb-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="344eb-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="344eb-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="344eb-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="344eb-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="344eb-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="344eb-172">Update-Module</span><span class="sxs-lookup"><span data-stu-id="344eb-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="344eb-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="344eb-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="344eb-174">Desinstalar-Module</span><span class="sxs-lookup"><span data-stu-id="344eb-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
