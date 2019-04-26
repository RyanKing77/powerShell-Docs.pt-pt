---
title: Conceitos de relatório de erros | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068186"
---
# <a name="error-reporting-concepts"></a>Error Reporting Concepts (Conceitos de Comunicação de Erros)

Windows PowerShell fornece dois mecanismos para o relatório de erros: um mecanismo para *erros de terminação* e de outro mecanismo para *erros de não terminação*. É importante que seu cmdlet para relatar erros corretamente para que o aplicativo de host que está a executar os cmdlets pode reagir de forma apropriada.

O cmdlet deve chamar o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método quando ocorre um erro que não existir ou não deve permitir que o cmdlet para continuar a processar os seus objetos de entrada. O cmdlet deve chamar o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método para reportar erros de não terminação, quando o cmdlet pode continuar a processar os objetos de entrada. Ambos os métodos fornecem um registo de erro que o aplicativo host pode usar para investigar a causa do erro.

Utilize as seguintes diretrizes para determinar se o erro é a acabar ou erro de não terminação.

- Um erro é um erro de terminação se impede que seu cmdlet de continuar a processar o objeto atual ou de processamento com êxito todos os objetos ainda mais a entrada, independentemente do seu conteúdo.

- Um erro é um erro de terminação, se não pretender que seu cmdlet para continuar a processar o objeto atual ou qualquer objeto ainda mais a entrada, independentemente do seu conteúdo.

- Um erro é um erro de terminação se ocorra num cmdlet que não aceita ou retorna um objeto ou se ocorra num cmdlet que aceita ou retorna apenas um objeto.

- Um erro é um erro de não terminação, se quiser que o seu cmdlet continuar a processar o objeto atual e quaisquer objetos de entrada ainda mais.

- Um erro é um erro de não terminação, se ele está relacionado a um objeto de entrada específico ou um subconjunto de objetos de entrada.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Registos de erro do PowerShell do Windows](./windows-powershell-error-records.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
