---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="call-base-class-constructor"></a>Chamar o Construtor de Classe Base

Para chamar um construtor de classe base a partir de uma subclasse, utilize a palavra-chave **base**:

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

Se uma classe base tem um construtor predefinido (sem parâmetros), pode omitir uma chamada do construtor explícita:

```powershell
class C : B
{
    C([int]$c) {}
}
```
