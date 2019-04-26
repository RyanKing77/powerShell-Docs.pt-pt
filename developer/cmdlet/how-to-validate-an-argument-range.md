---
title: Como validar um intervalo de argumento | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067795"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="84ead-102">How to Validate an Argument Range (Como Validar um Intervalo de Argumentos)</span><span class="sxs-lookup"><span data-stu-id="84ead-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="84ead-103">Este exemplo mostra como especificar uma regra de validação que o tempo de execução do Windows PowerShell pode usar para verificar os valores mínimos e máximo do argumento do parâmetro antes do cmdlet é executado.</span><span class="sxs-lookup"><span data-stu-id="84ead-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="84ead-104">Defina esta regra de validação ao declarar o atributo ValidateRange.</span><span class="sxs-lookup"><span data-stu-id="84ead-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="84ead-105">Para obter mais informações sobre a classe que define esse atributo, consulte [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="84ead-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="84ead-106">Para validar um intervalo de argumento</span><span class="sxs-lookup"><span data-stu-id="84ead-106">To validate an argument range</span></span>

- <span data-ttu-id="84ead-107">Adicione o atributo de ValidateRange, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="84ead-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="84ead-108">Este exemplo Especifica um intervalo de 0 a 5 para o `InputData` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="84ead-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

<span data-ttu-id="84ead-109">Para obter mais informações sobre como declarar este atributo, consulte [declaração de atributo ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="84ead-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84ead-110">Veja Também</span><span class="sxs-lookup"><span data-stu-id="84ead-110">See Also</span></span>

[<span data-ttu-id="84ead-111">Declaração de atributo ValidateRange</span><span class="sxs-lookup"><span data-stu-id="84ead-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="84ead-112">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="84ead-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
