---
title: Erros de não terminação | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 9d5c9b16fc5daf3d2f753eeeeedb0db925551a67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845256"
---
# <a name="non-terminating-errors"></a>Non-Terminating Errors (Erros de Não Terminação)

Este tópico aborda o método utilizado para comunicar os erros de não terminação. Ele também aborda como chamar o método a partir do cmdlet.

Quando ocorre um erro de não terminação, o cmdlet deve comunique este problema ao chamar o [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método. Quando o cmdlet comunica um erro de não terminação, o cmdlet pode continuar a funcionar neste objeto de entrada e de entrada mais objetos do pipeline. Se o cmdlet chama o [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método, o cmdlet pode escrever um registo de erro que descreve a condição que causou o erro de não terminação. Para obter mais informações sobre os registos de erro, consulte [registos de erros do Windows PowerShell](./windows-powershell-error-records.md).

Pode chamar cmdlets [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) como necessário a partir de dentro de seus métodos de processamento de entrada. No entanto, pode chamar cmdlets [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) apenas a partir do thread que chamou a [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método de processamento de entrada. Não chamar [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) de outro thread. Em vez disso, se comunica erros de volta para o thread principal.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Registos de erro do PowerShell do Windows](./windows-powershell-error-records.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
