---
title: Descrição geral do cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: f8a8c9300d1ac811c7fbbf7050dd24f78306db8f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056673"
---
# <a name="cmdlet-overview"></a>Cmdlet Overview (Cmdlet: Descrição Geral)

Um cmdlet é um comando simples que é utilizado no ambiente do Windows PowerShell. O tempo de execução do Windows PowerShell invoca estes cmdlets no contexto de scripts de automatização que são fornecidos na linha de comandos. O tempo de execução do Windows PowerShell também invoca-los por meio de programação através de APIs do Windows PowerShell.

## <a name="cmdlets"></a>Cmdlets

Cmdlets de executar uma ação e geralmente retorna um objeto do Microsoft .NET Framework para o comando seguinte no pipeline. Para escrever um cmdlet, tem de implementar uma classe de cmdlet que deriva de uma das duas classes base do cmdlet especializados. A classe derivada deve:

- Declare um atributo que identifica a classe derivada como um cmdlet.

- Defina propriedades públicas que são decoradas com atributos que identificam as propriedades públicas como parâmetros de cmdlet.

- Substitua um ou mais da métodos para registos do processo de processamento de entrada.

É possível carregar a assemblagem que contém a classe diretamente, utilizando o [Import-Module](/powershell/module/microsoft.powershell.core/import-module) cmdlet, ou criar um aplicativo de host carrega o assembly ao utilizar o [ System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API. Ambos os métodos oferecem acesso programático e da linha de comandos para a funcionalidade do cmdlet.

## <a name="cmdlet-terms"></a>Termos de cmdlet

Os termos seguintes são utilizados com frequência na documentação de cmdlet do Windows PowerShell:

- **Atributo de cmdlet**: Um atributo do .NET Framework que é usado para declarar uma classe cmdlet como um cmdlet. Embora o Windows PowerShell usa vários atributos que são opcionais, o atributo de Cmdlet é obrigatório. Para obter mais informações sobre este atributo, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).

- **Parâmetro de cmdlet**: As propriedades públicas que definem os parâmetros que estão disponíveis para o utilizador ou para a aplicação que está a executar o cmdlet. Pode ter exigido cmdlets, com nome, posicional, e *mudar* parâmetros. Parâmetros de comutador permitem-lhe definir os parâmetros que são avaliados apenas se os parâmetros são especificados na chamada. Para obter mais informações sobre os diferentes tipos de parâmetros, consulte [parâmetros de Cmdlet](./cmdlet-parameters.md).

- **Conjunto de parâmetros**: Um grupo de parâmetros que podem ser usados no mesmo comando a executar uma ação específica. Um cmdlet pode ter vários conjuntos de parâmetros, mas cada conjunto de parâmetros tem de ter, pelo menos, um parâmetro que seja exclusivo. Design do cmdlet boas recomenda vivamente que o parâmetro exclusivo também de ser um parâmetro necessário. Para obter mais informações sobre conjuntos de parâmetros, consulte [define o parâmetro de Cmdlet](./cmdlet-parameter-sets.md).

- **Parâmetro dinâmico**: Um parâmetro que é adicionado ao cmdlet em tempo de execução. Normalmente, os parâmetros dinâmicos são adicionados ao cmdlet quando outro parâmetro estiver definido como um valor específico. Para obter mais informações sobre parâmetros dinâmicos, consulte [parâmetros dinâmicos de Cmdlet](./cmdlet-dynamic-parameters.md).

