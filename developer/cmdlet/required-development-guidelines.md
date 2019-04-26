---
title: Diretrizes de desenvolvimento necessárias | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: 3f6bcd2e4ef4d9c404b3a5deeaa9f25d3fa42ec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067472"
---
# <a name="required-development-guidelines"></a>Required Development Guidelines (Diretrizes de Desenvolvimento Necessárias)

Devem ser seguidas as seguintes diretrizes quando escreve seus cmdlets. Eles são separados em diretrizes para a criação de cmdlets e diretrizes para escrever seu código de cmdlet. Se não seguir estas diretrizes, seus cmdlets poderá falhar e os utilizadores podem ter uma experiência ruim quando utilizarem seus cmdlets.

## <a name="in-this-topic"></a>Neste tópico

### <a name="design-guidelines"></a>Diretrizes de design

- [Utilize apenas aprovados verbos (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Nomes de cmdlet: Carateres que não podem ser utilizados (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Nomes de parâmetros que não podem ser utilizados (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Pedidos de confirmação de suporte (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Parâmetro de força de suporte para sessões interativas (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Objetos de resultado de documento (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Diretrizes de código

- [Derivar a partir do Cmdlet ou Classes de PSCmdlet (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Especificar o atributo de Cmdlet (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Substituir uma método (RC03) de processamento de entrada](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Especificar o atributo OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Não reter identificadores para objetos de saída (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Lidar com erros de modo eficiente (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Utilizar um módulo do Windows PowerShell para implementar os seus Cmdlets (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Diretrizes de design

Devem ser seguidas as seguintes diretrizes durante a criação de cmdlets para garantir uma experiência de usuário consistente entre o uso de seus cmdlets e os outros cmdlets. Quando encontrar uma diretriz de Design que se aplica à sua situação, certifique-se de que examinar as diretrizes de código para obter diretrizes semelhantes.

### <a name="use-only-approved-verbs-rd01"></a>Utilize apenas aprovados verbos (RD01)

O verbo especificado no atributo Cmdlet deve vir do conjunto de reconhecido dos verbos fornecidos pelo Windows PowerShell. Não tem de ser um dos sinónimos proibidos. Utilize as cadeias de caracteres constantes que são definidas pelas seguintes enumerações para especificar os verbos dos cmdlets:

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Para obter mais informações sobre os nomes de verbo aprovado, consulte [verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Os utilizadores têm um conjunto de nomes de cmdlet Detetáveis e esperado. Utilize o verbo apropriado, para que o utilizador pode fazer uma avaliação rápida do que um cmdlet faz bem como para detetar facilmente os recursos do sistema. Por exemplo, o seguinte comando da linha de comandos obtém uma lista de todos os comandos no sistema cujos nomes comecem com "start": `get-command start-*`. Utilize os nomes no seus cmdlets para diferenciar seus cmdlets de outros cmdlets. O substantivo indica o recurso no qual será possível efetuar a operação. A operação em si é representada pelo verbo.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Nomes de cmdlet: Carateres que não podem ser utilizados (RD02)

Ao atribuir um nome de cmdlets, não utilize qualquer um dos seguintes carateres especiais.

|Caráter|Nome|
|---------------|----------|
|#|sinal numérico|
|, |comma|
|()|parênteses|
|{}|chavetas|
|[]|Parênteses Retos|
|&|"e" comercial|
|-|hífen **observação:**  O hífen pode ser utilizado para separar o verbo do substantivo, mas não pode ser utilizado dentro do substantivo ou dentro do verbo.|
|/|barra|
|\|Barra invertida|
|$|cifrão|
|^|acento circunflexo|
|;|ponto e vírgula|
|:|dois pontos|
|"|aspas de fecho|
|'|Plica|
|<>|parênteses angulares|
|&#124;|barra vertical|
|?|ponto de interrogação|
|@|no início de sessão|
|' | criar uma escala (acentos graves)|
|*|asterisco|
|%|símbolo de percentagem|
|+|sinal de adição|
|=|sinal de igual|
|~|til|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Nomes de parâmetros que não podem ser utilizados (RD03)

Windows PowerShell fornece um conjunto comum de um parâmetros para todos os cmdlets e parâmetros adicionais que são adicionados em situações específicas. Ao criar seus próprios cmdlets não é possível utilizar os seguintes nomes: Confirmar, Debug, ErrorAction, ErrorVariable, OutBuffer, OutVariable, WarningAction, WarningVariable, WhatIf, UseTransaction e detalhada. Para obter mais informações sobre estes parâmetros, consulte [nomes de parâmetros comuns](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Pedidos de confirmação de suporte (RD04)

Para cmdlets que execute uma operação que modifica o sistema, deve chamar o [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para pedir a confirmação e, em casos especiais chamar o [ System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método. (A [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método deve ser chamado apenas depois do [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método é chamado.)

Para tornar essas chamadas tem de especificar o cmdlet que suporta pedidos de confirmação ao definir o `SupportsShouldProcess` palavra-chave do atributo de Cmdlet. Para obter mais informações sobre como definir este atributo, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Se o atributo de Cmdlet da classe cmdlet indica que o cmdlet oferece suporte a chamadas para o [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método e o cmdlet não consegue fazer a chamada para o [ System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, o utilizador pode modificar o sistema inesperadamente.

Utilize o [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para qualquer modificação de sistema. Uma preferência de utilizador e o `WhatIf` o controlo de parâmetro a [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. Por outro lado, o [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) chamada executa uma verificação adicional para modificações potencialmente perigosas. Este método não for controlado por qualquer preferência de utilizador ou o `WhatIf` parâmetro. Se seu cmdlet chama o [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método, ele deve ter um `Force` parâmetro que ignora as chamadas para esses dois métodos e que continua com a operação. Isso é importante porque ela permite que seu cmdlet a ser usado em scripts não-interativa e de anfitriões.

Se estas chamadas de suporte de seus cmdlets, o utilizador pode determinar se a ação, na verdade, deve ser executada. Por exemplo, o [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) chamadas de cmdlet a [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método antes de parar um conjunto de processos críticos, incluindo o sistema, o Winlogon, e Processos de Spoolsv.

Para obter mais informações sobre o suporte esses métodos, consulte [pedir confirmação](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Parâmetro de força de suporte para sessões interativas (RD05)

Se seu cmdlet é usado interativamente, forneça sempre um parâmetro Force para substituir as ações interativas, tais como pedidos ou linhas de entrada de leitura). Isso é importante porque ela permite que seu cmdlet a ser usado em scripts não-interativa e de anfitriões. Os seguintes métodos podem ser implementados por um host interativo.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Objetos de resultado de documento (RD06)

Windows PowerShell usa os objetos que são escritos para o pipeline. Por ordem para os usuários tirem proveito dos objetos que são devolvidos por cada cmdlet, tem de documentar os objetos que são devolvidos e tem de documentar o que os membros desses objetos retornados são utilizados para.

## <a name="code-guidelines"></a>Diretrizes de código

Devem ser seguidas as seguintes diretrizes ao escrever o código de cmdlet. Quando encontrar uma diretriz de código que se aplica à sua situação, certifique-se de que examinar as diretrizes de Design para obter diretrizes semelhantes.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Derivar a partir do Cmdlet ou Classes de PSCmdlet (RC01)

Um cmdlet deve derivar a partir da [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) ou [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base. Cmdlets que derivam do [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe não dependem do tempo de execução do Windows PowerShell. Eles podem ser chamados diretamente a partir de qualquer linguagem do Microsoft .NET Framework. Cmdlets que derivam do [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe dependem do tempo de execução do Windows PowerShell. Portanto, eles executar dentro de um espaço de execução.

Todas as classes de cmdlet que implementar têm de ser classes públicas. Para obter mais informações sobre essas classes de cmdlet, consulte [descrição geral do Cmdlet](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Especificar o atributo de Cmdlet (RC02)

Para um cmdlet ser reconhecido pelo Windows PowerShell, sua classe do .NET Framework deve ser decorada com o atributo de Cmdlet. Esse atributo especifica as seguintes funcionalidades do cmdlet.

- O par de verbo e substantivo que identifica o cmdlet.

- O conjunto de parâmetros padrão, que é utilizado quando forem especificados vários conjuntos de parâmetros. O conjunto de parâmetros padrão é utilizado quando o Windows PowerShell não tem informações suficientes para determinar qual parâmetro definido para utilizar.

- Indica se o cmdlet oferece suporte a chamadas para o [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. Esse método apresenta uma mensagem de confirmação ao utilizador antes do cmdlet faz uma alteração no sistema. Para obter mais informações sobre como os pedidos de confirmação são feitos, consulte [pedir confirmação](./requesting-confirmation-from-cmdlets.md).

- Indica o nível de impacto (ou gravidade) da ação associada com a mensagem de confirmação. Na maioria dos casos, deve ser utilizado o valor predefinido de média. Para obter mais informações sobre como o nível de impacto afeta os pedidos de confirmação que são apresentados ao utilizador, consulte [pedir confirmação](./requesting-confirmation-from-cmdlets.md).

Para obter mais informações sobre como declarar o atributo de cmdlet, consulte [declaração CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Substituir uma método (RC03) de processamento de entrada

Para o cmdlet para participar no ambiente do Windows PowerShell, ele deve substituir a, pelo menos, um dos seguintes *métodos de processamento de entrada*.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) esse método é chamado uma vez, e é utilizado para fornecer a funcionalidade de pré-processamento.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) esse método é chamado várias vezes, e é utilizado para fornecer a funcionalidade de Registro por Registro.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) esse método é chamado uma vez, e é utilizado para fornecer a funcionalidade de pós-processamento.

### <a name="specify-the-outputtype-attribute-rc04"></a>Especificar o atributo OutputType (RC04)

O atributo OutputType (introduzido no Windows PowerShell 2.0) Especifica o tipo de .NET Framework que seu cmdlet retorna para o pipeline. Ao especificar o tipo de saída de seus cmdlets Certifique-se aos objectos devolvidos pelo seu cmdlet mais detectáveis por outros cmdlets. Para obter mais informações sobre decorando a classe cmdlet com esse atributo, consulte [declaração de atributo OutputType](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Não reter identificadores para objetos de saída (RC05)

Seu cmdlet não deve manter quaisquer identificadores para os objetos que são transmitidos para o [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Esses objetos são transmitidos para o próximo cmdlet no pipeline, ou eles são usados por um script. Se mantiver os identificadores para objetos, duas entidades serão proprietários cada objeto, o que causa erros.

### <a name="handle-errors-robustly-rc06"></a>Lidar com erros de modo eficiente (RC06)

Um ambiente de administração inerentemente detecta e faz alterações importantes no sistema que está a administrar. Por conseguinte, é vital que cmdlets lidar com erros corretamente. Para obter mais informações sobre os registos de erro, consulte [relatório de erros do Windows PowerShell](./error-reporting-concepts.md).

- Quando um erro impede o continuar a processar quaisquer registos mais de um cmdlet, é um erro de terminação. O cmdlet deve chamar o [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método que faz referência a um [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto. Se uma exceção não é capturada pelo cmdlet, o tempo de execução do Windows PowerShell em si lança um erro de terminação que contenha menos informações.

- Para um erro de não terminação de mensagens em fila que não a interromperá se a operação no próximo registo que seja proveniente do pipeline (por exemplo, um registro produzido por um processo diferente), o cmdlet deve chamar o [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método que faz referência a uma [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto. Um exemplo de um erro de não terminação é o erro que ocorre se um determinado processo não conseguir parar. Chamar o [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método permite ao utilizador para executar consistentemente ações pedidas e para manter as informações de ações específicas que falharam. O cmdlet deve processar cada registo de forma independente possível.

- O [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto que é referenciado pela [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) e [ System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) métodos requer uma exceção em seu núcleo. Siga as diretrizes de design do .NET Framework, quando determinar que a exceção para utilizar. Se o erro semanticamente é o mesmo que uma exceção existente, utilize essa exceção ou derivar dessa exceção. Caso contrário, derivar uma nova exceção ou uma hierarquia de exceção diretamente a partir da [Exception](/dotnet/api/System.Exception) tipo.

Uma [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto também requer uma categoria de erro que agrupa os erros para o utilizador. O utilizador pode ver os erros com base na categoria do definindo o valor da `$ErrorView` variável de shell para CategoryView. As categorias de possíveis são definidas pelos [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeração.

- Se um cmdlet cria um novo thread, e se o código que está a executar esse thread gerará uma exceção não processada, o Windows PowerShell não capturará o erro e encerrará o processo.

- Se um objeto tiver código em seu destruidor que faz com que uma exceção não processada, o Windows PowerShell não capturará o erro e encerrará o processo. Isso também ocorre em caso de um objeto chama Dispose métodos que fazem com que uma exceção não processada.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Utilizar um módulo do Windows PowerShell para implementar os seus Cmdlets (RC07)

Crie um módulo do Windows PowerShell para empacotar e implantar seus cmdlets. Suporte para módulos é introduzido no Windows PowerShell 2.0. Pode utilizar os assemblies que contêm as suas classes de cmdlet diretamente como arquivos binários de módulo (isso é muito útil durante o teste de seus cmdlets), ou pode criar um manifesto de módulo que faça referência os assemblies de cmdlet. (Também pode adicionar assemblies de snap-in existentes ao utilizar os módulos.) Para obter mais informações sobre os módulos, consulte [escrever um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Veja Também

[Diretrizes de desenvolvimento altamente incentivadas](./strongly-encouraged-development-guidelines.md)

[Diretrizes de desenvolvimento de consultoria](./advisory-development-guidelines.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
