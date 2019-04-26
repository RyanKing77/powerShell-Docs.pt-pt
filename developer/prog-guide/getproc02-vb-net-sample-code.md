---
title: GetProc02 código de exemplo (VB.NET) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 821d0dd327529614322e446bfb30d128d1b6a7f3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081599"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="8f6dd-102">GetProc02 (VB.NET) Sample Code (Código de Exemplo GetProc02 [VB.NET])</span><span class="sxs-lookup"><span data-stu-id="8f6dd-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="8f6dd-103">O código a seguir mostra a implementação de um `Get-Process` cmdlet que aceita a entrada de linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="8f6dd-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="8f6dd-104">Tenha em atenção que esta implementação define um `Name` utiliza o parâmetro para permitir a entrada da linha de comandos e o [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como a saída objetos do mecanismo de envio de saída no pipeline.</span><span class="sxs-lookup"><span data-stu-id="8f6dd-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8f6dd-105">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="8f6dd-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="8f6dd-106">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8f6dd-106">See Also</span></span>

[<span data-ttu-id="8f6dd-107">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f6dd-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)