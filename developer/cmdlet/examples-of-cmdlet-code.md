---
title: Exemplos de código de Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056265"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="fe6e7-102">Examples of Cmdlet Code (Exemplos de Código Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="fe6e7-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="fe6e7-103">Esta seção contém exemplos de código de cmdlet que pode usar para começar a escrever seus próprios cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fe6e7-104">Se pretender que as instruções passo a passo para a escrita de cmdlets, consulte [tutoriais para escrever Cmdlets](./tutorials-for-writing-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="fe6e7-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fe6e7-105">Nesta Secção</span><span class="sxs-lookup"><span data-stu-id="fe6e7-105">In This Section</span></span>

<span data-ttu-id="fe6e7-106">[Como escrever um simples Cmdlet](./how-to-write-a-simple-cmdlet.md) este exemplo mostra a estrutura básica do código de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="fe6e7-107">[Como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md) este exemplo mostra como declarar os diferentes tipos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="fe6e7-108">[Como declarar define o parâmetro](./how-to-declare-parameter-sets.md) este exemplo mostra como declarar os conjuntos de parâmetros que podem alterar a ação que executa um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="fe6e7-109">[Como validar parâmetro de entrada](./how-to-validate-parameter-input.md) estes exemplos mostram como validar a entrada de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="fe6e7-110">[Como declarar parâmetros dinâmicos](./how-to-declare-dynamic-parameters.md) este exemplo mostra como declarar um parâmetro que é adicionado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="fe6e7-111">[Como invocar Scripts dentro de um Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) este exemplo mostra como invocar um script que é fornecido a um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="fe6e7-112">[Como substituir os métodos de processamento de entrada](./how-to-override-input-processing-methods.md) estes exemplos mostram a estrutura básica utilizada para substituir os métodos de BeginProcessing, ProcessRecord e EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="fe6e7-113">[Como suporte a chamadas para ShouldProcess](./how-to-request-confirmations.md) este exemplo mostra como o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos devem ser chamados a partir de dentro de um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="fe6e7-114">[Como suporte a transações](./how-to-support-transactions.md) este exemplo mostra como indicar que o cmdlet oferece suporte a transações e como implementar a ação que é executada quando o cmdlet é utilizado numa transação.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="fe6e7-115">[Como suportar tarefas](./how-to-support-jobs.md) este exemplo mostra como suportar tarefas quando escreve cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="fe6e7-116">[Como invocar um Cmdlet de dentro de um Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) este exemplo mostra como invocar um cmdlet a partir de outro cmdlet, o que permite-lhe adicionar a funcionalidade do cmdlet invocado para o cmdlet que está a desenvolver.</span><span class="sxs-lookup"><span data-stu-id="fe6e7-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe6e7-117">Veja Também</span><span class="sxs-lookup"><span data-stu-id="fe6e7-117">See Also</span></span>

[<span data-ttu-id="fe6e7-118">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe6e7-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
