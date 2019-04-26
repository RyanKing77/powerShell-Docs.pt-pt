---
title: Declaração de atributo ValidateSet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067077"
---
# <a name="validateset-attribute-declaration"></a>ValidateSet Attribute Declaration (Declaração do Atributo ValidateSet)

O atributo de ValidateSetAttribute Especifica um conjunto de valores possíveis para um argumento do parâmetro de cmdlet. Este atributo também pode ser utilizado por funções do Windows PowerShell.

Quando esse atributo é especificado, o tempo de execução do Windows PowerShell determina se o argumento fornecido para o parâmetro de cmdlet corresponde a um elemento no conjunto de elemento fornecido. O cmdlet é executado apenas se o argumento do parâmetro corresponde a um elemento no conjunto. Se nenhuma correspondência for encontrada, é gerado um erro ao tempo de execução do Windows PowerShell.

## <a name="syntax"></a>Sintaxe

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parâmetros

`ValidValues` ([System. String](/dotnet/api/System.String)) necessária. Especifica os valores de elemento de parâmetro válido. O exemplo a seguir mostra como especificar um elemento ou em vários elementos.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter. O valor predefinido de `true` indica que o caso é ignorado. Um valor de `false` faz com que o cmdlet diferencia maiúsculas de minúsculas.

## <a name="remarks"></a>Observações

- Este atributo pode ser utilizado apenas uma vez por parâmetro.

- Se o valor do parâmetro é uma matriz, cada elemento da matriz deve coincidir com um elemento do conjunto de atributo.

- O atributo ValidateSetAttribute é definido pela [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) classe.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
