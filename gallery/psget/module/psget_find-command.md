---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Encontrar o comando
ms.openlocfilehash: 26ddf4824816db245131a0fc95b7d2a88bef8f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="find-command"></a>Encontrar o comando

Localiza os comandos do PowerShell nos módulos.

## <a name="description"></a>Descrição
O cmdlet do comando de localizar localiza os comandos do PowerShell como os cmdlets, aliases, funções e fluxos de trabalho. Localizar comando procura módulos no repositórios registados.
Para cada comando que se encontra este cmdlet, devolve um objeto de PSGetCommandInfo. Pode transmitir um objeto de PSGetCommandInfo para o cmdlet do módulo de instalação para instalar o módulo que contém o comando.

- Pode filtrar localizar comando com parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.
  - Estes parâmetros são mutuamente exclusivos.
  - Estes parâmetros de versão são permitidos apenas com o nome do módulo único sem quaisquer carateres universais.
  - Se não for especificado o parâmetro RequiredVersion, localizar comando devolve a versão mais recente do módulo que seja igual ou maior do que a versão mínima especificado ou a versão mais recente do módulo, não se for especificada nenhuma versão mínima.
  - Se o parâmetro RequiredVersion for especificado, o comando de localizar devolve apenas a versão do módulo que corresponde exatamente a versão especificada.
- Pode filtrar comando Localizar nos metadados do módulo com o parâmetro-etiqueta
- Encontrar o comando pode filtrar por idioma específicas do repositório de pesquisa com o parâmetro-filtro.
- Encontrar o comando pode filtrar por módulos de todas as ou poucos dos repositórios do registado.

## <a name="cmdlet-syntax"></a>Sintaxe de cmdlet
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Referência de ajuda online do cmdlet

[Find-Command](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a>Comandos de exemplo
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```