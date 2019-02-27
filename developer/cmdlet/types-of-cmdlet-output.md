---
title: Tipos de resultado do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845361"
---
# <a name="types-of-cmdlet-output"></a>Tipos de resultado do cmdlet

PowerShell fornece vários métodos que podem ser chamados por cmdlets para gerar a saída. Esses métodos usam uma operação específica para escrever sua saída para um fluxo de dados específicos, como o fluxo de dados de êxito ou o fluxo de dados de erro. Este artigo descreve os tipos de saída e os métodos utilizados para gerá-los.

## <a name="types-of-output"></a>Tipos de saída

### <a name="success-output"></a>Saída de êxito

Cmdlets pode relatar êxito retornando um objeto que pode ser processado pelo comando seguinte no pipeline. Depois do cmdlet efetuou com êxito a ação, o cmdlet chama o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Recomendamos que chamar esse método em vez do [WriteLine](/dotnet/api/System.Console.WriteLine) ou [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) métodos.

Pode fornecer uma **PassThru** mudar o parâmetro para cmdlets que normalmente não retornam objetos.
Quando o **PassThru** parâmetro for especificado na linha de comandos, o cmdlet é-lhe pedido para retornar um objeto. Para obter um exemplo de um cmdlet que tem um **PassThru** parâmetro, veja [Add-histórico](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Saída de erro

Cmdlets podem comunicar os erros. Quando ocorre um erro de terminação, o cmdlet lançará uma exceção. Quando ocorre um erro de não terminação, o cmdlet chama o [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método para enviar um registo de erro para o fluxo de dados de erro. Para obter mais informações sobre os relatórios de erro, consulte [conceitos de relatórios de erro](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Saída verbosa ideal

Cmdlets pode fornecer informações úteis para si, enquanto o cmdlet está a processar corretamente registos ao chamar o [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método. O método gera as mensagens verbosas que indicam como a ação está em curso.

Por predefinição, as mensagens verbosas não são apresentadas. Pode especificar a **verboso** parâmetro quando o cmdlet é executado para exibir essas mensagens. **Verboso** é um parâmetro comum de que está disponível para todos os cmdlets.

### <a name="progress-output"></a>Saída de progresso

Cmdlets pode fornecer informações de progresso para quando o cmdlet está a efetuar tarefas que demoram muito tempo a concluir, como copiar um diretório recursivamente. Para apresentar informações de progresso o cmdlet chama o [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.

### <a name="debug-output"></a>Saída de depuração

Cmdlets pode fornecer mensagens de depuração que são úteis quando o código de cmdlet de resolução de problemas. Para apresentar informações de depuração o cmdlet chama o [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método.

Por predefinição, as mensagens de depuração não são apresentadas. Pode especificar a **depurar** parâmetro quando o cmdlet é executado para exibir essas mensagens. **Depurar** é um parâmetro comum de que está disponível para todos os cmdlets.

### <a name="warning-output"></a>Saída de aviso

Cmdlets pode apresentar mensagens de aviso ao chamar o [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método.

Por predefinição, são apresentadas mensagens de aviso. No entanto, pode configurar mensagens de aviso, utilizando o `$WarningPreference` variável ou ao utilizar o **verboso** e **depurar** parâmetros quando o cmdlet é chamado.

## <a name="displaying-output"></a>Exibindo saída

Para todas as chamadas de método de gravação, a exibição de conteúdo é determinada por meio de variáveis do tempo de execução específica. A exceção é o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Ao utilizar estas variáveis, pode fazer o adequado escrever chamada no local correto no seu código e não se preocupar sobre o quando ou se o resultado deverá ser apresentado.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Acessar a funcionalidade de saída de um aplicativo de host

Também é possível criar um cmdlet para aceder diretamente a funcionalidade de saída de um aplicativo host por meio de tempo de execução do PowerShell. Utilizar o anfitrião APIs fornecidas pelo PowerShell, em vez de [System. Console](/dotnet/api/System.Console) ou [Forms](/dotnet/api/System.Windows.Forms) garante que seu cmdlet irá funcionar com uma variedade de anfitriões. Por exemplo: o **powershell.exe** host de console, o **powershell_ise.exe** gráfica anfitrião, o anfitrião de comunicação remota do PowerShell e os anfitriões de terceiros.

## <a name="see-also"></a>Consulte também

[Conceitos de relatórios de erro](./error-reporting-concepts.md)

[Descrição geral do cmdlet](./cmdlet-overview.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)