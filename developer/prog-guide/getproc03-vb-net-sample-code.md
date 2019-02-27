---
title: GetProc03 código de exemplo (VB.NET) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: da85155c43471150a7b35ac37c1dce0790277084
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845858"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03 (VB.NET) Sample Code (Código de Exemplo GetProc03 [VB.NET])

O código a seguir mostra a implementação de um `Get-Process` pipelined de cmdlet que pode aceitar entrada. Essa implementação define um `Name` parâmetro que aceita entrada do pipeline, obtém informações de processo a partir do computador local com base nos nomes fornecidos e, em seguida, utiliza o [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como o mecanismo de saída para o envio de objetos para o pipeline.

## <a name="code-sample"></a>Exemplo de código

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->