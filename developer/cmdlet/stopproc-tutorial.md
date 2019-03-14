---
title: Tutorial de StopProc | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794404"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="37e93-102">StopProc Tutorial (Tutorial: StopProc)</span><span class="sxs-lookup"><span data-stu-id="37e93-102">StopProc Tutorial</span></span>

<span data-ttu-id="37e93-103">Esta secção fornece um tutorial para criar o cmdlet Stop-Proc, que é muito parecido com o [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet fornecido pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="37e93-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="37e93-104">Este tutorial disponibiliza os fragmentos de código que ilustram a forma como os cmdlets são implementados e uma explicação do código.</span><span class="sxs-lookup"><span data-stu-id="37e93-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="37e93-105">Tópicos neste tutorial</span><span class="sxs-lookup"><span data-stu-id="37e93-105">Topics in this Tutorial</span></span>

<span data-ttu-id="37e93-106">Os tópicos neste tutorial foram concebidos para ser lida sequencialmente, com cada tópico Criar sobre o que foi discutido no tópico anterior.</span><span class="sxs-lookup"><span data-stu-id="37e93-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="37e93-107">[Criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md) esta secção descreve como criar um cmdlet que suporta as modificações de sistema, tais como parar um processo em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="37e93-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="37e93-108">[Adicionar mensagens de utilizador ao seu Cmdlet](./adding-user-messages-to-your-cmdlet.md) esta secção descreve como adicionar a capacidade de escrever as mensagens do usuário, mensagens de depuração, mensagens de aviso e informações de progresso ao seu cmdlet.</span><span class="sxs-lookup"><span data-stu-id="37e93-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="37e93-109">[Adicionar Aliases, expansão de caráter universal e ajudar a parâmetros de Cmdlet](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) esta secção descreve como criar um cmdlet que suporta a expansão de caráter universal, ajuda e aliases de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="37e93-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="37e93-110">[Adicionar o parâmetro define aos Cmdlets de](./adding-parameter-sets-to-a-cmdlet.md) esta secção descreve como adicionar o parâmetro define como um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="37e93-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="37e93-111">Conjuntos de parâmetros permitem que o cmdlet para operar diferente com base nos quais os parâmetros são especificados pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="37e93-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="37e93-112">Veja Também</span><span class="sxs-lookup"><span data-stu-id="37e93-112">See Also</span></span>

[<span data-ttu-id="37e93-113">Criar um Cmdlet que modifica o sistema</span><span class="sxs-lookup"><span data-stu-id="37e93-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="37e93-114">Adicionar mensagens de utilizador ao seu Cmdlet</span><span class="sxs-lookup"><span data-stu-id="37e93-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="37e93-115">Adicionar Aliases, expansão de caráter universal e ajudar a parâmetros do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="37e93-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="37e93-116">Adicionar parâmetro define como Cmdlets</span><span class="sxs-lookup"><span data-stu-id="37e93-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="37e93-117">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="37e93-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
