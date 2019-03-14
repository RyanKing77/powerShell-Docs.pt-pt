---
title: Declaração de atributo ValidateCount | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794451"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount Attribute Declaration (Declaração do Atributo ValidateCount)

O atributo de ValidateCount Especifica o número mínimo e máximo de argumentos permitido para um parâmetro de cmdlet.

## <a name="syntax"></a>Sintaxe

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parâmetros

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required. Especifica o número mínimo de argumentos.

`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required. Especifica o número máximo de argumentos.

## <a name="remarks"></a>Observações

- Para obter mais informações sobre como declarar este atributo, consulte [como as regras de validação de entrada declarar](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- Quando esse atributo não é invocado, o parâmetro de cmdlet correspondente pode ter qualquer número de argumentos.

- O tempo de execução do Windows PowerShell emite um erro nas seguintes condições:

    - O `MinLength` e `MaxLength` parâmetros de atributo não são do tipo [System.Int32](/dotnet/api/System.Int32).

    - O valor do `MaxLength` parametr atributu é inferior ao valor da `MinLength` atributo de parâmetro.

- O atributo ValidateCount é definido pela [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) classe.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[Como declarar as regras de validação de entrada](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
