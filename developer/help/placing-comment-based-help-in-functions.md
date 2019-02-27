---
title: Colocar baseada no comentário ajuda nas funções | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848175"
---
# <a name="placing-comment-based-help-in-functions"></a>Placing Comment-Based Help in Functions (Colocar Ajuda Baseada em Comentários em Funções)

Este tópico explica onde colocar a ajuda baseada no comentário para uma função para que o `Get-Help` cmdlet associa o tópico de ajuda baseada no comentário com a função correta.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Onde colocar a ajuda baseada no comentário para uma função

- No início do corpo da função.

- No final do corpo da função.

- Antes do `Function` palavra-chave. Quando a função está num script ou o módulo de script, não podem existir mais do que uma linha em branco entre a última linha da ajuda baseada no comentário e o `Function` palavra-chave. Caso contrário, `Get-Help` associa a ajuda com o script, não com a função.

## <a name="examples-of-help-placement-in-a-function"></a>Exemplos de colocação de ajuda numa função

 Os exemplos seguintes mostram cada uma das opções de colocação de três para ajuda baseada no comentário para uma função.

### <a name="help-at-the-beginning-of-a-function-body"></a>Ajudar a no início do corpo de uma função

 O exemplo seguinte mostra baseada no comentário no início do corpo de uma função.

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a>Ajudar a no final do corpo de uma função

 O exemplo seguinte mostra baseada no comentário no final do corpo de uma função.

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a>Ajudar a antes da palavra-chave de função

 Os exemplos a seguir mostra baseada no comentário na linha antes da palavra-chave de função.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```