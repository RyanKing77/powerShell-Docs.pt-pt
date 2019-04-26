---
title: Relatório de erros do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067098"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="41023-102">Windows PowerShell Error Reporting (Comunicação de Erros do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="41023-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="41023-103">Os tópicos nesta secção descrevem como cmdlets relatar erros.</span><span class="sxs-lookup"><span data-stu-id="41023-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="41023-104">Nesta Secção</span><span class="sxs-lookup"><span data-stu-id="41023-104">In This Section</span></span>

<span data-ttu-id="41023-105">[Conceitos de relatórios de erro](./error-reporting-concepts.md) descreve os dois mecanismos que pode utilizar o cmdlets para relatar erros.</span><span class="sxs-lookup"><span data-stu-id="41023-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="41023-106">[Erros de terminação](./terminating-errors.md) descreve o método utilizado para comunicar erros, onde esse método pode ser chamado de dentro do cmdlet e as exceções que podem ser devolvidas pelo tempo de execução do Windows PowerShell, quando o método é chamado de terminação.</span><span class="sxs-lookup"><span data-stu-id="41023-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="41023-107">[Erros de não terminação](./non-terminating-errors.md) descreve o método utilizado para comunicar erros de não terminação e em que esse método pode ser chamado de dentro do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41023-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="41023-108">[Exibindo informações de erro por categoria](./displaying-error-information.md) aborda as formas que os usuários podem exibir o erro.</span><span class="sxs-lookup"><span data-stu-id="41023-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="41023-109">[Registos de erros do Windows PowerShell](./windows-powershell-error-records.md) descreve os componentes de um registo de erro.</span><span class="sxs-lookup"><span data-stu-id="41023-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="41023-110">[Interpretar os objetos de ErrorRecord](./interpreting-errorrecord-objects.md) discute como os objetos de ErrorRecord são interpretados.</span><span class="sxs-lookup"><span data-stu-id="41023-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="41023-111">Veja Também</span><span class="sxs-lookup"><span data-stu-id="41023-111">See Also</span></span>

[<span data-ttu-id="41023-112">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="41023-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
