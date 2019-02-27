---
title: Aliases de parâmetro | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844934"
---
# <a name="parameter-aliases"></a>Parameter Aliases (Aliases de Parâmetros)

Os parâmetros de cmdlet também podem ter aliases. Pode utilizar os aliases em vez dos nomes de parâmetros, quando escreve ou especificar o parâmetro num comando.

## <a name="benefits-of-using-aliases"></a>Vantagens da utilização de Aliases

Adicionar aliases para parâmetros fornece as seguintes vantagens.

- Pode fornecer um atalho para que o utilizador não tem de utilizar o nome do parâmetro completo quando o cmdlet é chamado. Por exemplo, poderia usar o alias "CN" em vez do nome de parâmetro "ComputerName".

- Se quiser fornecer nomes diferentes para o mesmo parâmetro, pode definir vários aliases. Pode querer definir vários aliases, se tem que trabalhar com vários grupos de utilizadores que se referem aos mesmos dados de formas diferentes.

- Pode proporcionar compatibilidade para os scripts existentes se mudar o nome de um parâmetro.

- Ao utilizar o atributo de Alias, juntamente com o atributo ValueFromPipelineByName, pode definir um parâmetro que permite seu cmdlet vincular a diferentes tipos de objeto. Por exemplo, digamos que tinha dois objetos de diferentes tipos e o primeiro objeto tinha uma propriedade de escritor e o segundo objeto tinha uma propriedade de editor. Se seu cmdlet tinha um parâmetro que tiveram aliases de escritor e editor e o cmdlet aceitaram entrada do pipeline com base em nomes de propriedade, seu cmdlet poderia vincular-se os dois objetos usando os dois aliases de parâmetro.

Para obter mais informações sobre os aliases que pode ser utilizado com parâmetros específicos, consulte [nomes de parâmetros comuns](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Definir Aliases de parâmetro

Para definir um alias para um parâmetro, declare o atributo de Alias, como mostra a seguinte declaração de parâmetro. Neste exemplo, vários aliases são definidas para o mesmo parâmetro. (Para obter mais informações, consulte[como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).)

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>Consulte Também

[Nomes de parâmetros comuns](./common-parameter-names.md)

[Como declarar parâmetros do Cmdlet](./how-to-declare-cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
