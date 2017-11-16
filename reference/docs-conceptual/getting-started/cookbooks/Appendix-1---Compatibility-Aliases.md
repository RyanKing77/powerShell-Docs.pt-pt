---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Apêndice 1 Aliases de compatibilidade"
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: d789139ef80d4208b56e0b2930f04f824a00537d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
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
|**conformidade com CLS**|**Limpar**|**Limpar anfitrião** (função)|**conformidade com CLS**|
|**DEL, apagar, rmdir**|**RM**|**Remover itens**|**RI**|
|**copiar**|**CP**|**Copy-Item**|**IC**|
|**mover**|**mV**|**Mover Item**|**mi**|
|**mudar o nome**|**mV**|**Item de mudança de nome**|**rni**|
|**tipo**|**cat**|**Get-conteúdo**|**GC**|
|**CD**|**CD**|**Localização do conjunto**|**SL**|
|**MD**|**mkdir**|**Novo Item**|**Ni**|
|**pushd**|**pushd**|**Localização de push**|**pushd**|
|**popd**|**popd**|**POP-localização**|**popd**|

