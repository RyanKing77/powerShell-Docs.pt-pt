---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085886"
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

Se uma classe base tem um construtor padrão (nenhum parâmetro), pode omitir uma chamada de construtor explícito:

```powershell
class C : B
{
    C([int]$c) {}
}
```
