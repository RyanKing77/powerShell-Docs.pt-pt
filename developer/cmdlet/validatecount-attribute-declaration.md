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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983903"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount Attribute Declaration (Declaração do Atributo ValidateCount)

O atributo de ValidateCount Especifica o número mínimo e máximo de argumentos permitido para um parâmetro de cmdlet.

## <a name="syntax"></a>Sintaxe

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parâmetros

`MinLength` ([System.Int32][]) Required. Especifica o número mínimo de argumentos.

`MaxLength`([System.Int32][]) Required. Especifica o número máximo de argumentos.

## <a name="remarks"></a>Observações

- Para obter mais informações sobre como declarar este atributo, consulte [Como validar uma contagem de argumentos][].

- Quando esse atributo não é invocado, o parâmetro de cmdlet correspondente pode ter qualquer número de argumentos.

- O tempo de execução do Windows PowerShell emite um erro nas seguintes condições:

    - O `MinLength` e `MaxLength` parâmetros de atributo não são do tipo [System.Int32][].

    - O valor do `MaxLength` parametr atributu é inferior ao valor da `MinLength` atributo de parâmetro.

- O atributo ValidateCount é definido pela [System.Management.Automation.ValidateCountAttribute][] classe.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.ValidateCountAttribute][]

[Como validar uma contagem de argumentos][]

[Escrever um Cmdlet do Windows PowerShell][]

[Como validar uma contagem de argumentos]: how-to-validate-an-argument-count.md
[Escrever um Cmdlet do Windows PowerShell]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
