---
ms.date: 09/09/2019
keywords: PowerShell, cmdlet
title: Apêndice 1 – Aliases de Compatibilidade
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848174"
---
# <a name="appendix-1---compatibility-aliases"></a>Apêndice 1-aliases de compatibilidade

O PowerShell tem vários aliases que permitem que os usuários do **Unix** e **cmd. exe** usem comandos conhecidos.
Os comandos e seus cmdlets do PowerShell relacionados e alias do PowerShell são mostrados na tabela a seguir:

|comando cmd. exe|Comando UNIX|Cmdlet do PowerShell|Alias do PowerShell|
|---------------|----------------|--------------|------------|
|**CLS**|**clear**|`Clear-Host`funcionamento|`cls`|
|**CopiarObjeto**|**CP**|`Copy-Item`|`cpi`|
|**comando**|**ls**|`Get-ChildItem`|`gci`|
|**type**|**cat**|`Get-Content`|`gc`|
|**prosseguir**|**MV**|`Move-Item`|`mi`|
|**MD**|**mkdir**|`New-Item`|`ni`|
|**PUSHD**|**PUSHD**|`Push-Location`|`pushd`|
|**popd**|**popd**|`Pop-Location`|`popd`|
|**del**, **Erase**, **RD**, **rmdir**|**RM**|`Remove-Item`|`ri`|
|**Outlook**|**MV**|`Rename-Item`|`rni`|
|**CD**, **chdir**|**CD**|`Set-Location`|`sl`|

Para localizar os aliases do PowerShell, use o cmdlet [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) . Para exibir os aliases de um cmdlet, use o parâmetro de **definição** e especifique o nome do cmdlet.
Ou, para localizar o nome do cmdlet de um alias, use o parâmetro **Name** e especifique o alias.

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
