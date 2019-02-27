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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849428"
---
# <a name="how-to-validate-an-argument-range"></a>How to Validate an Argument Range (Como Validar um Intervalo de Argumentos)

Este exemplo mostra como especificar uma regra de validação que o tempo de execução do Windows PowerShell pode usar para verificar os valores mínimos e máximo do argumento do parâmetro antes do cmdlet é executado. Defina esta regra de validação ao declarar o atributo ValidateRange.

> [!NOTE]
> Para obter mais informações sobre a classe que define esse atributo, consulte [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Para validar um intervalo de argumento

- Adicione o atributo de ValidateRange, conforme mostrado no código a seguir. Este exemplo Especifica um intervalo de 0 a 5 para o `InputData` parâmetro.

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

Para obter mais informações sobre como declarar este atributo, consulte [declaração de atributo ValidateRange](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Veja Também

[Declaração de atributo ValidateRange](./validaterange-attribute-declaration.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
