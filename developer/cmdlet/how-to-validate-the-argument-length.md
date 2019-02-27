---
title: Como validar o comprimento do argumento | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847601"
---
# <a name="how-to-validate-the-argument-length"></a>How to Validate the Argument Length (Como Validar o Comprimento de Argumentos)

Este exemplo mostra como especificar uma regra de validação que o tempo de execução do Windows PowerShell pode usar para verificar o número de carateres (o comprimento) do argumento do parâmetro antes do cmdlet é executado. Defina esta regra de validação ao declarar o atributo ValidateLength.

> [!NOTE]
> Para obter mais informações sobre a classe que define esse atributo, consulte [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>Para validar o comprimento do argumento

- Adicione o atributo de validar, conforme mostrado no código a seguir. Este exemplo Especifica que o comprimento do argumento deve ter um comprimento de 0 a 10 carateres.

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obter mais informações sobre como declarar este atributo, consulte [declaração de atributo ValidateLength](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Veja Também

[Declaração de atributo ValidateLength](./validatelength-attribute-declaration.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
