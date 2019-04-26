---
title: Como validar uma contagem de argumento | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067812"
---
# <a name="how-to-validate-an-argument-count"></a>How to Validate an Argument Count (Como Validar a Contagem de Argumentos)

Este exemplo mostra como especificar uma regra de validação que o tempo de execução do Windows PowerShell pode usar para verificar o número de argumentos (a contagem), que aceita um parâmetro antes do cmdlet é executado. Defina esta regra de validação ao declarar o atributo ValidateCount.

> [!NOTE]
> Para obter mais informações sobre a classe que define esse atributo, consulte [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Para validar uma contagem de argumentos

- Adicione o atributo de validar, conforme mostrado no código a seguir. Este exemplo Especifica que o parâmetro aceitará um argumento ou até três argumentos.

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

Para obter mais informações sobre como declarar este atributo, consulte [declaração de atributo ValidateCount](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Veja Também

[Declaração de atributo ValidateCount](./validatecount-attribute-declaration.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
