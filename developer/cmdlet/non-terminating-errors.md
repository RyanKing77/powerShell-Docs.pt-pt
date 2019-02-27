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
# <a name="non-terminating-errors"></a><span data-ttu-id="ae7c7-102">Non-Terminating Errors (Erros de Não Terminação)</span><span class="sxs-lookup"><span data-stu-id="ae7c7-102">Non-Terminating Errors</span></span>

<span data-ttu-id="ae7c7-103">Este tópico aborda o método utilizado para comunicar os erros de não terminação.</span><span class="sxs-lookup"><span data-stu-id="ae7c7-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="ae7c7-104">Ele também aborda como chamar o método a partir do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae7c7-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="ae7c7-105">Quando ocorre um erro de não terminação, o cmdlet deve comunique este problema ao chamar o [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método.</span><span class="sxs-lookup"><span data-stu-id="ae7c7-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="ae7c7-106">Quando o cmdlet comunica um erro de não terminação, o cmdlet pode continuar a funcionar neste objeto de entrada e de entrada mais objetos do pipeline.</span><span class="sxs-lookup"><span data-stu-id="ae7c7-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="ae7c7-107">Se o cmdlet chama o [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método, o cmdlet pode escrever um registo de erro que descreve a condição que causou o erro de não terminação.</span><span class="sxs-lookup"><span data-stu-id="ae7c7-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="ae7c7-108">Para obter mais informações sobre os registos de erro, consulte [registos de erros do Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="ae7c7-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="ae7c7-109">Pode chamar cmdlets [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) como necessário a partir de dentro de seus métodos de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="ae7c7-109">Cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="ae7c7-110">No entanto, pode chamar cmdlets [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) apenas a partir do thread que chamou a [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="ae7c7-110">However, cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="ae7c7-111">Não chamar [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) de outro thread.</span><span class="sxs-lookup"><span data-stu-id="ae7c7-111">Do not call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="ae7c7-112">Em vez disso, se comunica erros de volta para o thread principal.</span><span class="sxs-lookup"><span data-stu-id="ae7c7-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae7c7-113">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ae7c7-113">See Also</span></span>

[<span data-ttu-id="ae7c7-114">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="ae7c7-114">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="ae7c7-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="ae7c7-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="ae7c7-116">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="ae7c7-116">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="ae7c7-117">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="ae7c7-117">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="ae7c7-118">Registos de erro do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="ae7c7-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="ae7c7-119">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae7c7-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
