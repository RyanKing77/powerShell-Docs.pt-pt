---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 968e78beb8df77588a08a9ce8732e4abcadde4d0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2017
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="dac66-102">Declarar Interface implementada</span><span class="sxs-lookup"><span data-stu-id="dac66-102">Declare Implemented Interface</span></span>

<span data-ttu-id="dac66-103">Podem declarar interfaces implementadas após tipos base ou imediatamente após o ponto e vírgula (:), se não houver nenhum tipo base especificado.</span><span class="sxs-lookup"><span data-stu-id="dac66-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="dac66-104">Separe todos os nomes de tipo utilizando vírgulas.</span><span class="sxs-lookup"><span data-stu-id="dac66-104">Separate all type names by using commas.</span></span> <span data-ttu-id="dac66-105">É muito semelhante a sintaxe do c#.</span><span class="sxs-lookup"><span data-stu-id="dac66-105">It’s very similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

