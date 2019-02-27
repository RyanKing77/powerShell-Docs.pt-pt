---
title: Tutorial de GetProc | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851332"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="485bd-102">GetProc Tutorial (Tutorial: GetProc)</span><span class="sxs-lookup"><span data-stu-id="485bd-102">GetProc Tutorial</span></span>

<span data-ttu-id="485bd-103">Esta secção fornece um tutorial para criar um cmdlet de Get-Proc que é muito parecido com o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet fornecido pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="485bd-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="485bd-104">Este tutorial disponibiliza os fragmentos de código que ilustram a forma como os cmdlets são implementados e uma explicação do código.</span><span class="sxs-lookup"><span data-stu-id="485bd-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="485bd-105">Tópicos neste tutorial</span><span class="sxs-lookup"><span data-stu-id="485bd-105">Topics in this Tutorial</span></span>

<span data-ttu-id="485bd-106">Os tópicos neste tutorial foram concebidos para ser lida sequencialmente, com cada tópico Criar sobre o que foi discutido no tópico anterior.</span><span class="sxs-lookup"><span data-stu-id="485bd-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="485bd-107">[Criação de um Cmdlet sem parâmetros](./creating-a-cmdlet-without-parameters.md) esta secção descreve como criar um cmdlet que obtém informações do computador local sem o uso de parâmetros e, em seguida, escreve as informações para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="485bd-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="485bd-108">[Adicionar parâmetros de entrada de linha de comandos desse processo](./adding-parameters-that-process-command-line-input.md) esta secção descreve como adicionar um parâmetro para o cmdlet Get-Proc para que o cmdlet pode processar a entrada com base nos objetos explícitos transferidos para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="485bd-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="485bd-109">A implementação descrita aqui obtém processos com base no respetivo nome e, em seguida, escreve as informações para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="485bd-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="485bd-110">[Adicionar parâmetros de entrada do Pipeline esse processo](./adding-parameters-that-process-pipeline-input.md) esta secção descreve como adicionar um parâmetro para o cmdlet Get-Proc para que o cmdlet pode processar objetos passados para ele através do pipeline.</span><span class="sxs-lookup"><span data-stu-id="485bd-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="485bd-111">O cmdlet de implementação descrito aqui obtém processos com base nos objetos passados para o cmdlet e, em seguida, escreve as informações para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="485bd-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="485bd-112">[Adicionar um relatório de erros de não terminação ao seu Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) esta secção descreve como adicionar relatórios para um cmdlet de erros de não terminação.</span><span class="sxs-lookup"><span data-stu-id="485bd-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="485bd-113">A implementação descrita aqui Deteta erros de não terminação que ocorrem durante o processamento de entrada e grava um registo de erro no fluxo de erro.</span><span class="sxs-lookup"><span data-stu-id="485bd-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="485bd-114">Veja Também</span><span class="sxs-lookup"><span data-stu-id="485bd-114">See Also</span></span>

[<span data-ttu-id="485bd-115">Criação de um Cmdlet sem parâmetros</span><span class="sxs-lookup"><span data-stu-id="485bd-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="485bd-116">Adicionar parâmetros que processam a entrada da linha de comandos</span><span class="sxs-lookup"><span data-stu-id="485bd-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="485bd-117">Adicionar parâmetros do que a entrada de Pipeline de processo</span><span class="sxs-lookup"><span data-stu-id="485bd-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="485bd-118">Adicionar ao seu Cmdlet do relatório de erros de não terminação</span><span class="sxs-lookup"><span data-stu-id="485bd-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="485bd-119">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="485bd-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
