---
title: Exibindo informações de erro | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848406"
---
# <a name="displaying-error-information"></a>Displaying Error Information (Apresentar Informações de Erros)

Este tópico aborda as formas em que os utilizadores podem apresentar informações sobre o erro.

Quando seu cmdlet encontra um erro, a apresentação das informações de erro será, por predefinição, assemelhar-se a seguinte saída de erro.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

No entanto, os utilizadores podem ver erros por categoria, definindo a `$ErrorView` variável à `"CategoryView"`. Vista de categoria apresenta informações específicas do registo de erro, em vez de uma descrição de texto livre do erro. Esta vista pode ser útil se tiver uma longa lista de erros para analisar. Na vista de categorias, a mensagem de erro anterior é apresentada da seguinte forma.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Para obter mais informações sobre as categorias de erro, consulte [registos de erros do Windows PowerShell](./windows-powershell-error-records.md).

## <a name="see-also"></a>Consulte Também

[Registos de erro do PowerShell do Windows](./windows-powershell-error-records.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
