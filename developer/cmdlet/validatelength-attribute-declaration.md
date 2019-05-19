---
title: Declaração de atributo ValidateLength | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 4d3cdccc0fe3e24b1221e41beef4821b613aab93
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855148"
---
# <a name="validatelength-attribute-declaration"></a>ValidateLength Attribute Declaration (Declaração do Atributo ValidateLength)

O atributo de ValidateLength Especifica o número mínimo e máximo de carateres para um argumento do parâmetro de cmdlet. Este atributo também pode ser utilizado por funções do Windows PowerShell.

## <a name="syntax"></a>Sintaxe

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parâmetros

`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required. Especifica o número mínimo de carateres permitidos.

`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required. Especifica o número máximo de carateres permitidos.

## <a name="remarks"></a>Observações

- Para obter mais informações sobre como declarar este atributo, consulte [como as regras de validação de entrada declarar](./how-to-validate-parameter-input.md).

- Quando esse atributo não for utilizado, o argumento do parâmetro correspondente pode ter qualquer comprimento.

- O tempo de execução do Windows PowerShell emite um erro nas seguintes condições:

    - Quando o valor do `MaxLength` parametr atributu é inferior ao valor da `MinLength` atributo de parâmetro.

    - Quando o `MaxLength` parâmetro de atributo é definido como 0.

    - Quando o argumento não é uma cadeia de caracteres.

- O atributo ValidateLength é definido pela [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) classe.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
