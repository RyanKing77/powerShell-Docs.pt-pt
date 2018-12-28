---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Apêndice 1 – Aliases de Compatibilidade
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405554"
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
|**dir**|**Ls**|**Get-ChildItem**|**gci**|
|**CLS**|**Limpar**|**Clear-Host** (função)|**CLS**|
|**DEL, apagar, rmdir**|**RM**|**Remove-Item**|**RI**|
|**Cópia**|**CP**|**Copy-Item**|**CI**|
|**mover**|**mV**|**Move-Item**|**mi**|
|**Mudar o nome**|**mV**|**Rename-Item**|**rni**|
|**Tipo**|**cat**|**Get-Content**|**GC**|
|**CD**|**CD**|**Definir localização**|**SL**|
|**MD**|**mkdir**|**Novo Item**|**Ni**|
|**pushd**|**pushd**|**Localização de push**|**pushd**|
|**popd**|**popd**|**Localização pop**|**popd**|