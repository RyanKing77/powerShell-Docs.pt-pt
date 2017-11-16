---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Localizar RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a>Localizar RoleCapability

Encontra capacidades de funções nos módulos.

## <a name="description"></a>Descrição
O cmdlet Find RoleCapability localiza capacidades de função do PowerShell nos módulos. Localizar RoleCapability procura módulos no repositórios registados. Para cada capacidade de função que este cmdlet localiza, devolve um objeto de PSGetRoleCapabilityInfo. Pode transmitir um objeto de PSGetRoleCapabilityInfo para o cmdlet do módulo de instalação para instalar o módulo que contém a capacidade de função.
Capacidades de função de PowerShell definem quais os comandos, aplicações e assim sucessivamente estão disponíveis para um utilizador de um ponto final apenas suficiente administração (JEA). Capacidades de função são definidas pelos ficheiros com uma extensão de .psrc.

- Localizar RoleCapability pode filtrar com parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.
  - Estes parâmetros são mutuamente exclusivos.
  - Estes parâmetros de versão são permitidos apenas com o nome do módulo único sem quaisquer carateres universais.
  - Se não for especificado o parâmetro RequiredVersion, localizar RoleCapability devolve a versão mais recente do módulo que seja igual ou maior do que a versão mínima especificado ou a versão mais recente do módulo, não se for especificada nenhuma versão mínima.
  - Se não for especificado o parâmetro RequiredVersion, localizar RoleCapability devolve apenas a versão do módulo que corresponde exatamente a versão especificada.
- Pode filtrar RoleCapability localizar nos metadados do módulo com o parâmetro-etiqueta
- Localizar RoleCapability pode filtrar por idioma específicas do repositório de pesquisa com o parâmetro-filtro.
- Localizar RoleCapability pode filtrar por módulos de todas as ou poucos dos repositórios do registado.

## <a name="cmdlet-syntax"></a>Sintaxe de cmdlet
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Referência de ajuda online do cmdlet

[Localizar RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a>Comandos de exemplo
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

