---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f545461fd325049d0de4c651d7aa7d50d475eaca
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="packagemanagement-cmdlets"></a><span data-ttu-id="fe4b7-102">Cmdlets PackageManagement</span><span class="sxs-lookup"><span data-stu-id="fe4b7-102">PackageManagement Cmdlets</span></span>
<span data-ttu-id="fe4b7-103">Este é o núcleo dos PackageManagement para suportar a deteção de software, instalação e inventário (SDII).</span><span class="sxs-lookup"><span data-stu-id="fe4b7-103">This is the core of PackageManagement to support software discovery, installation, and inventory (SDII).</span></span> <span data-ttu-id="fe4b7-104">Experimente os cmdlets para estas operações:</span><span class="sxs-lookup"><span data-stu-id="fe4b7-104">Try out the cmdlets for these operations:</span></span>
-   <span data-ttu-id="fe4b7-105">Find-Package</span><span class="sxs-lookup"><span data-stu-id="fe4b7-105">Find-Package</span></span>
-   <span data-ttu-id="fe4b7-106">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fe4b7-106">Find-PackageProvider</span></span>
-   <span data-ttu-id="fe4b7-107">Get-Package</span><span class="sxs-lookup"><span data-stu-id="fe4b7-107">Get-Package</span></span>
-   <span data-ttu-id="fe4b7-108">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fe4b7-108">Get-PackageProvider</span></span>
-   <span data-ttu-id="fe4b7-109">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="fe4b7-109">Get-PackageSource</span></span>
-   <span data-ttu-id="fe4b7-110">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fe4b7-110">Import-PackageProvider</span></span>
-   <span data-ttu-id="fe4b7-111">Pacote de instalação</span><span class="sxs-lookup"><span data-stu-id="fe4b7-111">Install-Package</span></span>
-   <span data-ttu-id="fe4b7-112">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fe4b7-112">Install-PackageProvider</span></span>
-   <span data-ttu-id="fe4b7-113">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="fe4b7-113">Register-PackageSource</span></span>
-   <span data-ttu-id="fe4b7-114">Guardar pacote</span><span class="sxs-lookup"><span data-stu-id="fe4b7-114">Save-Package</span></span>
-   <span data-ttu-id="fe4b7-115">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="fe4b7-115">Set-PackageSource</span></span>
-   <span data-ttu-id="fe4b7-116">Pacote de desinstalação</span><span class="sxs-lookup"><span data-stu-id="fe4b7-116">Uninstall-Package</span></span>
-   <span data-ttu-id="fe4b7-117">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="fe4b7-117">Unregister-PackageSource</span></span>

<span data-ttu-id="fe4b7-118">Como PackageManagement é um módulo do PowerShell, pode efetuar o seguinte procedimento para atualizar PackageManagement próprio:</span><span class="sxs-lookup"><span data-stu-id="fe4b7-118">As PackageManagement is a PowerShell module, you can do the following to update PackageManagement itself:</span></span>
```powershell
PS C:\> Install-Module PackageManagement –Force
```
<span data-ttu-id="fe4b7-119">Neste caso, terá de reintroduzir a sessão do PowerShell para mudar para a nova versão do PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-119">In this case, you will have to re-enter PowerShell session to switch to the new version of PackageManagement.</span></span>

