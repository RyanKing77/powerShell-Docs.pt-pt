---
title: Declaração de atributo OutputType | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845214"
---
# <a name="outputtype-attribute-declaration"></a>OutputType Attribute Declaration (Declaração do Atributo OutputType)

O `OutputType` atributo identifica os tipos do .NET Framework devolvidos pelo cmdlet, função ou script.

## <a name="syntax"></a>Sintaxe

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parâmetros

Tipo (`string[]` ou `Type[]`) necessária. Especifica os tipos devolvidos pelo cmdlet função ou script.

ParameterSetName (string[]) opcional. Especifica os conjuntos de parâmetros que retornam tipos especificados no `type` parâmetro.

providerCmdlet opcional. Especifica o cmdlet de fornecedor que retorna os tipos especificados no `type` parâmetro.

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
