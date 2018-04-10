---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 3269c8cc871f22488b64fb072dac72698983f360
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="998ed-102">Chamar o Construtor de Classe Base</span><span class="sxs-lookup"><span data-stu-id="998ed-102">Call Base Class Constructor</span></span>

<span data-ttu-id="998ed-103">Para chamar um construtor de classe base a partir de uma subclasse, utilize a palavra-chave **base**:</span><span class="sxs-lookup"><span data-stu-id="998ed-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="998ed-104">Se uma classe base tem um construtor predefinido (sem parâmetros), pode omitir uma chamada do construtor explícita:</span><span class="sxs-lookup"><span data-stu-id="998ed-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```