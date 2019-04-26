---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 042e9a30068d32dc5860255bdec960371121d866
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085305"
---
# <a name="packagemanagement-cmdlets"></a>Cmdlets PackageManagement

Este é o núcleo do PackageManagement para suportar a deteção de software, instalação e inventário (SDII). Experimente os cmdlets para essas operações:

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

Como PackageManagement é um módulo do PowerShell, pode fazer o seguinte para atualizar PackageManagement em si:

```powershell
Install-Module PackageManagement –Force
```

Neste caso, terá de reintroduzir a sessão do PowerShell para mudar para a nova versão do PackageManagement.

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[Cmdlet de Find-Package](/powershell/module/PackageManagement/Find-Package)

Este cmdlet permite a deteção de pacotes de software em origens de pacotes disponíveis usando carregado fornecedores de pacote.

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

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[Find-PackageProvider Cmdlet](/powershell/module/PackageManagement/Find-PackageProvider)

O `Find-PackageProvider` cmdlet localiza a correspondência PackageManagement fornecedores que estão disponíveis no origens do pacote registrado com o PowerShellGet. Estes são os fornecedores de pacote disponíveis para instalação com o `Install-PackageProvider` cmdlet. Por predefinição, isto inclui módulos disponíveis na galeria do PowerShell com o "PackageManagement" e "Fornecedor" etiquetas.

`Find-PackageProvider` também encontra fornecedores PackageManagement correspondentes que estão disponíveis no armazenamento de Blobs do azure PackageManagement onde podemos usar o provedor de boostrapper PackageManagement para procurar e instalá-los.

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[Cmdlet Get-Package](/powershell/module/PackageManagement/Get-Package)

Este cmdlet devolve uma lista de todos os pacotes de software que tenham sido instaladas através do PackageManagement.

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[Cmdlet Get-PackageProvider](/powershell/module/PackageManagement/Get-PackageProvider)

Fornecedores de pacote que são carregados e pronto a ser utilizado no computador local podem ser inventariados com o cmdlet.

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[Cmdlet Get-PackageSource](/powershell/module/PackageManagement/Get-PackageSource)

Este cmdlet obtém uma lista de origens de pacotes que estão registados para um fornecedor do pacote.

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[Cmdlet de importação PackageProvider](/powershell/module/PackageManagement/Import-PackageProvider)

Este cmdlet adiciona os fornecedores de pacote de gestão de pacotes para a sessão atual.

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

## <a name="install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[Cmdlet Install-Package](/powershell/module/PackageManagement/Install-Package)

Este cmdlet permite a instalação de pacotes de software em origens de pacotes disponíveis usando carregado fornecedores de pacote.

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[Cmdlet de instalação PackageProvider](/powershell/module/PackageManagement/Install-PackageProvider)

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

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[Cmdlet register-PackageSource](/powershell/module/PackageManagement/Register-PackageSource)

Este cmdlet adiciona uma origem de pacote de um fornecedor do pacote especificado.
Cada fornecedor de PackageManagement pode ter uma ou várias origens de software ou repositórios. PackageManagement fornece cmdlets do PowerShell para adicionar/remover/consulta a origem. Por exemplo, pode registar uma origem de pacote para o fornecedor do NuGet:

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[Cmdlet Save-Package](/powershell/module/PackageManagement/Save-Package)

Este cmdlet guarda pacotes no computador local, sem instalá-los.

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[Cmdlet Set-PackageSource](/powershell/module/PackageManagement/Set-PackageSource)

Este cmdlet altera as informações sobre uma origem de pacote existente.

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[Cmdlet Uninstall-Package](/powershell/module/PackageManagement/Uninstall-Package)

Este cmdlet desinstala os pacotes instalados no computador local.

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[Cmdlet PackageSource anular o registo](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```