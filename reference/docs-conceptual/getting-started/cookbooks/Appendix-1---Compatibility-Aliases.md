---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Apêndice 1 – Aliases de Compatibilidade
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954641"
---
# <a name="appendix-1---compatibility-aliases"></a>Apêndice 1 - Aliases de compatibilidade

Windows PowerShell tem vários aliases de transição que permitem aos utilizadores de UNIX e Cmd utilizar nomes de comandos familiares do Windows PowerShell. Os aliases mais comuns são apresentados na tabela abaixo, juntamente com o comando do Windows PowerShell atrás o alias e o alias padrão do Windows PowerShell se existir.

Pode encontrar o comando do Windows PowerShell que qualquer alias aponta para do Windows PowerShell utilizando o cmdlet Get-Alias. Por exemplo, digite **get-alias cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|Comandos CMD|Comando de UNIX|PS Comando|PS Alias|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Limpar anfitrião** (função)|**cls**|
|**DEL, apagar, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|