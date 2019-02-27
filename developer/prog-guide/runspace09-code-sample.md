---
title: Exemplo de código RunSpace09 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845445"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="e7b01-102">Runspace09 Code Sample (Código de Exemplo Runspace09)</span><span class="sxs-lookup"><span data-stu-id="e7b01-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="e7b01-103">Eis o código-fonte para o exemplo de Runspace09 descrito em [criação de uma consola de aplicação que invoca um Pipeline de forma assíncrona](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="e7b01-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="e7b01-104">Este aplicativo de exemplo cria e abre um espaço de execução, cria e assincronamente invoca um pipeline, e, em seguida, utiliza pipeline de eventos para processar o script de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="e7b01-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="e7b01-105">O script que é executado por esta aplicação cria números inteiros de 1 a 10 em intervalos de 0,5 segundo (500 ms).</span><span class="sxs-lookup"><span data-stu-id="e7b01-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="e7b01-106">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="e7b01-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="e7b01-107">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e7b01-107">See Also</span></span>

[<span data-ttu-id="e7b01-108">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7b01-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)