---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Localizar DscResource
ms.openlocfilehash: 522a44e25c57a7dd75a098a1f34e53e74d96f4a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="find-dscresource"></a>Localizar DscResource

Localiza recursos de DSC nos módulos.

## <a name="description"></a>Descrição

O cmdlet Find DscResource localiza [configuração de estado pretendido (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) recursos contidos nos módulos que correspondem aos critérios especificados da repositórios registados.
Para cada módulo que este cmdlet localiza, localizar DscResource devolve um objeto de PSGetDscResourceInfo que podem ser transmitidos para o módulo de instalação para instalar os módulos que contém os recursos que este cmdlet devolve.

DSC é uma nova plataforma de gestão do Windows PowerShell que lhe permite implementar e gerir dados de configuração para os serviços de software e gerir o ambiente em que estes serviços são executados.

Pretendido que recursos de configuração de estado (DSC) fornecem os blocos modulares para uma configuração de DSC. Um recurso expõe propriedades que podem ser configurada (esquema) e contém as funções de script do PowerShell que chama o Gestor de configuração Local (MMC) para "torná-lo,".

Um recurso pode modelo algo como genérica como um ficheiro ou uma definição de servidor IIS tão específico. Grupos de como recursos são combinados para um módulo de DSC, que organiza todos os ficheiros necessários na uma estrutura que é portátil e inclui os metadados para identificar a forma como os recursos destinam-se a ser utilizado.

- Localizar DscResource pode filtrar com parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.
  - Estes parâmetros são mutuamente exclusivos.
  - Estes parâmetros de versão são permitidos apenas com o nome do módulo único sem quaisquer carateres universais.
  - Se não for especificado o parâmetro RequiredVersion, localizar DscResource devolve a versão mais recente do módulo que seja igual ou maior do que a versão mínima especificado ou a versão mais recente do módulo, não se for especificada nenhuma versão mínima.
  - Se não for especificado o parâmetro RequiredVersion, localizar DscResource devolve apenas a versão do módulo que corresponde exatamente a versão especificada.
- Pode filtrar DscResource localizar nos metadados do módulo com o parâmetro-etiqueta
- Localizar DscResource pode filtrar por idioma específicas do repositório de pesquisa com o parâmetro-filtro.
- Localizar DscResource pode filtrar por módulos de todas as ou poucos dos repositórios do registado.

## <a name="cmdlet-syntax"></a>Sintaxe de cmdlet
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Referência de ajuda online do cmdlet

[Find-DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a>Comandos de exemplo
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```