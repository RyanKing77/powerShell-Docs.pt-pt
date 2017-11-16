---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Fornecedor de NuGet bootstrapping e EXE
ms.openlocfilehash: 0036972eb9a0c20469da1aadafe223e6ec80f16a
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2017
---
# <a name="bootstrap-both-nuget-provider-and-nugetexe-or-bootstrap-only-nuget-provider"></a><span data-ttu-id="5081d-103">Arranque de fornecedor NuGet e NuGet.exe ou arranque apenas NuGet fornecedor</span><span class="sxs-lookup"><span data-stu-id="5081d-103">Bootstrap both NuGet provider and NuGet.exe or bootstrap only NuGet provider</span></span>

<span data-ttu-id="5081d-104">NuGet.exe não está incluído no fornecedor mais recente do NuGet.</span><span class="sxs-lookup"><span data-stu-id="5081d-104">NuGet.exe is not included in the latest NuGet provider.</span></span>
<span data-ttu-id="5081d-105">Para publicar operações de um módulo ou script, PowerShellGet requer o binário NuGet.exe executável.</span><span class="sxs-lookup"><span data-stu-id="5081d-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span>
<span data-ttu-id="5081d-106">Apenas é necessário para todas as outras operações o fornecedor do NuGet, incluindo *localizar*, *instalar*, *guardar*, e *desinstalar*.</span><span class="sxs-lookup"><span data-stu-id="5081d-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="5081d-107">PowerShellGet inclui lógica para lidar com qualquer um combinado o arranque de configuração do fornecedor do NuGet e NuGet.exe ou o arranque de configuração de apenas o fornecedor do NuGet.</span><span class="sxs-lookup"><span data-stu-id="5081d-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span>
<span data-ttu-id="5081d-108">Em ambos os casos, deve ocorrer apenas uma única mensagem de pedido.</span><span class="sxs-lookup"><span data-stu-id="5081d-108">In either case, only a single prompt message should occur.</span></span>
<span data-ttu-id="5081d-109">Se a máquina não estiver ligada à Internet, o utilizador ou um administrador tem de copiar uma instância do fornecedor de NuGet e/ou o ficheiro NuGet.exe fidedigna para a máquina desligada.</span><span class="sxs-lookup"><span data-stu-id="5081d-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

