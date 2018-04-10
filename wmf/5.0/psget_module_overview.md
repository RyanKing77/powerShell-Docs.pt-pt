---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 82b8046d5cbb47300f090ce2ffbf3c279ed19458
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>Deteção de módulo do PowerShell, instalar e de inventário com PowerShellGet

PowerShellGet está incluído nesta versão do WMF:
-   Pode filtrar encontrar o módulo nos metadados do módulo com o parâmetro-etiqueta
-   Encontrar o módulo pode filtrar por idioma específicas do repositório de pesquisa com o filtro parâmetro -
-   Pode encontrar o módulo filtro com base num módulo conteúdo com - comando, - DscResource e - inclui os parâmetros
-   Localizar DscResource permite a deteção de recursos de DSC individuais em repositórios
-   Suporte para instalar a partir do e da publicação para partilhas de ficheiros com NuGet

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

## <a name="new-features-in-powershellget"></a>Novas funcionalidades no PowerShellGet
-   Suporte para a versão de lado a lado no Windows PowerShell 5.0 ou mais recente
-   Suporte de instalação de dependência do módulo
-   Três novos cmdlets
    -   Get-InstalledModule
    -   Uninstall-Module
    -   Módulo de guardar