- **Método de processamento de entrada**: Um método que um cmdlet pode utilizar para processar os registos que recebe como entrada. Os métodos de processamento de entrada incluem o [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método, o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, o [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método e o [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) método. Quando implementa um cmdlet, tem de substituir, pelo menos, um da [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)e [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) métodos. Normalmente, o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) é o método que substituir porque ele é chamado para cada registo que o cmdlet processa. Por outro lado, o [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método e o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método são chamados uma vez para executar pré-processar ou pós-processamento dos registos. Para obter mais informações sobre estes métodos, consulte [métodos de processamento de entrada](./cmdlet-input-processing-methods.md).

- **Funcionalidade de ShouldProcess**: Windows PowerShell permite-lhe criar cmdlets que solicitar ao utilizador comentários antes do cmdlet faz uma alteração no sistema. Para utilizar esta funcionalidade, o cmdlet tem de declarar que suporta a funcionalidade de ShouldProcess quando declarar o atributo de Cmdlet, e o cmdlet deve chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos a partir de um método de processamento de entrada. Para obter mais informações sobre como suportar a funcionalidade de ShouldProcess, consulte [pedir confirmação](./requesting-confirmation-from-cmdlets.md).

- **Transação**: Um grupo lógico de comandos que são tratados como uma única tarefa. A tarefa falhar, automaticamente, se falha de qualquer comando no grupo e o utilizador tem a opção de aceitar ou rejeitar as ações executadas dentro da transação. Para participar de uma transação, o cmdlet tem de declarar que suporta transações quando o atributo de Cmdlet é declarado. Suporte para transações foi introduzido no Windows PowerShell 2.0. Para obter mais informações sobre transações, consulte [transações do Windows PowerShell](http://msdn.microsoft.com/en-us/74d7bac7-bc53-49f1-a47a-272e8da84710).

## <a name="how-cmdlets-differ-from-commands"></a>Como os Cmdlets diferem dos comandos

Cmdlets diferem dos comandos em outros ambientes de shell de comando das seguintes formas:

- Os cmdlets são instâncias de classes do .NET Framework; não são executáveis autónomo.

- Cmdlets podem ser criados do mínimo de uma dúzia de linhas de código.

- Cmdlets fazer em geral, a sua própria análise, apresentação de erro ou a formatação de saída. Analisar, apresentação de erro e formatação de saída são processadas pelo tempo de execução do Windows PowerShell.

- Objetos do pipeline, em vez de fluxos de texto de entrada do processo de cmdlets e cmdlets entregar normalmente objetos como saída no pipeline.

- Os cmdlets são orientados a registros porque processam um único objeto por vez.

## <a name="cmdlet-base-classes"></a>Classes de Base do cmdlet

Windows PowerShell oferece suporte a cmdlets derivados de duas classes base seguintes.

- A maioria dos cmdlets baseiam-se a classes do .NET Framework que derivam do [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe base. Derivar desta classe permite que um cmdlet para utilizar o conjunto mínimo de dependências no tempo de execução do Windows PowerShell. Isso tem dois benefícios. A primeira vantagem é que os objetos de cmdlet são menores e, é menos provável que seja afetado pelas alterações no tempo de execução do Windows PowerShell. A segunda vantagem é que, se necessário, pode criar diretamente uma instância do objeto cmdlet e, em seguida, invocá-lo diretamente, em vez de invocá-lo por meio de tempo de execução do Windows PowerShell.

- Os cmdlets mais complexas são baseados nas classes do .NET Framework que derivam do [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base. Derivar desta classe dá-lhe acesso muito mais para o tempo de execução do Windows PowerShell. Este acesso permite que seu cmdlet chamar scripts, para aceder a fornecedores e para aceder ao estado de sessão atual. (Para aceder ao estado de sessão atual, obter e define as variáveis de sessão e preferências.) No entanto, derivar desta classe aumenta o tamanho do objeto cmdlet, e significa que seu cmdlet está intimamente ligado para a versão atual do tempo de execução do Windows PowerShell.

Em geral, a menos que precise o acesso estendido para o tempo de execução do Windows PowerShell, deve derivar a [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. No entanto, o tempo de execução do Windows PowerShell possui recursos de Registro em log extenso para a execução de cmdlets. Se o seu modelo de auditoria depende este registo, pode impedir a execução do cmdlet a partir de outro cmdlet, derivando do [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.

## <a name="input-processing-methods"></a>Métodos de processamento de entrada

O [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe fornece os seguintes métodos virtuais que são utilizados para processar registros. Todas as classes de cmdlets derivados tem de substituir um ou mais dos primeiros três métodos:

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Utilizado para fornecer funcionalidade opcional única de pré-processamento para o cmdlet.

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Utilizado para fornecer a funcionalidade de processamento Registro-por-Registro para o cmdlet. O [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método poderá ser chamado qualquer número de vezes ou nada, dependendo da entrada do cmdlet.

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Utilizado para fornecer funcionalidade opcional única de pós-processamento para o cmdlet.

- [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Utilizada para parar o processamento quando o utilizador para o cmdlet de forma assíncrona (por exemplo, ao premir CTRL + C).

Para obter mais informações sobre estes métodos, consulte [métodos de processamento de entrada do Cmdlet](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Cmdlet Attributes (Atributos de Cmdlet)

Windows PowerShell define vários atributos de .NET Framework que são utilizados para gerir os cmdlets e especificar a funcionalidade comum, que é fornecido pelo Windows PowerShell e que poderão ser necessárias pelo cmdlet. Por exemplo, os atributos são usados para designar uma classe como um cmdlet, para especificar os parâmetros do cmdlet e pedir a validação de entrada para que os desenvolvedores de cmdlet não precisam implementar essa funcionalidade em seu código de cmdlet. Para obter mais informações sobre os atributos, consulte [atributos do Windows PowerShell](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Nomes de cmdlet

Windows PowerShell usa um par de nome de verbo e substantivo aos cmdlets de nome. Por exemplo, o `Get-Command` cmdlet incluído no Windows PowerShell é utilizado para obter todos os cmdlets que estão registados na shell de comandos. A ação que executa o cmdlet de identifica o verbo e substantivo identifica o recurso no qual o cmdlet executa a ação.

Estes nomes estão especificados quando a classe do .NET Framework está declarada como um cmdlet. Para obter mais informações sobre como declarar uma classe do .NET Framework como um cmdlet, consulte [declaração de atributo do Cmdlet](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Escrevendo código do Cmdlet

Este documento fornece duas formas de descobrir como o código de cmdlet é escrito. Se preferir ver o código sem explicações muito detalhadas, consulte [exemplos de código do Cmdlet](./examples-of-cmdlet-code.md). Se preferir obter mais explicações sobre o código, consulte a [GetProc Tutorial](./getproc-tutorial.md), [StopProc Tutorial](./stopproc-tutorial.md), ou [SelectStr Tutorial](./selectstr-tutorial.md) tópicos.

Para obter mais informações sobre as diretrizes para usando cmdlets, consulte [diretrizes de desenvolvimento do Cmdlet](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Veja Também

[Conceitos de Cmdlet do PowerShell do Windows](./windows-powershell-cmdlet-concepts.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
