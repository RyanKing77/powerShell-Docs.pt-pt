---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 6cba004890fc4b1dfac40920f751f61b0530cce9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="packagemanagement-cmdlets"></a>Cmdlets de PackageManagement
Este é o núcleo dos PackageManagement para suportar a deteção de software, instalação e inventário (SDII). Experimente os cmdlets para estas operações:
-   Encontrar o pacote
-   Localizar PackageProvider
-   Get-Package
-   Get-PackageProvider
-   Get-PackageSource
-   Importar PackageProvider
-   Pacote de instalação
-   Instalação PackageProvider
-   Registar PackageSource
-   Guardar pacote
-   Conjunto PackageSource
-   Pacote de desinstalação
-   PackageSource anular o registo

Como PackageManagement é um módulo do PowerShell, pode efetuar o seguinte procedimento para atualizar PackageManagement próprio:
```powershell
PS C:\> Install-Module PackageManagement –Force
```
Neste caso, terá de reintroduzir a sessão do PowerShell para mudar para a nova versão do PackageManagement.

## <a name="find-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890709aspx"></a>[Encontrar o pacote Cmdlet](https://technet.microsoft.com/en-us/library/dn890709.aspx)
Este cmdlet permite a deteção de pacotes de software em origens de pacote disponíveis utilizando carregar fornecedores de pacote.
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

## <a name="find-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676544aspx"></a>[Localizar PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/mt676544.aspx)
O cmdlet Find PackageProvider localiza fornecedores PackageManagement correspondentes, que estão disponíveis em origens de pacote registadas PowerShellGet. Estes são os fornecedores de pacote disponíveis para instalação com o cmdlet Install-PackageProvider. Por predefinição, isto inclui módulos disponíveis na galeria do PowerShell com o 'PackageManagement' e 'Provider' etiquetas. 

Localizar PackageProvider também localiza fornecedores PackageManagement correspondentes, que estão disponíveis no arquivo de Blobs do azure PackageManagement onde podemos utilizar o fornecedor de boostrapper PackageManagement para localizar e instalá-los.
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890704aspx"></a>[Cmdlet Get-Package](https://technet.microsoft.com/en-us/library/dn890704.aspx)
Este cmdlet devolve uma lista de todos os pacotes de software que foram instalados utilizando PackageManagement.
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890703aspx"></a>[Cmdlet Get-PackageProvider](https://technet.microsoft.com/en-us/library/dn890703.aspx)
Fornecedores de pacote que são carregados e pronto a ser utilizado no computador local podem ser inventariados utilizando o cmdlet.
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890705aspx"></a>[Cmdlet Get-PackageSource](https://technet.microsoft.com/en-us/library/dn890705.aspx)
Este cmdlet obtém uma lista de origens de pacote que estão registados para um fornecedor do pacote.
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676545aspx"></a>[Cmdlet de importação PackageProvider](https://technet.microsoft.com/en-us/library/mt676545.aspx)
Este cmdlet adiciona fornecedores de pacote de gestão de pacotes para a sessão atual.
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

##<a name="-install-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890711aspx"></a>[Cmdlet Install-Package](https://technet.microsoft.com/en-us/library/dn890711.aspx)

Este cmdlet permite a instalação de pacotes de software em origens de pacote disponível através de carregar os fornecedores de pacote.
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676543aspx"></a>[Cmdlet de instalação PackageProvider](https://technet.microsoft.com/en-us/library/mt676543.aspx)
Este cmdlet instala um ou mais fornecedores de pacote de gestão de pacotes.
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

## <a name="register-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890701aspx"></a>[Cmdlet register-PackageSource](https://technet.microsoft.com/en-us/library/dn890701.aspx)
Este cmdlet adiciona uma origem de pacote para um fornecedor do pacote especificado.
Cada fornecedor PackageManagement pode ter uma ou várias origens de software ou repositórios. PackageManagement fornece cmdlets do PowerShell para adicionar/remover/consulta de origem. Por exemplo, pode registar uma origem de pacote para o fornecedor do NuGet:
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890708aspx"></a>[Guardar pacote Cmdlet](https://technet.microsoft.com/en-us/library/dn890708.aspx)
Este cmdlet guarda pacotes para o computador local, sem instalá-los.
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## <a name="set-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890710aspx"></a>[Cmdlet do Set-PackageSource](https://technet.microsoft.com/en-us/library/dn890710.aspx)
Este cmdlet altera as informações sobre uma origem de pacote existente. 
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2 
```

## <a name="uninstall-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890702aspx"></a>[Cmdlet de pacote desinstalar](https://technet.microsoft.com/en-us/library/dn890702.aspx)
Este cmdlet desinstala os pacotes instalados no computador local.
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890707aspx"></a>[Cmdlet PackageSource anular o registo](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```

