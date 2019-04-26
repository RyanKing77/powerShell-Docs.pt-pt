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
# <a name="how-to-support-transactions"></a>How to Support Transactions (Como Suportar Transações)

Este exemplo mostra os elementos de código básico que adicionar suporte para transações para um cmdlet.

> [!IMPORTANT]
> Para obter mais informações sobre como o Windows PowerShell manipula transações, consulte [sobre transações][about_Transactions].

## <a name="to-support-transactions"></a>Para oferecer suporte a transações

1. Quando declara o atributo de Cmdlet, especifica que o cmdlet oferece suporte a transações.
   Quando o cmdlet oferece suporte a transações, o Windows PowerShell adiciona o `UseTransaction` parâmetro para o cmdlet quando é executada.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Dentro da entrada de métodos de processamento, adicionar um `if` bloco para determinar se uma transação está disponível.
   Se o `if` instrução é resolvido para `true`, as ações esta instrução podem ser executadas dentro do contexto da transação atual.

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
