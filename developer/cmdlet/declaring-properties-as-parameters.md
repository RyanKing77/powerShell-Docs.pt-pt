---
title: Declaração de propriedades como parâmetros | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850576"
---
# <a name="declaring-properties-as-parameters"></a>Declaring Properties as Parameters (Declarar Propriedades como Parâmetros)

Este tópico fornece informações básicas, que tem de compreender antes de declarar os parâmetros de um cmdlet.

Para declarar os parâmetros de um cmdlet dentro de sua classe de cmdlet, definir as propriedades públicas que representam cada parâmetro e, em seguida, adicione um ou mais atributos de parâmetro para cada propriedade. O tempo de execução do Windows PowerShell usa os atributos de parâmetro para identificar a propriedade como um parâmetro de cmdlet. A sintaxe básica para declarar o atributo de parâmetro é `[Parameter()]`.

Eis um exemplo de uma propriedade definida como um parâmetro necessário.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Eis algumas coisas a serem lembrados sobre parâmetros.

- Um parâmetro tem de ser marcado explicitamente como público. Parâmetros que não estão marcados como padrão público para interno e não serão encontrados pelo tempo de execução do Windows PowerShell.

- Parâmetros devem ser definidos como tipos de Microsoft .NET Framework para fornecer a melhor validação de parâmetro. Por exemplo, os parâmetros que estão limitados a um valor fora de um conjunto de valores devem ser definidos como um tipo de enumeração. Parâmetros que assumem um valor de identificador de recurso uniforme (URI) devem ser do tipo [System](/dotnet/api/System.Uri).

- Evite os parâmetros de cadeia básica para propriedades de tudo, mas textos livres.

- Pode adicionar um parâmetro para qualquer número de conjuntos de parâmetros. Para obter mais informações sobre conjuntos de parâmetros, consulte [define o parâmetro de Cmdlet](./cmdlet-parameter-sets.md).

Windows PowerShell também fornece um conjunto de parâmetros comuns que estão automaticamente disponíveis para cada cmdlet. Para obter mais informações sobre estes parâmetros e seus aliases, consulte [parâmetros comuns do Cmdlet](./common-parameter-names.md).

## <a name="see-also"></a>Veja Também

[Parâmetros de cmdlet comum](./common-parameter-names.md)

[Tipos de parâmetro de Cmdlet](./types-of-cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
