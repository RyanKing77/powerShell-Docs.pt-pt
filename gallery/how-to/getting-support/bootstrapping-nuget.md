---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Efetuar o arranque do NuGet
ms.openlocfilehash: 6d8f106bc3b8741203e87e4c097948a843f06d6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084390"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="b0264-103">Inicializar o fornecedor NuGet e NuGet.exe</span><span class="sxs-lookup"><span data-stu-id="b0264-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="b0264-104">NuGet.exe não está incluído no fornecedor mais recente do NuGet.</span><span class="sxs-lookup"><span data-stu-id="b0264-104">NuGet.exe is not included in the latest NuGet provider.</span></span> <span data-ttu-id="b0264-105">Para operações de um módulo ou o script de publicação, PowerShellGet requer o NuGet.exe executável binário.</span><span class="sxs-lookup"><span data-stu-id="b0264-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span> <span data-ttu-id="b0264-106">Apenas o fornecedor de NuGet é necessário para todas as outras operações, incluindo *encontrar*, *instalar*, *guardar*, e *desinstalar*.</span><span class="sxs-lookup"><span data-stu-id="b0264-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="b0264-107">O PowerShellGet inclui lógica para lidar com qualquer um combinado fazer a inicialização do fornecedor NuGet e NuGet.exe ou o arranque de apenas o fornecedor do NuGet.</span><span class="sxs-lookup"><span data-stu-id="b0264-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span> <span data-ttu-id="b0264-108">Em ambos os casos, deve ocorrer apenas uma única mensagem de linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="b0264-108">In either case, only a single prompt message should occur.</span></span> <span data-ttu-id="b0264-109">Se a máquina não estiver ligada à Internet, o utilizador ou um administrador tem de copiar uma instância fidedigna do fornecedor NuGet e/ou o ficheiro de NuGet.exe para a máquina desligada.</span><span class="sxs-lookup"><span data-stu-id="b0264-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="b0264-110">A partir da versão 6, o fornecedor de NuGet está incluído na instalação do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0264-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span>

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="b0264-111">Resolver o erro quando o fornecedor de NuGet não foi instalado num computador que é a Internet ligado</span><span class="sxs-lookup"><span data-stu-id="b0264-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="b0264-112">Resolver o erro quando o fornecedor de NuGet estiver disponível e NuGet.exe não está disponível durante a operação de publicação num computador que está a Internet ligado</span><span class="sxs-lookup"><span data-stu-id="b0264-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="b0264-113">Resolver o erro quando o fornecedor NuGet e NuGet.exe não estão disponíveis durante a operação de publicação num computador que está a Internet ligado</span><span class="sxs-lookup"><span data-stu-id="b0264-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="b0264-114">O fornecedor do NuGet numa máquina que não está ligado à Internet de inicialização manualmente</span><span class="sxs-lookup"><span data-stu-id="b0264-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="b0264-115">Os processos demonstrados acima partem do princípio da máquina está conectada à Internet e pode transferir os ficheiros de um local público.</span><span class="sxs-lookup"><span data-stu-id="b0264-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span> <span data-ttu-id="b0264-116">Se não for possível, a única opção é inicializar uma máquina com os processos indicados acima e copie manualmente o fornecedor para o nó isolado através de um processo offline de confiança.</span><span class="sxs-lookup"><span data-stu-id="b0264-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span> <span data-ttu-id="b0264-117">O caso de uso mais comum para este cenário é quando uma galeria privada está disponível para suportar um ambiente isolado.</span><span class="sxs-lookup"><span data-stu-id="b0264-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="b0264-118">Depois de seguir o processo acima para inicializar um computador de ligado à Internet, encontrará os ficheiros de fornecedor na localização:</span><span class="sxs-lookup"><span data-stu-id="b0264-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

`C:\Program Files\PackageManagement\ProviderAssemblies\`

<span data-ttu-id="b0264-119">A estrutura de pasta/ficheiro do fornecedor NuGet será (possivelmente com um número de versão diferentes):</span><span class="sxs-lookup"><span data-stu-id="b0264-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="b0264-120">Copie estas pastas e ficheiros através de um processo fidedigno para as máquinas offline.</span><span class="sxs-lookup"><span data-stu-id="b0264-120">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="b0264-121">Manualmente de inicialização NuGet.exe para suportar operações num computador que não está ligado à Internet de publicação</span><span class="sxs-lookup"><span data-stu-id="b0264-121">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="b0264-122">Além do processo para iniciar manualmente o fornecedor do NuGet, se a máquina será utilizada para publicar módulos ou scripts numa galeria privada utilizando o `Publish-Module` ou `Publish-Script` cmdlets, o arquivo executável binário do NuGet.exe será necessário.</span><span class="sxs-lookup"><span data-stu-id="b0264-122">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="b0264-123">O caso de uso mais comum para este cenário é quando uma galeria privada está disponível para suportar um ambiente isolado.</span><span class="sxs-lookup"><span data-stu-id="b0264-123">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span> <span data-ttu-id="b0264-124">Existem duas opções para obter o ficheiro de NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="b0264-124">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="b0264-125">É uma opção inicializar uma máquina que está ligados à Internet e copie os ficheiros para as máquinas offline usando um processo fidedigno.</span><span class="sxs-lookup"><span data-stu-id="b0264-125">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span> <span data-ttu-id="b0264-126">Depois de efetuar o arranque do computador ligado à Internet, o binário NuGet.exe estarão localizado em uma das duas pastas:</span><span class="sxs-lookup"><span data-stu-id="b0264-126">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="b0264-127">Se o `Publish-Module` ou `Publish-Script` cmdlets foram executados com permissões elevadas (como administrador):</span><span class="sxs-lookup"><span data-stu-id="b0264-127">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="b0264-128">Se os cmdlets foram executados como um utilizador sem permissões elevadas:</span><span class="sxs-lookup"><span data-stu-id="b0264-128">If the cmdlets were executed as a user without elevated permissions:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="b0264-129">Uma segunda opção consiste em transferir NuGet.exe a partir do site da NuGet.Org: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) Ao selecionar uma versão de Preciosidade para máquinas de produção, certifique-se de que é posterior à 2.8.5.208 e identificar a versão que foi intitulada "recomendados".</span><span class="sxs-lookup"><span data-stu-id="b0264-129">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span> <span data-ttu-id="b0264-130">Lembre-se desbloquear o ficheiro se este foi transferido através de um browser.</span><span class="sxs-lookup"><span data-stu-id="b0264-130">Remember to unblock the file if it was downloaded using a browser.</span></span> <span data-ttu-id="b0264-131">Isto pode ser efetuado utilizando o `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b0264-131">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="b0264-132">Em ambos os casos, o ficheiro de NuGet.exe pode ser copiado para qualquer localização no `$env:path`, mas os locais padrão são:</span><span class="sxs-lookup"><span data-stu-id="b0264-132">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

<span data-ttu-id="b0264-133">Para disponibilizar o executável para que todos os utilizadores possam utilizar `Publish-Module` e `Publish-Script` cmdlets:</span><span class="sxs-lookup"><span data-stu-id="b0264-133">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="b0264-134">Para disponibilizar o executável para apenas um utilizador específico, copiar para a localização dentro de apenas do perfil do usuário:</span><span class="sxs-lookup"><span data-stu-id="b0264-134">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```
