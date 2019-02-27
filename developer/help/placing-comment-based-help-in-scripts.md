---
title: Colocar a ajuda baseada no comentário em Scripts | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850149"
---
# <a name="placing-comment-based-help-in-scripts"></a>Placing Comment-Based Help in Scripts (Colocar Ajuda Baseada em Comentários em Scripts)

Este tópico explica onde colocar baseada no comentário ajuda para obter um script para que o `Get-Help` cmdlet associa o tópico de ajuda baseada no comentário com scripts e não com qualquer das funções que podem ser no script.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Onde colocar baseada no comentário ajuda para obter um Script

- No início do ficheiro de script. Ajuda de script pode ser precedida no script apenas por comentários e linhas em branco.

- No final do ficheiro de script.

  Se o primeiro item no corpo do script (após a ajuda) é uma declaração de função, tem de existir pelo menos duas linhas em branco entre o fim do script ajuda e a declaração de função. Caso contrário, a ajuda é interpretada como sendo de ajuda para a função, não ajuda para o script.

## <a name="examples-of-help-placement-in-a-script"></a>Exemplos de colocação de ajuda num Script

 Os exemplos seguintes mostram cada uma das opções de colocação para baseada no comentário para obter ajuda para obter um script.

### <a name="help-at-the-beginning-of-a-script"></a>Ajudar a no início de um Script

 O exemplo seguinte mostra baseada no comentário no início de um script.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Ajudar no fim de um Script

 O exemplo seguinte mostra baseada no comentário no final de um script.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```