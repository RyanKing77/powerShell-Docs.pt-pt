---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2f05fe96ec792a31fabf3aff0f9e18b40178316c
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893193"
---
# <a name="packagemanagement-cmdlets"></a><span data-ttu-id="dc270-102">Cmdlets PackageManagement</span><span class="sxs-lookup"><span data-stu-id="dc270-102">PackageManagement Cmdlets</span></span>

<span data-ttu-id="dc270-103">Este é o núcleo do PackageManagement para suportar a deteção de software, instalação e inventário (SDII).</span><span class="sxs-lookup"><span data-stu-id="dc270-103">This is the core of PackageManagement to support software discovery, installation, and inventory (SDII).</span></span> <span data-ttu-id="dc270-104">Experimente os cmdlets para essas operações:</span><span class="sxs-lookup"><span data-stu-id="dc270-104">Try out the cmdlets for these operations:</span></span>

- `Find-Package`
- `Find-PackageProvider`
- `Get-Package`
- `Get-PackageProvider`
- `Get-PackageSource`
- `Import-PackageProvider`
- `Install-Package`
- `Install-PackageProvider`
- `Register-PackageSource`
- `Save-Package`
- `Set-PackageSource`
- `Uninstall-Package`
- `Unregister-PackageSource`

<span data-ttu-id="dc270-105">Como PackageManagement é um módulo do PowerShell, pode fazer o seguinte para atualizar PackageManagement em si:</span><span class="sxs-lookup"><span data-stu-id="dc270-105">As PackageManagement is a PowerShell module, you can do the following to update PackageManagement itself:</span></span>

```powershell
Install-Module PackageManagement –Force
```

<span data-ttu-id="dc270-106">Neste caso, terá de reintroduzir a sessão do PowerShell para mudar para a nova versão do PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="dc270-106">In this case, you will have to re-enter PowerShell session to switch to the new version of PackageManagement.</span></span>

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[<span data-ttu-id="dc270-107">Cmdlet de Find-Package</span><span class="sxs-lookup"><span data-stu-id="dc270-107">Find-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Find-Package)

<span data-ttu-id="dc270-108">Este cmdlet permite a deteção de pacotes de software em origens de pacotes disponíveis usando carregado fornecedores de pacote.</span><span class="sxs-lookup"><span data-stu-id="dc270-108">This cmdlet allows discovery of software packages in available package sources using loaded package providers.</span></span>

