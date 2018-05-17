---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 02aebbd2557298b1b88229fdf5f67bdd08cea452
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="powershellget-cmdlets-for-module-management"></a>Cmdlets do PowerShellGet para Gestão de Módulos

- [Localizar DscResource](https://technet.microsoft.com/library/mt654006.aspx)
- [Encontrar o módulo](https://technet.microsoft.com/library/dn807167.aspx)
- [Encontrar o Script](https://technet.microsoft.com/library/mt654001.aspx)
- [Get-InstalledModule](https://technet.microsoft.com/en-us/library/mt653990.aspx)
- [Get-InstalledScript](https://technet.microsoft.com/en-us/library/mt653994.aspx)
- [Get-PSRepository](https://technet.microsoft.com/en-us/library/dn807170.aspx)
- [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx)
- [Script de instalação](https://technet.microsoft.com/en-us/library/mt653998.aspx)
- [New-ScriptFileInfo](https://technet.microsoft.com/en-us/library/mt653995.aspx)
- [Publish-Module](https://technet.microsoft.com/en-us/library/dn807163.aspx)
- [Script publicar](https://technet.microsoft.com/en-us/library/mt654003.aspx)
- [Registar PSRepository](https://technet.microsoft.com/en-us/library/dn807168.aspx)
- [Save-Module](https://technet.microsoft.com/en-us/library/mt653992.aspx)
- [Script de guardar](https://technet.microsoft.com/en-us/library/mt654004.aspx)
- [Set-PSRepository](https://technet.microsoft.com/en-us/library/dn807165.aspx)
- [Test-ScriptFileInfo](https://technet.microsoft.com/en-us/library/mt654005.aspx)
- [Uninstall-Module](https://technet.microsoft.com/en-us/library/mt653996.aspx)
- [Script de desinstalação](https://technet.microsoft.com/en-us/library/mt653989.aspx)
- [Update-Module](https://technet.microsoft.com/en-us/library/dn807166.aspx)
- [Update-ModuleManifest](https://technet.microsoft.com/en-us/library/mt654002.aspx)
- [Script de atualização](https://technet.microsoft.com/en-us/library/mt653997.aspx)
- [Update-ScriptFileInfo](https://technet.microsoft.com/en-us/library/mt653991.aspx)
- [Unregister-PSRepository](https://technet.microsoft.com/en-us/library/dn807161.aspx)

## <a name="module-dependency-installation-support-get-installedmodule-and-uninstall-module-cmdlets"></a>Suporte de instalação do módulo dependência, Get-InstalledModule e os cmdlets do módulo de desinstalação
- Adicionar a população de dependências de módulo no cmdlet do módulo de publicar. As listas de RequiredModules e NestedModules de PSModuleInfo são utilizadas na preparação da lista de dependências de um módulo para ser publicado.
- Suporte de instalação de dependência adicionada em cmdlets do módulo de instalação e o módulo de atualização. Dependências de módulo estarem instaladas e atualizadas por predefinição.
- Adicionar um parâmetro - IncludeDependencies para o cmdlet do módulo de localizar para incluir as dependências de módulo nos resultados.
- Adicionado suporte - MaximumVersion no módulo localizar, instalar módulo e os cmdlets do módulo de atualização.
- Foram adicionados módulo de desinstalação e Get-InstalledModule cmdlets novos.

## <a name="powershellget-cmdlets-demo-with-module-dependencies-support"></a>Demonstração de cmdlets PowerShellGet com dependências do módulo de suporte:

### <a name="ensure-that-module-dependencies-are-available-on-the-repository"></a>Certifique-se de que estão disponíveis as dependências de módulo no repositório:
```powershell
Find-Module -Repository LocalRepo -Name RequiredModule1,RequiredModule2,RequiredModule3,NestedRequiredModule1,NestedRequiredModule2,NestedRequiredModule3 | Sort-Object -Property Name

Version    Name                     Repository    Description
-------    ----                     ----------    -----------
2.5        NestedRequiredModule1    LocalRepo     NestedRequiredModule1 module
2.5        NestedRequiredModule2    LocalRepo     NestedRequiredModule2 module
2.0        NestedRequiredModule3    LocalRepo     NestedRequiredModule3 module
2.5        RequiredModule1          LocalRepo     RequiredModule1 module
2.5        RequiredModule2          LocalRepo     RequiredModule2 module
2.0        RequiredModule3          LocalRepo     RequiredModule3 module
```

### <a name="create-a-module-with-dependencies-that-are-specified-in-the-requiredmodules-and-nestedmodules-properties-of-its-module-manifest"></a>Crie um módulo com dependências que são especificadas nas propriedades de RequiredModules e NestedModules do respetivo manifesto de módulo.
```powershell
$RequiredModules = @('RequiredModule1',
                     @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.5'; },
                     @{ModuleName = 'RequiredModule3'; RequiredVersion = '2.0'; })

$NestedRequiredModules = @('TestDepWithNestedRequiredModules1.psm1', 'NestedRequiredModule1',
                            @{ModuleName = 'NestedRequiredModule2'; ModuleVersion = '1.5'; },
                            @{ModuleName = 'NestedRequiredModule3'; RequiredVersion = '2.0'; })

New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\TestDepWithNestedRequiredModules1\TestDepWithNestedRequiredModules1.psd1' `
-NestedModules $NestedRequiredModules -RequiredModules $RequiredModules -ModuleVersion "1.0" -Description "TestDepWithNestedRequiredModules1 module"
```

###  <a name="publish-two-versions-10-and-20-of-the-testdepwithnestedrequiredmodules1-module-with-dependencies-to-the-repository"></a>Publicar duas versões (**"1.0"** e **"2.0"**) do módulo TestDepWithNestedRequiredModules1 com dependências para o repositório.
```powershell
Publish-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -NuGetApiKey "MyNuGet-ApiKey-For-LocalRepo"
```

###  <a name="find-the-testdepwithnestedrequiredmodules1-module-with-its-dependencies-by-specifying--includedependencies"></a>Localize o módulo de TestDepWithNestedRequiredModules1 com as respetivas dependências, especificando - IncludeDependencies.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo –IncludeDependencies -MaximumVersion "1.0"

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.5        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
```

### <a name="use-find-module-metadata-to-find-the-module-dependencies"></a>Utilize dos metadados do módulo de procura para localizar as dependências do módulo.
```powershell
$psgetModuleInfo = Find-Module -Repository MSPSGallery -Name ModuleWithDependencies2
$psgetModuleInfo.Dependencies.ModuleName

RequiredModule1
RequiredModule2
RequiredModule3
NestedRequiredModule1
NestedRequiredModule2
NestedRequiredModule3

$psgetModuleInfo.Dependencies

Name Value
---- -----
ModuleName RequiredModule1
CanonicalId PowerShellGet:RequiredModule1/#http://psget/psGallery/api/v2/

ModuleName RequiredModule2
ModuleVersion 2.0
CanonicalId PowerShellGet:RequiredModule2/2.0#http://psget/psGallery/api/v2/

ModuleName RequiredModule3
RequiredVersion 2.5
CanonicalId PowerShellGet:RequiredModule3/2.5#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule1
CanonicalId PowerShellGet:NestedRequiredModule1/#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule2
ModuleVersion 2.0
CanonicalId PowerShellGet:NestedRequiredModule2/2.0#http://psget/psGallery/api/v2/

ModuleName NestedRequiredModule3
RequiredVersion 2.5
CanonicalId PowerShellGet:NestedRequiredModule3/2.5#http://psget/psGallery/api/v2/
```

###  <a name="install-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>Instale o módulo de TestDepWithNestedRequiredModules1 com dependências.
```powershell
Install-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -RequiredVersion "1.0"
Get-InstalledModule

Version    Name                    Repository   Description
-------    ----                    ----------   -----------
1.0        NestedRequiredModule1   LocalRepo    NestedRequiredModule1 module
2.5        NestedRequiredModule2   LocalRepo    NestedRequiredModule2 module
2.0        NestedRequiredModule3   LocalRepo    NestedRequiredModule3 module
1.0        RequiredModule1         LocalRepo    RequiredModule1 module
2.5        RequiredModule2                    LocalRepo    RequiredModule2 module
2.0        RequiredModule3                    LocalRepo    RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1  LocalRepo    TestDepWithNestedRequiredModules1 module
```

###  <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>Atualize o módulo de TestDepWithNestedRequiredModules1 com dependências.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

###  <a name="run-the-uninstall-module-cmdlet-to-uninstall-a-module-that-you-installed-by-using-powershellget"></a>Execute o cmdlet Uninstall-Module para desinstalar um módulo que instalou utilizando PowerShellGet.
Se qualquer outro módulo depende do módulo que pretende eliminar, PowerShellGet emitir um erro.
```powershell
Get-InstalledModule -Name RequiredModule1 | Uninstall-Module

PackageManagement\Uninstall-Package : The module 'RequiredModule1' of version '2.5' in module base folder 'C:\Program Files\WindowsPowerShell\Modules\RequiredModule1\2.5' cannot be uninstalled, because one or more other modules 'ModuleWithDependencies2' are dependent on this module. Uninstall the modules that depend on this module before uninstalling module 'RequiredModule1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\PSGet.psm1:1303 char:25
+ ... $null = PackageManagement\\Uninstall-Package @PSBoundParameters
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : InvalidOperation: (Microsoft.Power...ninstallPackage:UninstallPackage) [Uninstall-Package], Exception
+ FullyQualifiedErrorId : UnableToUninstallAsOtherModulesNeedThisModule,Uninstall-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.UninstallPackage
```

## <a name="save-module-cmdlet"></a>Cmdlet do módulo de guardar
```powershell
Save-Module -Repository MSPSGallery -Name ModuleWithDependencies2 -Path C:\MySavedModuleLocation
dir C:\MySavedModuleLocation

Directory: C:\MySavedModuleLocation

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 4/21/2015 5:40 PM ModuleWithDependencies2
d----- 4/21/2015 5:40 PM NestedRequiredModule1
d----- 4/21/2015 5:40 PM NestedRequiredModule2
d----- 4/21/2015 5:40 PM NestedRequiredModule3
d----- 4/21/2015 5:40 PM RequiredModule1
d----- 4/21/2015 5:40 PM RequiredModule2
d----- 4/21/2015 5:40 PM RequiredModule3
```

## <a name="update-modulemanifest-cmdlet"></a>Cmdlet Update-ModuleManifest
Este novo cmdlet é utilizado para ajudar a atualização de manifesto do ficheiro com valores de propriedade de entrada. Demora todos os parâmetros que ModuleManifest de teste.

Repararmos que muitos autores de módulo pretende especificar "\*" valores exportado como FunctionsToExport, CmdletsToExport, etc. Durante a publicação do módulo para a galeria do PowerShell, comandos e as funções não especificadas não são preenchidos corretamente para a galeria. Por conseguinte, sugerimos que módulo autores atualização os manifestos com valores adequados.

Se tiver de módulos que exportou propriedades, atualização ModuleManifest preencham completamente o ficheiro de manifesto especificado com as informações de funções exportadas, os cmdlets, variáveis etc:
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

Após a atualização-ModuleManifest:
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

Para cada módulo, também existem campos de metadados associados à mesma. Para poder apresentar os metadados corretamente na Galeria de PowrShell, pode utilizar a atualização ModuleManifest para preencher os campos em PrivateData.
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```
Tabela hash de PrivateData do modelo de ficheiro de manifesto tem as seguintes propriedades:
```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```
***Nota:*** DscResourcesToExport só é suportada no mais recente versão 5.0 do PowerShell. Iremos não será possível atualizar o campo se estiver a executar numa versão anterior do PowerShell.
