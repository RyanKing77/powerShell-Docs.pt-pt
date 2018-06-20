---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225492"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="67316-102">Declarar a Interface Implementada</span><span class="sxs-lookup"><span data-stu-id="67316-102">Declare Implemented Interface</span></span>

<span data-ttu-id="67316-103">Podem declarar interfaces implementadas após tipos base ou imediatamente após o ponto e vírgula (:), se não houver nenhum tipo base especificado.</span><span class="sxs-lookup"><span data-stu-id="67316-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="67316-104">Separe todos os nomes de tipo utilizando vírgulas.</span><span class="sxs-lookup"><span data-stu-id="67316-104">Separate all type names by using commas.</span></span> <span data-ttu-id="67316-105">É muito semelhante a sintaxe do c#.</span><span class="sxs-lookup"><span data-stu-id="67316-105">It’s very similar to C# syntax.</span></span>

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
