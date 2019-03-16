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
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054362"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="abd27-102">Non-Terminating Errors (Erros de Não Terminação)</span><span class="sxs-lookup"><span data-stu-id="abd27-102">Non-Terminating Errors</span></span>

<span data-ttu-id="abd27-103">Este tópico aborda o método utilizado para comunicar os erros de não terminação.</span><span class="sxs-lookup"><span data-stu-id="abd27-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="abd27-104">Ele também aborda como chamar o método a partir do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="abd27-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="abd27-105">Quando ocorre um erro de não terminação, o cmdlet deve comunique este problema ao chamar o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método.</span><span class="sxs-lookup"><span data-stu-id="abd27-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="abd27-106">Quando o cmdlet comunica um erro de não terminação, o cmdlet pode continuar a funcionar neste objeto de entrada e de entrada mais objetos do pipeline.</span><span class="sxs-lookup"><span data-stu-id="abd27-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="abd27-107">Se o cmdlet chama o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método, o cmdlet pode escrever um registo de erro que descreve a condição que causou o erro de não terminação.</span><span class="sxs-lookup"><span data-stu-id="abd27-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="abd27-108">Para obter mais informações sobre os registos de erro, consulte [registos de erros do Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="abd27-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="abd27-109">Pode chamar cmdlets [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) como necessário a partir de dentro de seus métodos de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="abd27-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="abd27-110">No entanto, pode chamar cmdlets [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) apenas a partir do thread que chamou a [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="abd27-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="abd27-111">Não chamar [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) de outro thread.</span><span class="sxs-lookup"><span data-stu-id="abd27-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="abd27-112">Em vez disso, se comunica erros de volta para o thread principal.</span><span class="sxs-lookup"><span data-stu-id="abd27-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="abd27-113">Veja Também</span><span class="sxs-lookup"><span data-stu-id="abd27-113">See Also</span></span>

[<span data-ttu-id="abd27-114">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="abd27-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="abd27-115">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="abd27-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="abd27-116">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="abd27-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="abd27-117">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="abd27-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="abd27-118">Registos de erro do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="abd27-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="abd27-119">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="abd27-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