```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -ProviderName PowerShellGet -Source as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[<span data-ttu-id="dc270-109">Find-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="dc270-109">Find-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Find-PackageProvider)

<span data-ttu-id="dc270-110">O `Find-PackageProvider` cmdlet localiza a correspondência PackageManagement fornecedores que estão disponíveis no origens do pacote registrado com o PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="dc270-110">The `Find-PackageProvider` cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span> <span data-ttu-id="dc270-111">Estes são os fornecedores de pacote disponíveis para instalação com o `Install-PackageProvider` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dc270-111">These are package providers available for installation with the `Install-PackageProvider` cmdlet.</span></span> <span data-ttu-id="dc270-112">Por predefinição, isto inclui módulos disponíveis na galeria do PowerShell com o "PackageManagement" e "Fornecedor" etiquetas.</span><span class="sxs-lookup"><span data-stu-id="dc270-112">By default, this includes modules available in the PowerShell Gallery with the 'PackageManagement' and 'Provider' Tags.</span></span>

<span data-ttu-id="dc270-113">`Find-PackageProvider` também encontra fornecedores PackageManagement correspondentes que estão disponíveis no armazenamento de Blobs do azure PackageManagement onde podemos usar o provedor de boostrapper PackageManagement para procurar e instalá-los.</span><span class="sxs-lookup"><span data-stu-id="dc270-113">`Find-PackageProvider` also finds matching PackageManagement providers that are available in the PackageManagement azure blob store where we use the PackageManagement boostrapper provider for finding and installing them.</span></span>

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[<span data-ttu-id="dc270-114">Cmdlet Get-Package</span><span class="sxs-lookup"><span data-stu-id="dc270-114">Get-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Get-Package)

<span data-ttu-id="dc270-115">Este cmdlet devolve uma lista de todos os pacotes de software que tenham sido instaladas através do PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="dc270-115">This cmdlet returns a list of all software packages that have been installed using PackageManagement.</span></span>

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[<span data-ttu-id="dc270-116">Cmdlet Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="dc270-116">Get-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Get-PackageProvider)

<span data-ttu-id="dc270-117">Fornecedores de pacote que são carregados e pronto a ser utilizado no computador local podem ser inventariados com o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dc270-117">Package providers that are loaded and ready to be used on the local machine can be inventoried by using the cmdlet.</span></span>

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[<span data-ttu-id="dc270-118">Cmdlet Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="dc270-118">Get-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Get-PackageSource)

<span data-ttu-id="dc270-119">Este cmdlet obtém uma lista de origens de pacotes que estão registados para um fornecedor do pacote.</span><span class="sxs-lookup"><span data-stu-id="dc270-119">This cmdlet gets a list of package sources that are registered for a package provider.</span></span>

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[<span data-ttu-id="dc270-120">Cmdlet de importação PackageProvider</span><span class="sxs-lookup"><span data-stu-id="dc270-120">Import-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Import-PackageProvider)

<span data-ttu-id="dc270-121">Este cmdlet adiciona os fornecedores de pacote de gestão de pacotes para a sessão atual.</span><span class="sxs-lookup"><span data-stu-id="dc270-121">This cmdlet adds Package Management package providers to the current session.</span></span>

```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force
```

## <a name="-install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[<span data-ttu-id="dc270-122"> Cmdlet Install-Package</span><span class="sxs-lookup"><span data-stu-id="dc270-122"> Install-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Install-Package)

<span data-ttu-id="dc270-123">Este cmdlet permite a instalação de pacotes de software em origens de pacotes disponíveis usando carregado fornecedores de pacote.</span><span class="sxs-lookup"><span data-stu-id="dc270-123">This cmdlet allows installation of software packages in available package sources using loaded package providers.</span></span>

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[<span data-ttu-id="dc270-124">Cmdlet de instalação PackageProvider</span><span class="sxs-lookup"><span data-stu-id="dc270-124">Install-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Install-PackageProvider)

<span data-ttu-id="dc270-125">Este cmdlet instala um ou mais fornecedores de pacote de gestão de pacotes.</span><span class="sxs-lookup"><span data-stu-id="dc270-125">This cmdlet installs one or more Package Management package providers.</span></span>

```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[<span data-ttu-id="dc270-126">Cmdlet register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="dc270-126">Register-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Register-PackageSource)

<span data-ttu-id="dc270-127">Este cmdlet adiciona uma origem de pacote de um fornecedor do pacote especificado.</span><span class="sxs-lookup"><span data-stu-id="dc270-127">This cmdlet adds a package source for a specified package provider.</span></span>
<span data-ttu-id="dc270-128">Cada fornecedor de PackageManagement pode ter uma ou várias origens de software ou repositórios.</span><span class="sxs-lookup"><span data-stu-id="dc270-128">Each PackageManagement provider may have one or multiple software sources, or repositories.</span></span> <span data-ttu-id="dc270-129">PackageManagement fornece cmdlets do PowerShell para adicionar/remover/consulta a origem.</span><span class="sxs-lookup"><span data-stu-id="dc270-129">PackageManagement provides PowerShell cmdlets to add/remove/query the source.</span></span> <span data-ttu-id="dc270-130">Por exemplo, pode registar uma origem de pacote para o fornecedor do NuGet:</span><span class="sxs-lookup"><span data-stu-id="dc270-130">For example, you can register a package source for the NuGet provider:</span></span>

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[<span data-ttu-id="dc270-131">Cmdlet Save-Package</span><span class="sxs-lookup"><span data-stu-id="dc270-131">Save-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Save-Package)

<span data-ttu-id="dc270-132">Este cmdlet guarda pacotes no computador local, sem instalá-los.</span><span class="sxs-lookup"><span data-stu-id="dc270-132">This cmdlet saves packages to the local computer without installing them.</span></span>

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[<span data-ttu-id="dc270-133">Cmdlet Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="dc270-133">Set-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Set-PackageSource)

<span data-ttu-id="dc270-134">Este cmdlet altera as informações sobre uma origem de pacote existente.</span><span class="sxs-lookup"><span data-stu-id="dc270-134">This cmdlet changes information about an existing package source.</span></span>

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[<span data-ttu-id="dc270-135">Cmdlet Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="dc270-135">Uninstall-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Uninstall-Package)

<span data-ttu-id="dc270-136">Este cmdlet desinstala os pacotes instalados no computador local.</span><span class="sxs-lookup"><span data-stu-id="dc270-136">This cmdlet uninstalls packages installed on the local computer.</span></span>

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[<span data-ttu-id="dc270-137">Cmdlet PackageSource anular o registo</span><span class="sxs-lookup"><span data-stu-id="dc270-137">Unregister-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```