## <a name="find-package-cmdlethttpstechnetmicrosoftcomlibrarydn890709aspx"></a>[<span data-ttu-id="fe4b7-120">Encontrar o pacote Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fe4b7-120">Find-Package Cmdlet</span></span>](https://technet.microsoft.com/library/dn890709.aspx)
<span data-ttu-id="fe4b7-121">Este cmdlet permite a deteção de pacotes de software em origens de pacote disponíveis utilizando carregar fornecedores de pacote.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-121">This cmdlet allows discovery of software packages in available package sources using loaded package providers.</span></span>
```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -Provider PowerShellGet -Source PSGallery

# Find a package from a provider that is not yet installed
# This will bootstrap NuGet provider and then search for jquery package using NuGet
# with <http://www.nuget.org/api/v2/> as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdlethttpstechnetmicrosoftcomlibrarymt676544aspx"></a>[<span data-ttu-id="fe4b7-122">Localizar PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fe4b7-122">Find-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/library/mt676544.aspx)
<span data-ttu-id="fe4b7-123">O cmdlet Find PackageProvider localiza fornecedores PackageManagement correspondentes, que estão disponíveis em origens de pacote registadas PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-123">The Find-PackageProvider cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span> <span data-ttu-id="fe4b7-124">Estes são os fornecedores de pacote disponíveis para instalação com o cmdlet Install-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-124">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span> <span data-ttu-id="fe4b7-125">Por predefinição, isto inclui módulos disponíveis na galeria do PowerShell com o 'PackageManagement' e 'Provider' etiquetas.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-125">By default, this includes modules available in the PowerShell Gallery with the 'PackageManagement' and 'Provider' Tags.</span></span>

<span data-ttu-id="fe4b7-126">Localizar PackageProvider também localiza fornecedores PackageManagement correspondentes, que estão disponíveis no arquivo de Blobs do azure PackageManagement onde podemos utilizar o fornecedor de boostrapper PackageManagement para localizar e instalá-los.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-126">Find-PackageProvider also finds matching PackageManagement providers that are available in the PackageManagement azure blob store where we use the PackageManagement boostrapper provider for finding and installing them.</span></span>
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdlethttpstechnetmicrosoftcomlibrarydn890704aspx"></a>[<span data-ttu-id="fe4b7-127">Cmdlet Get-Package</span><span class="sxs-lookup"><span data-stu-id="fe4b7-127">Get-Package Cmdlet</span></span>](https://technet.microsoft.com/library/dn890704.aspx)
<span data-ttu-id="fe4b7-128">Este cmdlet devolve uma lista de todos os pacotes de software que foram instalados utilizando PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-128">This cmdlet returns a list of all software packages that have been installed using PackageManagement.</span></span>
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890703aspx"></a>[<span data-ttu-id="fe4b7-129">Cmdlet Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fe4b7-129">Get-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890703.aspx)
<span data-ttu-id="fe4b7-130">Fornecedores de pacote que são carregados e pronto a ser utilizado no computador local podem ser inventariados utilizando o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-130">Package providers that are loaded and ready to be used on the local machine can be inventoried by using the cmdlet.</span></span>
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890705aspx"></a>[<span data-ttu-id="fe4b7-131">Cmdlet Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="fe4b7-131">Get-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890705.aspx)
<span data-ttu-id="fe4b7-132">Este cmdlet obtém uma lista de origens de pacote que estão registados para um fornecedor do pacote.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-132">This cmdlet gets a list of package sources that are registered for a package provider.</span></span>
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676545aspx"></a>[<span data-ttu-id="fe4b7-133">Cmdlet de importação PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fe4b7-133">Import-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676545.aspx)
<span data-ttu-id="fe4b7-134">Este cmdlet adiciona fornecedores de pacote de gestão de pacotes para a sessão atual.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-134">This cmdlet adds Package Management package providers to the current session.</span></span>
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

##<a name="-install-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890711aspx"></a>[<span data-ttu-id="fe4b7-135"> Cmdlet Install-Package</span><span class="sxs-lookup"><span data-stu-id="fe4b7-135"> Install-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890711.aspx)

<span data-ttu-id="fe4b7-136">Este cmdlet permite a instalação de pacotes de software em origens de pacote disponível através de carregar os fornecedores de pacote.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-136">This cmdlet allows installation of software packages in available package sources using loaded package providers.</span></span>
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676543aspx"></a>[<span data-ttu-id="fe4b7-137">Cmdlet de instalação PackageProvider</span><span class="sxs-lookup"><span data-stu-id="fe4b7-137">Install-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676543.aspx)
<span data-ttu-id="fe4b7-138">Este cmdlet instala um ou mais fornecedores de pacote de gestão de pacotes.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-138">This cmdlet installs one or more Package Management package providers.</span></span>
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

## <a name="register-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890701aspx"></a>[<span data-ttu-id="fe4b7-139">Cmdlet register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="fe4b7-139">Register-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890701.aspx)
<span data-ttu-id="fe4b7-140">Este cmdlet adiciona uma origem de pacote para um fornecedor do pacote especificado.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-140">This cmdlet adds a package source for a specified package provider.</span></span>
<span data-ttu-id="fe4b7-141">Cada fornecedor PackageManagement pode ter uma ou várias origens de software ou repositórios.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-141">Each PackageManagement provider may have one or multiple software sources, or repositories.</span></span> <span data-ttu-id="fe4b7-142">PackageManagement fornece cmdlets do PowerShell para adicionar/remover/consulta de origem.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-142">PackageManagement provides PowerShell cmdlets to add/remove/query the source.</span></span> <span data-ttu-id="fe4b7-143">Por exemplo, pode registar uma origem de pacote para o fornecedor do NuGet:</span><span class="sxs-lookup"><span data-stu-id="fe4b7-143">For example, you can register a package source for the NuGet provider:</span></span>
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890708aspx"></a>[<span data-ttu-id="fe4b7-144">Guardar pacote Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fe4b7-144">Save-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890708.aspx)
<span data-ttu-id="fe4b7-145">Este cmdlet guarda pacotes para o computador local, sem instalá-los.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-145">This cmdlet saves packages to the local computer without installing them.</span></span>
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## <a name="set-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890710aspx"></a>[<span data-ttu-id="fe4b7-146">Cmdlet do Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="fe4b7-146">Set-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890710.aspx)
<span data-ttu-id="fe4b7-147">Este cmdlet altera as informações sobre uma origem de pacote existente.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-147">This cmdlet changes information about an existing package source.</span></span>
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890702aspx"></a>[<span data-ttu-id="fe4b7-148">Cmdlet de pacote desinstalar</span><span class="sxs-lookup"><span data-stu-id="fe4b7-148">Uninstall-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890702.aspx)
<span data-ttu-id="fe4b7-149">Este cmdlet desinstala os pacotes instalados no computador local.</span><span class="sxs-lookup"><span data-stu-id="fe4b7-149">This cmdlet uninstalls packages installed on the local computer.</span></span>
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890707aspx"></a>[<span data-ttu-id="fe4b7-150">Cmdlet PackageSource anular o registo</span><span class="sxs-lookup"><span data-stu-id="fe4b7-150">Unregister-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```
