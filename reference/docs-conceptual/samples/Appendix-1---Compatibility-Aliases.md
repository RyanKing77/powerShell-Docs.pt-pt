---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Apêndice 1 – Aliases de Compatibilidade
ms.openlocfilehash: 553b9f01d6b5e3f4e04f1a75c25979b54dc205da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030341"
---
# <a name="appendix-1---compatibility-aliases"></a>Apêndice 1 – Aliases de compatibilidade

Windows PowerShell tem vários aliases de transição que permitem aos usuários do UNIX e Cmd utilizar nomes de comandos familiares do Windows PowerShell. Os aliases mais comuns são mostrados na tabela a seguir, juntamente com o comando do Windows PowerShell por trás o alias e o alias padrão do Windows PowerShell se existir.

Pode encontrar o comando do Windows PowerShell que qualquer alias aponta para de dentro do Windows PowerShell utilizando o cmdlet Get-Alias. Por exemplo, digite **get-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Comando CMD|Comando de UNIX|PS Comando|PS Alias|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host** (função)|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|
