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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083234"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="3e886-102">Placing Comment-Based Help in Scripts (Colocar Ajuda Baseada em Comentários em Scripts)</span><span class="sxs-lookup"><span data-stu-id="3e886-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="3e886-103">Este tópico explica onde colocar baseada no comentário ajuda para obter um script para que o `Get-Help` cmdlet associa o tópico de ajuda baseada no comentário com scripts e não com qualquer das funções que podem ser no script.</span><span class="sxs-lookup"><span data-stu-id="3e886-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="3e886-104">Onde colocar baseada no comentário ajuda para obter um Script</span><span class="sxs-lookup"><span data-stu-id="3e886-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="3e886-105">No início do ficheiro de script.</span><span class="sxs-lookup"><span data-stu-id="3e886-105">At the beginning of the script file.</span></span> <span data-ttu-id="3e886-106">Ajuda de script pode ser precedida no script apenas por comentários e linhas em branco.</span><span class="sxs-lookup"><span data-stu-id="3e886-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="3e886-107">No final do ficheiro de script.</span><span class="sxs-lookup"><span data-stu-id="3e886-107">At the end of the script file.</span></span>

  <span data-ttu-id="3e886-108">Se o primeiro item no corpo do script (após a ajuda) é uma declaração de função, tem de existir pelo menos duas linhas em branco entre o fim do script ajuda e a declaração de função.</span><span class="sxs-lookup"><span data-stu-id="3e886-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="3e886-109">Caso contrário, a ajuda é interpretada como sendo de ajuda para a função, não ajuda para o script.</span><span class="sxs-lookup"><span data-stu-id="3e886-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="3e886-110">Exemplos de colocação de ajuda num Script</span><span class="sxs-lookup"><span data-stu-id="3e886-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="3e886-111">Os exemplos seguintes mostram cada uma das opções de colocação para baseada no comentário para obter ajuda para obter um script.</span><span class="sxs-lookup"><span data-stu-id="3e886-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="3e886-112">Ajudar a no início de um Script</span><span class="sxs-lookup"><span data-stu-id="3e886-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="3e886-113">O exemplo seguinte mostra baseada no comentário no início de um script.</span><span class="sxs-lookup"><span data-stu-id="3e886-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="3e886-114">Ajudar no fim de um Script</span><span class="sxs-lookup"><span data-stu-id="3e886-114">Help at the End of a Script</span></span>

 <span data-ttu-id="3e886-115">O exemplo seguinte mostra baseada no comentário no final de um script.</span><span class="sxs-lookup"><span data-stu-id="3e886-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```