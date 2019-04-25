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
ms.openlocfilehash: 0cfb5c203c97a4d20e7fadf8183e608e9e31b881
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081653"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="1ddbd-102">GetProc03 (VB.NET) Sample Code (Código de Exemplo GetProc03 [VB.NET])</span><span class="sxs-lookup"><span data-stu-id="1ddbd-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="1ddbd-103">O código a seguir mostra a implementação de um `Get-Process` pipelined de cmdlet que pode aceitar entrada.</span><span class="sxs-lookup"><span data-stu-id="1ddbd-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="1ddbd-104">Essa implementação define um `Name` parâmetro que aceita entrada do pipeline, obtém informações de processo a partir do computador local com base nos nomes fornecidos e, em seguida, utiliza o [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como o mecanismo de saída para o envio de objetos para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="1ddbd-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1ddbd-105">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="1ddbd-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->