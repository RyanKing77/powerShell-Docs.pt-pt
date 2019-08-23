---
title: Relatório de erros do cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986320"
---
# <a name="cmdlet-error-reporting"></a>Relatório de erros do cmdlet

Os cmdlets devem relatar erros de forma diferente, dependendo se os erros estão terminando erros ou erros de não encerramento. Erros de encerramento são erros que fazem com que o pipeline seja encerrado imediatamente ou erros que ocorrem quando não há motivo para continuar o processamento. Os erros de não encerramento são aqueles que relatam uma condição de erro atual, mas o cmdlet pode continuar processando objetos de entrada. Com erros de não encerramento, o usuário geralmente é notificado do problema, mas o cmdlet continua processando o próximo objeto de entrada.

## <a name="terminating-and-nonterminating-errors"></a>Erros de encerramento e não encerramento

As diretrizes a seguir podem ser usadas para determinar se uma condição de erro é um erro de encerramento ou de não encerramento.

- A condição de erro impede que o cmdlet processe com êxito outros objetos de entrada? Nesse caso, esse é um erro de encerramento.

- A condição de erro está relacionada a um objeto de entrada específico ou a um subconjunto de objetos de entrada? Nesse caso, esse é um erro de não encerramento.

- O cmdlet aceita vários objetos de entrada, de modo que o processamento pode ter sucesso em outro objeto de entrada? Nesse caso, esse é um erro de não encerramento.

- Os cmdlets que podem aceitar vários objetos de entrada devem decidir entre o que são erros de encerramento e de não finalização, mesmo quando uma determinada situação se aplica a apenas um único objeto de entrada.

- Os cmdlets podem receber qualquer número de objetos de entrada e enviar qualquer número de objetos de êxito ou erro antes de lançar uma exceção de encerramento. Não há nenhuma relação entre o número de objetos de entrada recebidos e o número de objetos de êxito e de erro enviados.

- Os cmdlets que podem aceitar apenas 0-1 objetos de entrada e gerar apenas 0-1 objetos de saída devem tratar erros como erros de encerramento e gerar exceções de encerramento.

## <a name="reporting-nonterminating-errors"></a>Relatando erros de não encerramento

O relatório de um erro não finalizado sempre deve ser feito dentro da implementação do cmdlet do método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , do método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ou o método de [processamento System. Management. Automation. cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) end. Esses tipos de erros são relatados chamando o método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) que, por sua vez, envia um registro de erro para o fluxo de erro.

## <a name="reporting-terminating-errors"></a>Erros de encerramento de relatórios

Os erros de encerramento são relatados pelo lançamento de exceções ou pela chamada do método [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Lembre-se de que os cmdlets também podem detectar e relançar exceções, como a **OutOfMemory**, no entanto, elas não são necessárias para relançar exceções, já que o tempo de execução do PowerShell as detectará também.

Você também pode definir suas próprias exceções para problemas específicos de sua situação ou adicionar informações adicionais a uma exceção existente usando seu registro de erro.

## <a name="error-records"></a>Registros de erro

O PowerShell descreve uma condição de erro de não finalização com objetos [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Cada objeto fornece informações de categoria de erro, um objeto de destino opcional e detalhes sobre a condição de erro.

### <a name="error-identifiers"></a>Identificadores de erro

O identificador de erro é uma cadeia de caracteres simples que identifica a condição de erro dentro do cmdlet.
O PowerShell combina esse identificador com um identificador de cmdlet para criar um identificador de erro totalmente qualificado que pode ser usado posteriormente ao filtrar fluxos de erro ou erros de log, ao responder a erros específicos ou a outras atividades específicas do usuário.

As diretrizes a seguir devem ser seguidas ao especificar identificadores de erro:

- Atribua identificadores de erro diferentes, altamente específicos, a caminhos de código diferentes. Cada caminho de código que chama [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) deve ter seu próprio identificador de erro.

- Os identificadores de erro devem ser exclusivos para os tipos de exceção CLR (Common Language Runtime) para erros de encerramento e não encerramento.

- Não altere a semântica de um identificador de erro entre versões do seu cmdlet ou provedor do PowerShell. Depois que a semântica de um identificador de erro é estabelecida, ela deve permanecer constante durante todo o ciclo de vida do seu cmdlet.

- Para erros de encerramento, use um identificador de erro exclusivo para um determinado tipo de exceção CLR. Se o tipo de exceção for alterado, use um novo identificador de erro.

- Para erros de não encerramento, use um identificador de erro específico para um objeto de entrada específico.

- Escolha o texto para o identificador que tersely corresponde ao erro que está sendo relatado. Não use espaço em branco ou pontuação.

- Não gere identificadores de erro que não sejam reproduzíveis. Por exemplo, não gere identificadores que incluam um identificador de processo. Os identificadores de erro são úteis apenas quando correspondem a identificadores que são vistos por outros usuários que estão enfrentando o mesmo problema.

### <a name="error-categories"></a>Categorias de erro

As categorias de erro são usadas para agrupar erros para o usuário. O PowerShell define essas categorias e cmdlets, e os provedores do PowerShell devem escolher entre eles ao gerar o registro de erro.

Para obter uma descrição das categorias de erro disponíveis, consulte a enumeração [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) . Em geral, você deve evitar o uso de **NOERROR**, **UndefinedError**e **erro genérico** sempre que possível.

Os usuários podem exibir erros com base na categoria quando `$ErrorView` configurados como **CategoryView**.

## <a name="see-also"></a>Consulte também

[Visão geral do cmdlet](./cmdlet-overview.md)

[Tipos de saída de cmdlet](./types-of-cmdlet-output.md)

[Referência do Windows PowerShell](../windows-powershell-reference.md)
