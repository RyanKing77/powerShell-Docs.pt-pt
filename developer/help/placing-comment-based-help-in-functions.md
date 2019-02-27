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
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="0c647-102">Placing Comment-Based Help in Functions (Colocar Ajuda Baseada em Comentários em Funções)</span><span class="sxs-lookup"><span data-stu-id="0c647-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="0c647-103">Este tópico explica onde colocar a ajuda baseada no comentário para uma função para que o `Get-Help` cmdlet associa o tópico de ajuda baseada no comentário com a função correta.</span><span class="sxs-lookup"><span data-stu-id="0c647-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="0c647-104">Onde colocar a ajuda baseada no comentário para uma função</span><span class="sxs-lookup"><span data-stu-id="0c647-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="0c647-105">No início do corpo da função.</span><span class="sxs-lookup"><span data-stu-id="0c647-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="0c647-106">No final do corpo da função.</span><span class="sxs-lookup"><span data-stu-id="0c647-106">At the end of the function body.</span></span>

- <span data-ttu-id="0c647-107">Antes do `Function` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="0c647-107">Before the `Function` keyword.</span></span> <span data-ttu-id="0c647-108">Quando a função está num script ou o módulo de script, não podem existir mais do que uma linha em branco entre a última linha da ajuda baseada no comentário e o `Function` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="0c647-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="0c647-109">Caso contrário, `Get-Help` associa a ajuda com o script, não com a função.</span><span class="sxs-lookup"><span data-stu-id="0c647-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="0c647-110">Exemplos de colocação de ajuda numa função</span><span class="sxs-lookup"><span data-stu-id="0c647-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="0c647-111">Os exemplos seguintes mostram cada uma das opções de colocação de três para ajuda baseada no comentário para uma função.</span><span class="sxs-lookup"><span data-stu-id="0c647-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="0c647-112">Ajudar a no início do corpo de uma função</span><span class="sxs-lookup"><span data-stu-id="0c647-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="0c647-113">O exemplo seguinte mostra baseada no comentário no início do corpo de uma função.</span><span class="sxs-lookup"><span data-stu-id="0c647-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="0c647-114">Ajudar a no final do corpo de uma função</span><span class="sxs-lookup"><span data-stu-id="0c647-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="0c647-115">O exemplo seguinte mostra baseada no comentário no final do corpo de uma função.</span><span class="sxs-lookup"><span data-stu-id="0c647-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="0c647-116">Ajudar a antes da palavra-chave de função</span><span class="sxs-lookup"><span data-stu-id="0c647-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="0c647-117">Os exemplos a seguir mostra baseada no comentário na linha antes da palavra-chave de função.</span><span class="sxs-lookup"><span data-stu-id="0c647-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```