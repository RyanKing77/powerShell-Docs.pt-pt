---
title: Diretrizes de desenvolvimento necessárias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: e68e43a91f9139e8d3dc636b5740121515aab2e6
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986673"
---
# <a name="required-development-guidelines"></a>Required Development Guidelines (Diretrizes de Desenvolvimento Necessárias)

As diretrizes a seguir devem ser seguidas quando você escrever seus cmdlets. Elas são separadas em diretrizes para criar cmdlets e diretrizes para escrever seu código de cmdlet. Se você não seguir essas diretrizes, os cmdlets poderão falhar e os usuários poderão ter uma experiência ruim ao usar seus cmdlets.

## <a name="in-this-topic"></a>Neste tópico

### <a name="design-guidelines"></a>Diretrizes de design

- [Usar somente verbos aprovados (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Nomes de cmdlet: Caracteres que não podem ser usados (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Nomes de parâmetros que não podem ser usados (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Solicitações de confirmação de suporte (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Suporte ao parâmetro Force para sessões interativas (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Objetos de saída de documento (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Diretrizes de código

- [Derive das classes cmdlet ou PSCmdlet (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Especificar o atributo de cmdlet (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Substituir um método de processamento de entrada (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Especificar o atributo OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Não manter identificadores para objetos de saída (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Tratar erros robustamente (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Usar um módulo do Windows PowerShell para implantar seus cmdlets (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Diretrizes de design

As diretrizes a seguir devem ser seguidas durante a criação de cmdlets para garantir uma experiência de usuário consistente entre usar seus cmdlets e outros cmdlets. Quando encontrar uma diretriz de design que se aplique à sua situação, certifique-se de examinar as diretrizes de código para obter diretrizes semelhantes.

### <a name="use-only-approved-verbs-rd01"></a>Usar somente verbos aprovados (RD01)

O verbo especificado no atributo cmdlet deve vir do conjunto reconhecido de verbos fornecidos pelo Windows PowerShell. Ele não deve ser um dos sinônimos proibidos. Use as cadeias de caracteres constantes que são definidas pelas seguintes enumerações para especificar verbos de cmdlet:

- [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Para obter mais informações sobre os nomes de verbo aprovados, consulte [verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Os usuários precisam de um conjunto de nomes de cmdlet detectáveis e esperados. Use o verbo apropriado para que o usuário possa fazer uma rápida avaliação do que um cmdlet faz e descobrir facilmente os recursos do sistema. Por exemplo, o comando de linha de comando a seguir obtém uma lista de todos os comandos no sistema cujos nomes começam com "Start" `get-command start-*`:. Use os substantivos em seus cmdlets para diferenciar seus cmdlets de outros cmdlets. O substantivo indica o recurso no qual a operação será executada. A própria operação é representada pelo verbo.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Nomes de cmdlet: Caracteres que não podem ser usados (RD02)

Ao nomear cmdlets, não use nenhum dos caracteres especiais a seguir.

|Caráter|Nome|
|---------------|----------|
|#|sinal de número|
|,|pontos|
|()|parênteses|
|{}|chaves|
|[]|colchetes|
|&|'|
|-|Observação de hífen **:**  O hífen pode ser usado para separar o verbo do substantivo, mas não pode ser usado dentro do substantivo ou dentro do verbo.|
|/|barra de marcas|
|\\| barra invertida|
|$|cifrão|
|^|acento|
|;|ponto e vírgula|
|:|pontos|
|"|aspas duplas|
|'|aspa simples|
|<>|colchetes angulares|
|&#124;|barra vertical|
|?|ponto de interrogação|
|@|sinal de arroba|
|`|escala de fundo (acento grave)|
|*|asterisco|
|%|sinal de porcentagem|
|+|sinal de adição|
|=|sinal de igual|
|~|supressor|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Nomes de parâmetros que não podem ser usados (RD03)

O Windows PowerShell fornece um conjunto comum de parâmetros a todos os cmdlets, além de parâmetros adicionais que são adicionados em situações específicas. Ao criar seus próprios cmdlets, você não pode usar os seguintes nomes: Confirmar, depurar, Erroaction, ErrorVariable, OutBuffer, OutVariable, WarningAction, WarningVariable, WhatIf, UseTransaction e Verbose. Para obter mais informações sobre esses parâmetros, consulte [nomes de parâmetro comuns](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Solicitações de confirmação de suporte (RD04)

Para os cmdlets que executam uma operação que modifica o sistema, eles devem chamar o método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) para solicitar a confirmação e, em casos especiais, chamam o [ Método System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . (O método [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) deve ser chamado somente depois que o método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) for chamado.)

Para fazer essas chamadas, o cmdlet deve especificar que ele dá suporte a solicitações de `SupportsShouldProcess` confirmação definindo a palavra-chave do atributo cmdlet. Para obter mais informações sobre como definir esse atributo, consulte [declaração de atributo de cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Se o atributo cmdlet da classe cmdlet indicar que o cmdlet dá suporte a chamadas para o método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e o cmdlet não fará a chamada para o [ Método System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , o usuário pode modificar o sistema inesperadamente.

Use o método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) para qualquer modificação no sistema. Uma preferência de usuário e `WhatIf` o parâmetro controlam o método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Por outro lado, a chamada [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) executa uma verificação adicional para modificações potencialmente perigosas. Esse método não é controlado por nenhuma preferência de `WhatIf` usuário ou parâmetro. Se o cmdlet chama o método [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , ele deve ter um `Force` parâmetro que ignora as chamadas para esses dois métodos e que prossegue com a operação. Isso é importante porque permite que o cmdlet seja usado em hosts e scripts não interativos.

Se os cmdlets suportarem essas chamadas, o usuário poderá determinar se a ação deve realmente ser executada. Por exemplo, o cmdlet [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) chama o método [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) antes de parar um conjunto de processos críticos, incluindo os processos System, Winlogon e spoolsv.

Para obter mais informações sobre como dar suporte a esses métodos, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Suporte ao parâmetro Force para sessões interativas (RD05)

Se o cmdlet for usado interativamente, sempre forneça um parâmetro Force para substituir as ações interativas, como prompts ou linhas de leitura de entrada). Isso é importante porque permite que o cmdlet seja usado em hosts e scripts não interativos. Os métodos a seguir podem ser implementados por um host interativo.

- [System. Management. Automation. host. PSHostUserInterface. prompt *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System. Management. Automation. host. Pshostuserinterface. PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System. Management. Automation. host. Ihostuisupportsmultiplechoiceselection. PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System. Management. Automation. host. Pshostuserinterface. PromptForCredential *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System. Management. Automation. host. Pshostuserinterface. ReadLine *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System. Management. Automation. host. Pshostuserinterface. ReadLineAsSecureString *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Objetos de saída de documento (RD06)

O Windows PowerShell usa os objetos que são gravados no pipeline. Para que os usuários tirem proveito dos objetos que são retornados por cada cmdlet, você deve documentar os objetos que são retornados e deve documentar de que forma os membros desses objetos retornados são usados.

## <a name="code-guidelines"></a>Diretrizes de código

As diretrizes a seguir devem ser seguidas durante a gravação do código de cmdlet. Quando você encontrar uma diretriz de código que se aplica à sua situação, certifique-se de examinar as diretrizes de design para obter diretrizes semelhantes.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Derive das classes cmdlet ou PSCmdlet (RC01)

Um cmdlet deve ser derivado da classe base [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) ou [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Os cmdlets que derivam da classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) não dependem do tempo de execução do Windows PowerShell. Eles podem ser chamados diretamente de qualquer linguagem do Microsoft .NET Framework. Os cmdlets que derivam da classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) dependem do tempo de execução do Windows PowerShell. Portanto, eles são executados em um runspace.

Todas as classes de cmdlet implementadas devem ser classes públicas. Para obter mais informações sobre essas classes de cmdlet, consulte [visão geral do cmdlet](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Especificar o atributo de cmdlet (RC02)

Para que um cmdlet seja reconhecido pelo Windows PowerShell, sua classe de .NET Framework deve ser decorada com o atributo de cmdlet. Esse atributo especifica os seguintes recursos do cmdlet.

- O par verbo-e-substantivo que identifica o cmdlet.

- O conjunto de parâmetros padrão que é usado quando vários conjuntos de parâmetros são especificados. O conjunto de parâmetros padrão é usado quando o Windows PowerShell não tem informações suficientes para determinar qual conjunto de parâmetros usar.

- Indica se o cmdlet dá suporte a chamadas para o método [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Esse método exibe uma mensagem de confirmação para o usuário antes que o cmdlet faça uma alteração no sistema. Para obter mais informações sobre como as solicitações de confirmação são feitas, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md).

- Indique o nível de impacto (ou a severidade) da ação associada à mensagem de confirmação. Na maioria dos casos, o valor padrão de Medium deve ser usado. Para obter mais informações sobre como o nível de impacto afeta as solicitações de confirmação exibidas para o usuário, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md).

Para obter mais informações sobre como declarar o atributo de cmdlet, consulte [declaração](./cmdlet-attribute-declaration.md)de CmdletAttribute.

### <a name="override-an-input-processing-method-rc03"></a>Substituir um método de processamento de entrada (RC03)

Para que o cmdlet participe do ambiente do Windows PowerShell, ele deve substituir pelo menos um dos seguintes *métodos de processamento de entrada*.

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) esse método é chamado uma vez e é usado para fornecer funcionalidade de pré-processamento.

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) esse método é chamado várias vezes e é usado para fornecer funcionalidade de registro por registro.

[System. Management. Automation. cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) endprocessando esse método é chamado uma vez e é usado para fornecer funcionalidade de pós-processamento.

### <a name="specify-the-outputtype-attribute-rc04"></a>Especificar o atributo OutputType (RC04)

O atributo OutputType (introduzido no Windows PowerShell 2,0) especifica o tipo de .NET Framework que seu cmdlet retorna para o pipeline. Ao especificar o tipo de saída de seus cmdlets, você torna os objetos retornados por seu cmdlet mais detectáveis por outros cmdlets. Para obter mais informações sobre como decorar a classe cmdlet com esse atributo, consulte [declaração de atributo OutputType](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Não manter identificadores para objetos de saída (RC05)

O cmdlet não deve reter nenhum identificador para os objetos passados para o método [System. Management. Automation. cmdlet. WriteObject *](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Esses objetos são passados para o próximo cmdlet no pipeline ou são usados por um script. Se você mantiver os identificadores para os objetos, duas entidades serão proprietárias de cada objeto, o que causará erros.

### <a name="handle-errors-robustly-rc06"></a>Tratar erros robustamente (RC06)

Um ambiente de administração detecta inerentemente e faz alterações importantes no sistema que você está administrando. Portanto, é vital que os cmdlets manipulem erros corretamente. Para obter mais informações sobre registros de erro, consulte [relatório de erros do Windows PowerShell](./error-reporting-concepts.md).

- Quando um erro impede que um cmdlet continue a processar mais registros, ele é um erro de encerramento. O cmdlet deve chamar o método [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) que faz referência a um objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Se uma exceção não for detectada pelo cmdlet, o tempo de execução do Windows PowerShell gera um erro de encerramento que contém menos informações.

- Para um erro de não finalização que não interrompa a operação no próximo registro que vem do pipeline (por exemplo, um registro produzido por um processo diferente), o cmdlet deve chamar o método [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) que faz referência a um objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Um exemplo de um erro de não finalização é o erro que ocorre se um processo específico não for interrompido. Chamar o método [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) permite que o usuário execute consistentemente as ações solicitadas e retenha as informações de ações específicas que falham. Seu cmdlet deve tratar cada registro da maneira mais independente possível.

- O objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) que é referenciado pelos métodos [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) e [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) requer um exceção em seu núcleo. Siga as diretrizes de design de .NET Framework ao determinar a exceção a ser usada. Se o erro for semanticamente igual a uma exceção existente, use essa exceção ou derive dessa exceção. Caso contrário, derive uma nova exceção ou hierarquia de exceção diretamente do tipo [System. Exception](/dotnet/api/System.Exception) .

Um objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) também requer uma categoria de erro que agrupa erros para o usuário. O usuário pode exibir erros com base na categoria definindo o valor da `$ErrorView` variável shell como CategoryView. As categorias possíveis são definidas pela enumeração [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) .

- Se um cmdlet criar um novo thread e se o código que está sendo executado nesse thread lançar uma exceção sem tratamento, o Windows PowerShell não detectará o erro e encerrará o processo.

- Se um objeto tiver código em seu destruidor que causa uma exceção sem tratamento, o Windows PowerShell não capturará o erro e encerrará o processo. Isso também ocorrerá se um objeto chamar métodos Dispose que causam uma exceção sem tratamento.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Usar um módulo do Windows PowerShell para implantar seus cmdlets (RC07)

Crie um módulo do Windows PowerShell para empacotar e implantar seus cmdlets. O suporte para módulos é introduzido no Windows PowerShell 2,0. Você pode usar os assemblies que contêm as classes de cmdlet diretamente como arquivos de módulo binário (isso é muito útil ao testar seus cmdlets), ou você pode criar um manifesto de módulo que referencie os assemblies de cmdlet. (Você também pode adicionar assemblies de snap-in existentes ao usar módulos.) Para obter mais informações sobre módulos, consulte [escrevendo um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Veja Também

[Diretrizes de desenvolvimento altamente incentivadas](./strongly-encouraged-development-guidelines.md)

[Diretrizes de desenvolvimento de consultoria](./advisory-development-guidelines.md)

[Escrevendo um cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
