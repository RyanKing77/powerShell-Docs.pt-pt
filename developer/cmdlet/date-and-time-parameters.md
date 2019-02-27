---
title: Data e hora parâmetros | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 49f6c667b0fd9678586559af39a33f982de0a68c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846712"
---
# <a name="date-and-time-parameters"></a>Date and Time Parameters (Parâmetros de Data e Hora)

A tabela seguinte apresenta uma lista de nomes recomendados e funcionalidades para os parâmetros que lidam com informações de data e hora. Parâmetros de data e hora são normalmente utilizados para registrar quando algo é criado ou acessado.

Tipo de dados acedidos: SwitchParameter

Implementar este parâmetro, de modo que quando é especificado o cmdlet irá operar nos recursos que foram acessados com base na data e hora especificada pelos `Before` e `After` parâmetros.

Se este parâmetro for especificado, o `Created` e `Modified` parâmetros têm de não ser especificado.

Depois de tipo de dados: DateTime

Implemente este parâmetro para especificar a data e hora após o qual foi utilizado o cmdlet. Para o `After` parâmetro para trabalhar, o cmdlet também tem de ter uma `Accessed`, `Created`, ou `Modified` parâmetro. E, esse parâmetro deve ser definido como `true` quando o cmdlet é chamado.

Antes de tipo de dados: DateTime

Implemente este parâmetro para especificar a data e hora antes do qual foi utilizado o cmdlet. Para o `Before` parâmetro para trabalhar, o cmdlet também tem de ter uma `Accessed`, `Created`, ou `Modified` parâmetro. E, esse parâmetro deve ser definido como `true` quando o cmdlet é chamado.

Criou o tipo de dados: SwitchParameter

Implementar este parâmetro, de modo que quando é especificado o cmdlet irá operar nos recursos que foram criados com base na data e hora especificada pelos `Before` e `After` parâmetros.

Se este parâmetro for especificado, o `Accessed` e `Modified` parâmetros não pode ser especificados.

Tipo de dados exatos: SwitchParameter

Implemente este parâmetro, de modo que quando é especificado o termo de recursos tem de corresponder ao nome do recurso exatamente. Quando o parâmetro não for especificado o termo de recursos e o nome não têm de corresponder exatamente.

Tipo de dados modificados: DateTime

Implementar este parâmetro, de modo que quando é especificado o cmdlet irá operar em recursos que foram alterados com base na data e hora especificada pelos `Before` e `After` parâmetros.

Se este parâmetro for especificado, o `Accessed` e `Created` parâmetros não pode ser especificados.

## <a name="see-also"></a>Veja Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
