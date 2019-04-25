---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a0b1573611c5d4232082c19ca19b4cca79d0699e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057473"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>Deteção de módulo do PowerShell, instalar e inventário com o PowerShellGet

O PowerShellGet está incluído nesta versão do WMF:
-   Find-Module pode filtrar os metadados do módulo com o - parâmetro de etiqueta
-   Find-Module poderá filtrar na linguagem de pesquisa de repositório específico com o parâmetro - Filter
-   Find-Module pode filtrar com base num módulo de conteúdo com o - comando, - DscResource e - inclui parâmetros
-   Find-DscResource permite a deteção de recursos de DSC individuais nos repositórios
-   Suporte para a instalação do e publicação de partilhas de ficheiros com o NuGet

## <a name="example-commands"></a>Comandos de exemplo
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a>Novos recursos do PowerShellGet
-   Suporte para a versão de lado a lado no Windows PowerShell 5.0 ou mais recente
-   Suporte de instalação de dependência do módulo
-   Três novos cmdlets
    -   Get-InstalledModule
    -   Uninstall-Module
    -   Save-Module
