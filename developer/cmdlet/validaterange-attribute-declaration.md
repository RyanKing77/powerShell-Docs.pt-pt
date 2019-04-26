---
title: Declaração de atributo ValidateRange | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067115"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange Attribute Declaration (Declaração do Atributo ValidateRange)

O atributo de ValidateRange Especifica os valores mínimos e máximo (o intervalo) para o argumento do parâmetro de cmdlet. Este atributo também pode ser utilizado por funções do Windows PowerShell.

## <a name="syntax"></a>Sintaxe

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parâmetros

`MinRange` ([System. Object](/dotnet/api/system.object)) necessária. Especifica o valor mínimo permitido.

`MaxRange` ([System. Object](/dotnet/api/system.object)) necessária. Especifica o valor máximo permitido.

## <a name="remarks"></a>Observações

- O tempo de execução do Windows PowerShell gera um erro de construção quando o valor do `MinRange` parâmetro é superior ao valor da `MaxRange` parâmetro.

- O tempo de execução do Windows PowerShell gera um erro de validação nas seguintes condições:

    - Quando o valor do argumento é menos do que o `MinRange` limite ou maior do que o `MaxRange` limite.

    - Quando o argumento não é do mesmo tipo como o `MinRange` e o `MaxRange` parâmetros.

- O atributo ValidateRange é definido pela [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) classe.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
