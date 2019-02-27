---
title: Módulos e Snap-ins | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849960"
---
# <a name="modules-and-snap-ins"></a>Modules and Snap-ins (Módulos e Snap-ins)

Cmdlets podem ser adicionados a uma sessão através de módulos (introduzidos pelo Windows PowerShell 2.0) ou do snap-ins. Assim que o cmdlet é adicionado à sessão que pode ser executado por meio de programação por um aplicativo host ou interativamente na linha de comandos.

Recomendamos que utilize módulos como o método de entrega para a adição de cmdlets para uma sessão pelos seguintes motivos:

- Módulos permitem que adicione cmdlets ao carregar o assembly onde o cmdlet é definido. Não é necessário implementar uma classe de snap-in.

- Módulos permitem-lhe adicionar outros recursos, como variáveis, funções, scripts, tipos e formatação ficheiros e muito mais.

- Snap-ins pode ser utilizados apenas para adicionar os cmdlets e provedores à sessão.

## <a name="see-also"></a>Consulte Também

[Escrever um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
