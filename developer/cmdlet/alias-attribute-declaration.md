---
title: Declaração de atributo de alias | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846145"
---
# <a name="alias-attribute-declaration"></a>Alias Attribute Declaration (Declaração do Atributo Alias)

O atributo de Alias permite que o usuário Especifique nomes diferentes para um parâmetro de cmdlet. Aliases que podem ser utilizados para fornecer os atalhos para um nome de parâmetro ou podem fornecer nomes diferentes que são adequados para diferentes cenários.

## <a name="syntax"></a>Sintaxe

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parâmetros

`aliasName` (String[]) É necessário. Especifica um conjunto de nomes de alias separados por vírgulas para o parâmetro de cmdlet.

## <a name="remarks"></a>Observações

- O atributo de Alias é utilizado com o atributo de parâmetro ao especificar um parâmetro de cmdlet. Para obter mais informações sobre como declarar esses atributos, consulte [como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).

- Cada nome de alias têm de ser exclusivo dentro de um cmdlet. Windows PowerShell não verifica se os nomes de alias duplicado.

- O atributo de Alias é utilizado uma vez para cada parâmetro num cmdlet.

- O atributo de Alias é definido pela [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) classe.

## <a name="see-also"></a>Consulte Também

[Aliases de parâmetro](./parameter-aliases.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
