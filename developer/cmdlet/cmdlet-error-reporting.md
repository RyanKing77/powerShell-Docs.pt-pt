---
title: Relatório de erros de cmdlet | Documentos da Microsoft
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
ms.openlocfilehash: 7b54fc220a66a47c25b3e8cba644882d31713cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847993"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet Error Reporting (Comunicação de Erros de Cmdlets)

Cmdlets devem reportar erros de forma diferente, dependendo se os erros são de terminação erros ou erros de não terminação. Erros de terminação são os erros que fazer com que o pipeline ser terminada imediatamente ou erros que ocorrem quando não há motivo para continuar o processamento. Erros de não terminação são esses erros que indicam uma condição de erro atual, mas o cmdlet pode continuar a processar objetos de entrada. Com erros de não terminação, o utilizador, normalmente, é notificado do problema, mas o cmdlet continua a processar o objeto de entrada seguinte.

## <a name="terminating-and-nonterminating-errors"></a>Erros de não terminação e terminação

As diretrizes seguintes podem ser utilizadas para determinar se uma condição de erro é um erro de terminação ou um erro de não terminação.

- A condição de erro que seu cmdlet de processar com êxito todos os objetos ainda mais a entrada? Se assim for, isso é um erro de terminação.

- A condição de erro está relacionada a um objeto de entrada específico ou um subconjunto de objetos de entrada? Se assim for, este é um erro de não terminação.

- O cmdlet aceita vários objetos entrados, como, por exemplo que o processamento pode ter êxito em outro objeto de entrada? Se assim for, este é um erro de não terminação.

- Cmdlets que podem aceitar vários objetos de entrada devem decidir entre o que são de terminação e erros de não terminação, mesmo quando uma situação específica se aplica a apenas um único objeto de entrada.

- Cmdlets pode receber qualquer número de objetos de entrada e enviar qualquer número de objetos de sucesso ou erro antes que ocorra uma exceção de terminação. Não existe nenhuma relação entre o número de objetos de entrada recebidos e o número de objetos de êxito e erro enviada.

- Cmdlets que pode aceitar apenas 0-1 objetos de entrada e gerar apenas 0-1 de saída objetos devem tratar erros como erros de terminação e gerar exceções de terminação.

## <a name="reporting-nonterminating-errors"></a>Relatório de erros de não terminação

Os relatórios de um erro de não terminação sempre devem ser feito na implementação do cmdlet do [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método, o [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, ou o [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Esses tipos de erros são comunicados ao chamar o [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método que por sua vez envia um registo de erro para a sequência de erro.

## <a name="reporting-terminating-errors"></a>Relatório de erros de terminação

Erros de terminação são comunicados por gerar exceções ou ao chamar o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método. Lembre-se de que cmdlets também pode ser capturado e exceções, tais como OutOfMemory, no entanto, eles não são necessários para volta a lançar exceções, como o tempo de execução do Windows PowerShell irá ampará-los também.

Também pode definir seus próprios exceções para problemas específicos à sua situação, ou adicionar informações adicionais a uma exceção existente com o respetivo registo de erro.

## <a name="error-records"></a>Registos de erro

Windows PowerShell descreve uma condição de erro de não terminação através da utilização de [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objetos. Cada [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto fornece informações de categoria de erro, um objeto de destino opcional e detalhes sobre a condição de erro.

### <a name="error-identifiers"></a>Identificadores de erro

O identificador de erro é uma cadeia de caracteres que identifica a condição de erro no cmdlet. Windows PowerShell combina este identificador com um identificador de cmdlet para criar um identificador de erro completamente qualificado que pode ser utilizado mais tarde, ao filtrar os fluxos de erro ou erros de registo, ao responder a erros específicos, ou com outras atividades específicas do usuário.

Devem ser seguidas as seguintes diretrizes ao especificar os identificadores de erro.

- Atribua identificadores de erro diferentes, altamente específicas a diferentes caminhos de código. Cada caminho de código que chama [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) deve ter seu próprio identificador de erro.

- Identificadores de erro devem ser exclusivos para tipos de exceções de CLR para erros de terminação e de não terminação.

- Não altere a semântica de um identificador de erro entre versões do seu cmdlet ou o fornecedor de Windows PowerShell. Depois da semântica de um identificador de erro é estabelecida, devem permanecer constante ao longo do ciclo de vida de seu cmdlet.

- Para erros de terminação, utilize um identificador exclusivo de erro para um determinado tipo de exceção do CLR. Se alterar o tipo de exceção, utilize um novo identificador de erro.

- Para erros de não terminação, utilize um identificador de erro específico para um objeto de entrada específico.

- Escolha o texto para o identificador que tersely corresponde ao erro está a ser comunicado. Não utilize espaços em branco ou pontuação.

- Não geram identificadores de erro que não são reproduzíveis. Por exemplo, não geram identificadores que incluem um identificador de processo. Identificadores de erro são úteis apenas quando eles correspondem aos identificadores são visualizadas por outros utilizadores que estão com o mesmo problema.

### <a name="error-categories"></a>Categorias de erro

Categorias de erro são utilizadas para agrupar os erros para o utilizador final. Windows PowerShell define essas categorias e cmdlets e provedores do Windows PowerShell tem de escolher entre elas ao gerar o registo de erro.

Para obter uma descrição das categorias de erro que estão disponíveis, consulte a [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeração. Em geral, deve evitar utilizar NoError UndefinedError e GenericError sempre que possível.

Os utilizadores podem ver os erros com base na categoria quando eles definido "`$ErrorView`" para "CategoryView".

## <a name="see-also"></a>Veja Também

[Cmdlets do Windows PowerShell](./cmdlet-overview.md)

[Resultado do cmdlet](./types-of-cmdlet-output.md)

[Shell do Windows PowerShell SDK](../windows-powershell-reference.md)
