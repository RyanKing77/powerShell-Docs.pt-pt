---
title: Como suporte a transações | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067863"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="f549b-102">How to Support Transactions (Como Suportar Transações)</span><span class="sxs-lookup"><span data-stu-id="f549b-102">How to Support Transactions</span></span>

<span data-ttu-id="f549b-103">Este exemplo mostra os elementos de código básico que adicionar suporte para transações para um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f549b-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f549b-104">Para obter mais informações sobre como o Windows PowerShell manipula transações, consulte [sobre transações][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="f549b-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="f549b-105">Para oferecer suporte a transações</span><span class="sxs-lookup"><span data-stu-id="f549b-105">To support transactions</span></span>

1. <span data-ttu-id="f549b-106">Quando declara o atributo de Cmdlet, especifica que o cmdlet oferece suporte a transações.</span><span class="sxs-lookup"><span data-stu-id="f549b-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="f549b-107">Quando o cmdlet oferece suporte a transações, o Windows PowerShell adiciona o `UseTransaction` parâmetro para o cmdlet quando é executada.</span><span class="sxs-lookup"><span data-stu-id="f549b-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="f549b-108">Dentro da entrada de métodos de processamento, adicionar um `if` bloco para determinar se uma transação está disponível.</span><span class="sxs-lookup"><span data-stu-id="f549b-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="f549b-109">Se o `if` instrução é resolvido para `true`, as ações esta instrução podem ser executadas dentro do contexto da transação atual.</span><span class="sxs-lookup"><span data-stu-id="f549b-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="f549b-110">Veja Também</span><span class="sxs-lookup"><span data-stu-id="f549b-110">See Also</span></span>

[<span data-ttu-id="f549b-111">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f549b-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
