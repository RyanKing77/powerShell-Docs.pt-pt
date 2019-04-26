---
title: Referência do Windows PowerShell - o que há de novo
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080531"
---
# <a name="whats-new"></a>Novidades

Windows PowerShell 2.0 fornece as seguintes novas funcionalidades para utilização durante a escrita de cmdlets, fornecedores e alojar aplicações.

## <a name="modules"></a>Módulos

Agora pode empacotar e distribuir as soluções do Windows PowerShell através da utilização de módulos. Módulos permitem-lhe partição, organizar e abstraem o código do Windows PowerShell em unidades independentes e reutilizáveis. Para obter mais informações sobre os módulos, consulte a escrever um módulo do Windows PowerShell.

## <a name="the-powershell-class"></a>A classe do PowerShell

A classe de PowerShell fornece uma solução mais simples para a criação de aplicativos, conhecidos como aplicativos de host, que por meio de programação executam comandos. Essa classe permite-lhe criar um pipeline de comandos, especifique o espaço de execução que é utilizado para executar os comandos e especificar a invocar os comandos de forma síncrona ou assíncrona.

## <a name="the-runspacepool-class"></a>A classe RunspacePool

Conjuntos de espaço de execução permitem-lhe criar vários espaços de execução com uma única chamada. O método de CreateRunspacePool fornece várias sobrecargas que podem ser utilizadas para criar espaços de execução que têm os mesmos recursos, como o mesmo anfitrião, estado de sessão inicial e informações de ligação.

## <a name="the-initialsessionstate-class"></a>A classe InitialSessionState

A classe InitialSessionState permite-lhe criar uma configuração de estado de sessão que é utilizada quando um espaço de execução é aberto. Pode criar uma configuração personalizada, uma configuração predefinida que inclui os comandos fornecidos pelo mshshort e uma configuração cujos comandos são restringidos com base nos recursos da sessão.

## <a name="remote-runspaces"></a>Espaços de execução remotos

Agora, pode criar espaços de execução que podem ser abertos em computadores remotos, que lhe permite executar comandos no computador remoto e recolher os resultados localmente. Para criar um espaço de execução remoto, tem de especificar informações sobre a ligação remota ao criar o espaço de execução. Consulte os métodos CreateRunspace e CreateRunspacePool para exemplos. As informações de ligação são definidas pela classe RunspaceConnectionInfo.

## <a name="private-runspace-elements"></a>Elementos de espaço de execução privada

Agora, pode criar espaços de execução cujos elementos são públicos ou privados. Isto permite-lhe criar espaços de execução cujos elementos estão disponíveis para o espaço de execução, mas não estão disponíveis ao usuário. Consulte a classe ConstrainedSessionStateEntry para descobrir quais elementos do espaço de execução podem ser feitos privados.

## <a name="runspace-threading-modes-and-apartment-state"></a>Espaço de execução modos e o estado de apartamento de threading

Agora pode especificar como os threads são criados e usados ao executar comandos num espaço de execução. Ver as propriedades System.Management.Automation.Runspaces.Runspace.ThreadOptions e System.Management.Automation.Runspaces.RunspacePool.ThreadOptions.

Agora pode obter o estado apartment os threads que são utilizados para executar comandos num espaço de execução. Ver as propriedades System.Management.Automation.Runspaces.Runspace.ApartmentState e System.Management.Automation.Runspaces.RunspacePool.ApartmentState.

## <a name="transaction-cmdlets"></a>Cmdlets de transação

Agora, pode criar cmdlets que pode ser utilizado dentro de uma transação. Quando um cmdlet é utilizado numa transação, as ações são temporárias e podem ser aceites ou rejeitados pelos cmdlets de transação fornecidos pelo Windows PowerShell.

Para obter mais informações sobre transações, consulte como suporte a transações.

## <a name="transaction-provider"></a>Fornecedor de transação

Agora, pode criar fornecedores que podem ser utilizados dentro de uma transação. Semelhante aos cmdlets, quando um fornecedor é utilizado numa transação, as ações são temporárias e podem ser aceites ou rejeitados pelos cmdlets de transação fornecidos pelo Windows PowerShell.

Para obter mais informações sobre como especificar o suporte para transações dentro de uma classe de fornecedor, consulte a propriedade System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities.

## <a name="job-cmdlets"></a>Cmdlets de tarefa

Agora pode escrever os cmdlets que pode executar sua ação como uma tarefa. Estas tarefas são executadas em segundo plano sem a interação com a sessão atual. Para obter mais informações sobre como o Windows PowerShell suporta tarefas, consulte tarefas em segundo plano.

## <a name="cmdlet-output-types"></a>Tipos de saída do cmdlet

Agora, pode especificar os tipos de .NET Framework que são devolvidos pelo seus cmdlets ao declarar o atributo OutputType ao escrever seus cmdlets. Isso permitirá que outras pessoas Determinar que tipos de objetos são devolvidos por um cmdlet examinando a propriedade OutputType do cmdlet.

## <a name="event-support"></a>Suporte a eventos

Agora pode escrever os cmdlets que adicionam e consumir eventos. Consulte a classe PSEvent.

## <a name="proxy-commands"></a>Comandos de proxy

Agora pode escrever os comandos de proxy que podem ser utilizados para executar outro comando. Um comando de proxy permite-lhe controlar qual é a funcionalidade do cmdlet de origem está disponível para o utilizador. Por exemplo, pode criar um comando de proxy que remove um parâmetro que é fornecido pelo comando de origem. Consulte a classe ProxyCommand.

## <a name="multiple-choice-prompts"></a>Vários pedidos de escolha

Agora pode escrever aplicações que podem fornecer avisos que permita que o utilizador selecionar várias opções. Conheça a interface de IHostUISupportsMultipleChoiceSelection

## <a name="interactive-sessions"></a>Sessões interativas

Agora pode escrever aplicações que podem iniciar e parar uma sessão interativa num computador remoto.
Ver a interface de IHostSupportsInteractiveSession.

## <a name="custom-cmdlet-help-for-providers"></a>Ajuda do Cmdlet personalizado para fornecedores

Agora, pode criar personalizado de tópicos de ajuda para os cmdlets do fornecedor. Tópicos de ajuda de cmdlets personalizados podem explicar como o cmdlet funciona nos fornecedor caminho e o documento recursos especiais, incluindo os parâmetros dinâmicos que o fornecedor adiciona ao cmdlet.
