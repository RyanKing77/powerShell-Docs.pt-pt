---
title: Atributos no código de Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845263"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="94aa4-102">Attributes in Cmdlet Code (Atributos no Código Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="94aa4-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="94aa4-103">Para utilizar a funcionalidade comum fornecida pelo Windows PowerShell, as classes e propriedades públicas definidas no código cmdlet são decoradas com atributos.</span><span class="sxs-lookup"><span data-stu-id="94aa4-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="94aa4-104">Por exemplo, a seguinte definição de classe usa o atributo de Cmdlet para identificar a classe do Microsoft .NET Framework em que o **Get-Proc** cmdlet é implementado.</span><span class="sxs-lookup"><span data-stu-id="94aa4-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="94aa4-105">(Este cmdlet é utilizado como um exemplo neste documento e é semelhante a `Get-Process` cmdlet fornecido pelo Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="94aa4-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="94aa4-106">Esses atributos são considerados os metadados porque a sua implementação é separada da implementação do código de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94aa4-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="94aa4-107">Quando o tempo de execução do Windows PowerShell é executado o cmdlet, ele reconhece os atributos e, em seguida, executa a ação apropriada para cada atributo.</span><span class="sxs-lookup"><span data-stu-id="94aa4-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="94aa4-108">Embora pode querer implementar sua própria versão da funcionalidade fornecida por esses atributos, a estrutura de um cmdlet boa utiliza essas funcionalidades comuns.</span><span class="sxs-lookup"><span data-stu-id="94aa4-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="94aa4-109">Para obter mais informações sobre os atributos diferentes que pode ser declarado nos seus cmdlets, consulte [tipos de atributo](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="94aa4-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="94aa4-110">Veja Também</span><span class="sxs-lookup"><span data-stu-id="94aa4-110">See Also</span></span>

[<span data-ttu-id="94aa4-111">Tipos de atributos</span><span class="sxs-lookup"><span data-stu-id="94aa4-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="94aa4-112">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="94aa4-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
