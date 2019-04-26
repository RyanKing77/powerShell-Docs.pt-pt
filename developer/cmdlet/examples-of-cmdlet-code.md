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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068203"
---
# <a name="examples-of-cmdlet-code"></a>Examples of Cmdlet Code (Exemplos de Código Cmdlet)

Esta seção contém exemplos de código de cmdlet que pode usar para começar a escrever seus próprios cmdlets.

> [!IMPORTANT]
> Se pretender que as instruções passo a passo para a escrita de cmdlets, consulte [tutoriais para escrever Cmdlets](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>Nesta Secção

[Como escrever um simples Cmdlet](./how-to-write-a-simple-cmdlet.md) este exemplo mostra a estrutura básica do código de cmdlet.

[Como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md) este exemplo mostra como declarar os diferentes tipos de parâmetros.

[Como declarar define o parâmetro](./how-to-declare-parameter-sets.md) este exemplo mostra como declarar os conjuntos de parâmetros que podem alterar a ação que executa um cmdlet.

[Como validar parâmetro de entrada](./how-to-validate-parameter-input.md) estes exemplos mostram como validar a entrada de parâmetro.

[Como declarar parâmetros dinâmicos](./how-to-declare-dynamic-parameters.md) este exemplo mostra como declarar um parâmetro que é adicionado em tempo de execução.

[Como invocar Scripts dentro de um Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) este exemplo mostra como invocar um script que é fornecido a um cmdlet.

[Como substituir os métodos de processamento de entrada](./how-to-override-input-processing-methods.md) estes exemplos mostram a estrutura básica utilizada para substituir os métodos de BeginProcessing, ProcessRecord e EndProcessing.

[Como suporte a chamadas para ShouldProcess](./how-to-request-confirmations.md) este exemplo mostra como o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos devem ser chamados a partir de dentro de um cmdlet.

[Como suporte a transações](./how-to-support-transactions.md) este exemplo mostra como indicar que o cmdlet oferece suporte a transações e como implementar a ação que é executada quando o cmdlet é utilizado numa transação.

[Como suportar tarefas](./how-to-support-jobs.md) este exemplo mostra como suportar tarefas quando escreve cmdlets.

[Como invocar um Cmdlet de dentro de um Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) este exemplo mostra como invocar um cmdlet a partir de outro cmdlet, o que permite-lhe adicionar a funcionalidade do cmdlet invocado para o cmdlet que está a desenvolver.

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
