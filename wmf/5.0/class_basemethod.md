---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0e79127faf3f9bf6fe7d525db5bb946daf3b93e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058629"
---
# <a name="call-base-class-method"></a><span data-ttu-id="c3916-102">Chamar o Método de Classe Base</span><span class="sxs-lookup"><span data-stu-id="c3916-102">Call Base Class Method</span></span>

<span data-ttu-id="c3916-103">Pode substituir os métodos existentes numa subclasse.</span><span class="sxs-lookup"><span data-stu-id="c3916-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="c3916-104">Para tal, declare métodos, utilizando o mesmo nome e assinatura:</span><span class="sxs-lookup"><span data-stu-id="c3916-104">To do this, declare methods by using the same name and signature:</span></span>

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="c3916-105">Para chamar os métodos de classe base das implementações substituídas, converter para a classe base ([baseClass] $isso) na invocação:</span><span class="sxs-lookup"><span data-stu-id="c3916-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="c3916-106">Todos os métodos do PowerShell são virtuais.</span><span class="sxs-lookup"><span data-stu-id="c3916-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="c3916-107">Pode ocultar os métodos não virtuais do .NET numa subclasse usando a mesma sintaxe para uma substituição: apenas declarar métodos com o mesmo nome e assinatura.</span><span class="sxs-lookup"><span data-stu-id="c3916-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```