><span data-ttu-id="5081d-110">**Tenha em atenção**: a partir da versão 6, o fornecedor do NuGet está incluído na instalação do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5081d-110">**Note**: Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span> [<span data-ttu-id="5081d-111">http://github.com/PowerShell/PowerShell</span><span class="sxs-lookup"><span data-stu-id="5081d-111">http://github.com/powershell/powershell</span></span>](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="5081d-112">Resolver erros quando o fornecedor do NuGet não foi instalado num computador onde é Internet ligado</span><span class="sxs-lookup"><span data-stu-id="5081d-112">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

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
## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="5081d-113">Resolver erros quando o fornecedor do NuGet está disponível e NuGet.exe não está disponível durante a operação de publicar num computador onde é Internet ligado</span><span class="sxs-lookup"><span data-stu-id="5081d-113">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="5081d-114">Resolver erros quando o fornecedor do NuGet e NuGet.exe não estão disponíveis durante a operação de publicar num computador onde é Internet ligado</span><span class="sxs-lookup"><span data-stu-id="5081d-114">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

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

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="5081d-115">Bootstrapping manualmente o fornecedor do NuGet num computador que não está ligado à Internet</span><span class="sxs-lookup"><span data-stu-id="5081d-115">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="5081d-116">Os processos demonstrados acima partem do princípio da máquina está ligada à Internet e pode transferir os ficheiros a partir de uma localização pública.</span><span class="sxs-lookup"><span data-stu-id="5081d-116">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span>
<span data-ttu-id="5081d-117">Se não for possível, é a única opção para arranque de uma máquina através de processos indicados acima e copiar manualmente o fornecedor para o nó isolado através de um processo offline fidedigno.</span><span class="sxs-lookup"><span data-stu-id="5081d-117">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span>
<span data-ttu-id="5081d-118">O caso de utilização mais comum para este cenário é quando uma galeria privada está disponível para suportar um ambiente isolado.</span><span class="sxs-lookup"><span data-stu-id="5081d-118">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="5081d-119">Depois de seguir o processo acima para arranque de um computador ligado à Internet, irá encontrar os ficheiros de fornecedor na localização:</span><span class="sxs-lookup"><span data-stu-id="5081d-119">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>
```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

<span data-ttu-id="5081d-120">A estrutura de pasta/ficheiro do fornecedor do NuGet será (possivelmente com um número de versão diferentes):</span><span class="sxs-lookup"><span data-stu-id="5081d-120">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

<span data-ttu-id="5081d-121">NuGet</span><span class="sxs-lookup"><span data-stu-id="5081d-121">NuGet</span></span><br>
<span data-ttu-id="5081d-122">--2.8.5.208</span><span class="sxs-lookup"><span data-stu-id="5081d-122">--2.8.5.208</span></span><br>
<span data-ttu-id="5081d-123">---Microsoft.PackageManagement.NuGetProvider.dll</span><span class="sxs-lookup"><span data-stu-id="5081d-123">----Microsoft.PackageManagement.NuGetProvider.dll</span></span>

<span data-ttu-id="5081d-124">Copie estas pastas e ficheiros através de um processo fidedigno para as máquinas offline.</span><span class="sxs-lookup"><span data-stu-id="5081d-124">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="5081d-125">Manualmente bootstrapping NuGet.exe para suportar a publicar operações num computador que não está ligado à Internet</span><span class="sxs-lookup"><span data-stu-id="5081d-125">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="5081d-126">Para além do processo de arranque manualmente o fornecedor do NuGet, se a máquina será utilizada para publicar módulos ou scripts para uma galeria privada utilizando o *publicar-Module* ou *publicar Script* cmdlets, ficheiro executável binário NuGet.exe será necessário.</span><span class="sxs-lookup"><span data-stu-id="5081d-126">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the *Publish-Module* or *Publish-Script* cmdlets, the NuGet.exe binary executable file will be required.</span></span>
<span data-ttu-id="5081d-127">O caso de utilização mais comum para este cenário é quando uma galeria privada está disponível para suportar um ambiente isolado.</span><span class="sxs-lookup"><span data-stu-id="5081d-127">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>
<span data-ttu-id="5081d-128">Existem duas opções para obter o ficheiro NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="5081d-128">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="5081d-129">É uma opção de arranque de uma máquina que se ligadas à Internet e copie os ficheiros para as máquinas offline através de um processo fidedigno.</span><span class="sxs-lookup"><span data-stu-id="5081d-129">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span>
<span data-ttu-id="5081d-130">Após bootstrapping a máquina ligada à Internet, o binário NuGet.exe estarão localizado em uma das duas pastas:</span><span class="sxs-lookup"><span data-stu-id="5081d-130">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="5081d-131">Se o *publicar-Module* ou *publicar Script* cmdlets foram executados com permissões elevadas (como um administrador):</span><span class="sxs-lookup"><span data-stu-id="5081d-131">If the *Publish-Module* or *Publish-Script* cmdlets were executed with elevated permissions (As an Administrator):</span></span>
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="5081d-132">Se os cmdlets foram executados como um utilizador sem permissões elevadas:</span><span class="sxs-lookup"><span data-stu-id="5081d-132">If the cmdlets were executed as a user without elevated permissions:</span></span>
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="5081d-133">É uma segunda opção para transferir NuGet.exe do Web site NuGet.Org: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span><span class="sxs-lookup"><span data-stu-id="5081d-133">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span></span><br>
<span data-ttu-id="5081d-134">Quando selecionar uma versão de NugGet para máquinas de produção, certifique-se de que é posterior à 2.8.5.208 e identificar a versão que tenha sido com a etiqueta "recomendados".</span><span class="sxs-lookup"><span data-stu-id="5081d-134">When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span>
<span data-ttu-id="5081d-135">Lembre-se desbloquear o ficheiro se este foi transferido utilizando um browser.</span><span class="sxs-lookup"><span data-stu-id="5081d-135">Remember to unblock the file if it was downloaded using a browser.</span></span>
<span data-ttu-id="5081d-136">Isto pode ser efetuado utilizando o *desbloqueio ficheiro* cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5081d-136">This can be performed by using the *Unblock-File* cmdlet.</span></span>

<span data-ttu-id="5081d-137">Em ambos os casos, o ficheiro NuGet.exe pode ser copiado para qualquer localização em *$env: caminho*, mas as localizações padrão são:</span><span class="sxs-lookup"><span data-stu-id="5081d-137">In either case, the NuGet.exe file can be copied to any location in *$env:path*, but the standard locations are:</span></span>

<span data-ttu-id="5081d-138">Para disponibilizar o executável para que todos os utilizadores possam utilizar *publicar-Module* e *publicar Script* cmdlets:</span><span class="sxs-lookup"><span data-stu-id="5081d-138">To make the executable available so that all users can use *Publish-Module* and *Publish-Script* cmdlets:</span></span>
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="5081d-139">Para disponibilizar o ficheiro executável a apenas um utilizador específico, copiar para a localização dentro do perfil desse utilizador apenas:</span><span class="sxs-lookup"><span data-stu-id="5081d-139">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

