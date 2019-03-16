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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054412"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="929b0-102">Error Reporting Concepts (Conceitos de Comunicação de Erros)</span><span class="sxs-lookup"><span data-stu-id="929b0-102">Error Reporting Concepts</span></span>

<span data-ttu-id="929b0-103">Windows PowerShell fornece dois mecanismos para o relatório de erros: um mecanismo para *erros de terminação* e de outro mecanismo para *erros de não terminação*.</span><span class="sxs-lookup"><span data-stu-id="929b0-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="929b0-104">É importante que seu cmdlet para relatar erros corretamente para que o aplicativo de host que está a executar os cmdlets pode reagir de forma apropriada.</span><span class="sxs-lookup"><span data-stu-id="929b0-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="929b0-105">O cmdlet deve chamar o [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método quando ocorre um erro que não existir ou não deve permitir que o cmdlet para continuar a processar os seus objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="929b0-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="929b0-106">O cmdlet deve chamar o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método para reportar erros de não terminação, quando o cmdlet pode continuar a processar os objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="929b0-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="929b0-107">Ambos os métodos fornecem um registo de erro que o aplicativo host pode usar para investigar a causa do erro.</span><span class="sxs-lookup"><span data-stu-id="929b0-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="929b0-108">Utilize as seguintes diretrizes para determinar se o erro é a acabar ou erro de não terminação.</span><span class="sxs-lookup"><span data-stu-id="929b0-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="929b0-109">Um erro é um erro de terminação se impede que seu cmdlet de continuar a processar o objeto atual ou de processamento com êxito todos os objetos ainda mais a entrada, independentemente do seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="929b0-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="929b0-110">Um erro é um erro de terminação, se não pretender que seu cmdlet para continuar a processar o objeto atual ou qualquer objeto ainda mais a entrada, independentemente do seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="929b0-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="929b0-111">Um erro é um erro de terminação se ocorra num cmdlet que não aceita ou retorna um objeto ou se ocorra num cmdlet que aceita ou retorna apenas um objeto.</span><span class="sxs-lookup"><span data-stu-id="929b0-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="929b0-112">Um erro é um erro de não terminação, se quiser que o seu cmdlet continuar a processar o objeto atual e quaisquer objetos de entrada ainda mais.</span><span class="sxs-lookup"><span data-stu-id="929b0-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="929b0-113">Um erro é um erro de não terminação, se ele está relacionado a um objeto de entrada específico ou um subconjunto de objetos de entrada.</span><span class="sxs-lookup"><span data-stu-id="929b0-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="929b0-114">Veja Também</span><span class="sxs-lookup"><span data-stu-id="929b0-114">See Also</span></span>

[<span data-ttu-id="929b0-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="929b0-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="929b0-116">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="929b0-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="929b0-117">Registos de erro do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="929b0-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="929b0-118">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="929b0-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
