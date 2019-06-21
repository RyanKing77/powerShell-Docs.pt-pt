---
title: GetProc02 (C#) o código de exemplo | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: c4e7c13ffc26980e533530965187df8563003470
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301555"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="3c877-102">GetProc02 (C#) Sample Code (Código de Exemplo GetProc02 [C#])</span><span class="sxs-lookup"><span data-stu-id="3c877-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="3c877-103">O código a seguir mostra a implementação de um `Get-Process` cmdlet que aceita a entrada de linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="3c877-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="3c877-104">Tenha em atenção que esta implementação define um `Name` utiliza o parâmetro para permitir a entrada da linha de comandos e o [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) objetos de método, como o mecanismo de saída para o envio de saída para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="3c877-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3c877-105">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="3c877-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="3c877-106">Veja Também</span><span class="sxs-lookup"><span data-stu-id="3c877-106">See Also</span></span>

[<span data-ttu-id="3c877-107">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c877-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
