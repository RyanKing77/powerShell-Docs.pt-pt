---
title: Como validar um padrão de argumento | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846159"
---
# <a name="how-to-validate-an-argument-pattern"></a>How to Validate an Argument Pattern (Como Validar um Padrão de Argumentos)

Este exemplo mostra como especificar uma regra de validação que o tempo de execução do Windows PowerShell pode usar para verificar o padrão de caráter do argumento do parâmetro antes do cmdlet é executado. Defina esta regra de validação ao declarar o atributo ValidatePattern.

> [!NOTE]
> Para obter mais informações sobre a classe que define esse atributo, consulte [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Para validar um padrão de argumento

- Adicione o atributo de validar, conforme mostrado no código a seguir. Este exemplo Especifica um padrão de quatro dígitos, em que cada dígito tem um valor de 0 a 9.

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

Para obter mais informações sobre como declarar este atributo, consulte [declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Veja Também

[Declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
