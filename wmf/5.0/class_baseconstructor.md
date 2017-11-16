---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 1fd6d80d6b7effb4bd98c1594d64e531c4e5c9b5
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2017
---
# <a name="call-base-class-constructor"></a>Chame o construtor de classe Base

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

