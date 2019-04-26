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
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068237"
---
# <a name="date-and-time-parameters"></a>Date and Time Parameters (Parâmetros de Data e Hora)

A tabela seguinte apresenta uma lista de nomes recomendados e funcionalidades para os parâmetros que lidam com informações de data e hora. Parâmetros de data e hora são normalmente utilizados para registrar quando algo é criado ou acessado.

|Parâmetro|Funcionalidade|
|---|---|
|**Accessed**<br>Tipo de dados: SwitchParameter|Implementar este parâmetro, de modo que quando é especificado o cmdlet irá operar nos recursos que foram acessados com base na data e hora especificada pelos **antes de** e **após** parâmetros. Se este parâmetro for especificado, o **Created** e **modificado** parâmetros têm de não ser especificado.|
|**Depois de**<br>Tipo de dados: DateTime|Implemente este parâmetro para especificar a data e hora após o qual foi utilizado o cmdlet. Para o **após** parâmetro para trabalhar, o cmdlet também tem de ter um **Accessed**, **criado**, ou **modificado** parâmetro. E, esse parâmetro deve ser definido como **true** quando o cmdlet é chamado.|
|**Antes de**<br>Tipo de dados: DateTime|Implemente este parâmetro para especificar a data e hora antes do qual foi utilizado o cmdlet. Para o **antes de** parâmetro para trabalhar, o cmdlet também tem de ter um **Accessed**, **criado**, ou **modificado** parâmetro. E, esse parâmetro deve ser definido como **true** quando o cmdlet é chamado.|
|**Criado**<br>Tipo de dados: SwitchParameter|Implementar este parâmetro, de modo que quando é especificado o cmdlet irá operar nos recursos que foram criados com base na data e hora especificada pelos **antes de** e **após** parâmetros. Se este parâmetro for especificado, o **Accessed** e **modificado** parâmetros não pode ser especificados.|
|**Exact**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro, de modo que quando é especificado o termo de recursos tem de corresponder ao nome do recurso exatamente. Quando o parâmetro não for especificado o termo de recursos e o nome não têm de corresponder exatamente.|
|**Modificado**<br>Tipo de dados: DateTime|Implementar este parâmetro, de modo que quando é especificado o cmdlet irá operar em recursos que foram alterados com base na data e hora especificada pelos **antes de** e **após** parâmetros. Se este parâmetro for especificado, o **Accessed** e **Created** parâmetros não pode ser especificados.|
## <a name="see-also"></a>Veja Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
