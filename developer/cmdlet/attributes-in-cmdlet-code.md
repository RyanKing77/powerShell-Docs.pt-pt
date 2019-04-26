---
title: Atributos no código de Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068692"
---
# <a name="attributes-in-cmdlet-code"></a>Attributes in Cmdlet Code (Atributos no Código Cmdlet)

Para utilizar a funcionalidade comum fornecida pelo Windows PowerShell, as classes e propriedades públicas definidas no código cmdlet são decoradas com atributos. Por exemplo, a seguinte definição de classe usa o atributo de Cmdlet para identificar a classe do Microsoft .NET Framework em que o **Get-Proc** cmdlet é implementado. (Este cmdlet é utilizado como um exemplo neste documento e é semelhante a `Get-Process` cmdlet fornecido pelo Windows PowerShell.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Esses atributos são considerados os metadados porque a sua implementação é separada da implementação do código de cmdlet. Quando o tempo de execução do Windows PowerShell é executado o cmdlet, ele reconhece os atributos e, em seguida, executa a ação apropriada para cada atributo.

Embora pode querer implementar sua própria versão da funcionalidade fornecida por esses atributos, a estrutura de um cmdlet boa utiliza essas funcionalidades comuns.

Para obter mais informações sobre os atributos diferentes que pode ser declarado nos seus cmdlets, consulte [tipos de atributo](./attribute-types.md).

## <a name="see-also"></a>Veja Também

[Tipos de atributos](./attribute-types.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
