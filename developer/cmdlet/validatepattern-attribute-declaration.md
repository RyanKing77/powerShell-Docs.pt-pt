---
title: Declaração de atributo ValidatePattern | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848826"
---
# <a name="validatepattern-attribute-declaration"></a>ValidatePattern Attribute Declaration (Declaração do Atributo ValidatePattern)

O atributo de ValidatePattern Especifica um padrão de expressão regular que valida o argumento de um parâmetro de cmdlet. Este atributo também pode ser utilizado por funções do Windows PowerShell.

Quando ValidatePattern é invocado dentro de um cmdlet, o tempo de execução do Windows PowerShell converte o argumento do parâmetro de cmdlet numa cadeia de caracteres e, em seguida, compara essa cadeia de caracteres para o padrão fornecido pelo atributo ValidatePattern. O cmdlet é executado apenas se a representação de cadeia de caracteres convertida do argumento e o padrão fornecido corresponde. Se não forem iguais, ocorrerá um erro ao tempo de execução do Windows PowerShell.

## <a name="syntax"></a>Sintaxe

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parâmetros

`RegexString` ([System. String](/dotnet/api/System.String)) necessária. Especifica uma expressão regular que valida o argumento do parâmetro.

Opções ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) opcional chamado de parameter. Especifica uma combinação de bit a bit de [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) sinalizadores que especificam as opções de expressão regular.

## <a name="remarks"></a>Observações

- Este atributo pode ser utilizado apenas uma vez por parâmetro.

- Pode utilizar o `Option` parâmetro do atributo para definir mais aprofundadamente o padrão. Por exemplo, pode fazer o padrão de maiúsculas de minúsculas.

- Se este atributo é aplicado a uma coleção, cada elemento na coleção tem de corresponder ao padrão.

- O atributo ValidatePattern é definido pela [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) classe.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
