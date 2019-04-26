---
title: Instalar o SKD do Windows PowerShell
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082486"
---
# <a name="installing-the-windows-powershell-sdk"></a>Instalar o SKD do Windows PowerShell

Aplica-se a: Windows PowerShell 2.0, Windows PowerShell 3.0

O tópico seguinte descreve como instalar o SDK do PowerShell em diferentes versões do Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Instalar o Windows PowerShell 3.0 SDK para Windows 8 e Windows Server 2012

Windows PowerShell 3.0 é instalado automaticamente com o Windows 8 e Windows Server 2012. Além disso, pode transferir e instalar os assemblies de referência para o Windows PowerShell 3.0 como parte do SDK do Windows 8. Esses assemblies permitem-lhe escrever programas de anfitrião, fornecedores e cmdlets para o Windows PowerShell 3.0. Quando instalar o Windows SDK para Windows 8, os assemblies do Windows PowerShell são instalados automaticamente na pasta do assembly de referência, na \Programas ficheiros (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0. Para obter mais informações, consulte o site de download do Windows 8 SDK. Exemplos de código do Windows PowerShell também estão disponíveis no Centro de desenvolvimento.
Para obter mais informações, consulte a página de exemplo de código de área de trabalho no site do Dev center.

Além disso, o Windows PowerShell 3.0 está retroativamente compatível com o SDK do Windows PowerShell 2.0, que inclui um número de amostras de código. Para obter mais informações sobre como transferir o SDK do Windows PowerShell 2.0, veja a seguir. (Observe que embora os exemplos de 2.0 código são compatíveis com o Windows 8 e Windows PowerShell 3.0, não é possível instalar Windows PowerShell 2.0 numa plataforma Windows 8.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Instalar o Windows PowerShell 3.0 SDK para Windows 7 e Windows Server 2008 R2

Windows 7 e Windows Server 2008 R2 têm automaticamente PowerShell 2.0 instalado. Além disso, pode instalar o PowerShell 3.0 nesses sistemas. (Para obter mais informações, consulte instalar o Windows PowerShell.). Conforme descrito acima, também pode instalar o SDK do Windows 8 no Windows 7 e Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Instalar o Windows PowerShell 2.0 SDK para Windows 7, Vista, XP, Server 2003 e o Server 2008

O SDK do Windows PowerShell 2.0 fornece os assemblies de referência necessários para escrever cmdlets, fornecedores e alojamento de aplicações e fornece C# código de exemplo que pode ser usado como o ponto de partida, quando começa a escrever código.

Para instalar este SDK, consulte o SDK do Windows PowerShell 2.0.

### <a name="reference-assemblies"></a>Assemblies de referência

Assemblies de referência são instalados na seguinte localização por predefinição: c:\Programas\Microsoft Assemblies\Microsoft\WindowsPowerShell\V1.0 arquivos.

> [!NOTE]
>
> Não é possível carregar o código que é compilado contra os assemblies do Windows PowerShell 2.0 em instalações do Windows PowerShell 1.0. No entanto, o código que é compilado contra os assemblies do Windows PowerShell 1.0 pode ser carregado para instalações do Windows PowerShell 2.0.


### <a name="samples"></a>Amostras

Por predefinição, exemplos de código são instalados na seguinte localização: C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. As secções seguintes fornecem uma breve descrição do que faz cada exemplo.

#### <a name="cmdlet-samples"></a>Exemplos de cmdlet

- GetProcessSample01 - mostra como escrever um cmdlet simple que obtém todos os processos no computador local.
- GetProcessSample02 - mostra como adicionar parâmetros ao cmdlet. O cmdlet assume uma ou mais nomes de processo e retorna os processos correspondentes.
- GetProcessSample03 - mostra como adicionar parâmetros que aceitam entrada do pipeline.
- GetProcessSample04 - mostra como lidar com erros de não terminação.
- GetProcessSample05 - mostra como exibir uma lista de processos.
- SelectObject - mostra como escrever um filtro para selecionar apenas a determinados objetos.
- SelectString - mostra como procurar ficheiros para padrões especificados.
- StopProcessSample01 - mostra como implementar um parâmetro PassThru e como solicitar comentários do usuário por chamadas para os métodos ShouldProcess e ShouldContinue. Os utilizadores especificar o parâmetro PassThru, quando desejam forçar o cmdlet para retornar um objeto,
- StopProcessSample02 - mostra como parar um processo específico.
- StopProcessSample03 - mostra como declarar aliases para os parâmetros e como suportam carateres universais.
- StopProcessSample04 - mostra como declarar os conjuntos de parâmetros, o objeto que o cmdlet assume como entrada e como especificar o parâmetro predefinido para utilizar.

#### <a name="remoting-samples"></a>Exemplos de comunicação remota

- RemoteRunspace01 - mostra como criar um espaço de execução remoto que é utilizado para estabelecer uma ligação remota.
- RemoteRunspacePool01 - mostra como construir um conjunto de espaço de execução remoto e como executar vários comandos em simultâneo ao utilizar este conjunto.
- Serialization01 - mostra como examinar uma classe .NET existente e certifique-se de que as informações de propriedades públicas selecionadas dessa classe preservadas na serialização/desserialização.
- Serialization02 - mostra como examinar uma classe .NET existente e certifique-se de que as informações de instância desta classe preservadas na serialização/desserialização quando as informações não estão disponíveis nas propriedades públicas da classe.
- Serialization03 - mostra como examinar uma classe .NET existente e certifique-se de que as instâncias dessa classe e de classes derivadas são desserializadas (reativado) em objetos do .NET em direto.

#### <a name="event-samples"></a>Exemplos de evento

- Event01 - mostra como criar um cmdlet para o registo de eventos derivando de ObjectEventRegistrationBase.
- Event02 - mostra como mostra a forma receber notificações de eventos do Windows PowerShell que são gerados em computadores remotos. Ele usa o evento de PSEventReceived exposto por meio da classe de espaço de execução.

#### <a name="hosting-application-samples"></a>Exemplos de aplicações de alojamento

- Runspace01 - mostra como usar a classe de PowerShell para executar o `Get-Process` cmdlet forma síncrona.
O `Get-Process` cmdlet devolve objetos de processo para cada processo em execução no computador local.
- Runspace02 - mostra como usar a classe de PowerShell para executar o `Get-Process` e `Sort-Object` cmdlets de forma síncrona. O `Get-Process` cmdlet devolve objetos de processo para cada processo em execução no computador local e o `Sort-Object` classifica os objetos com base na respetiva propriedade de Id. Os resultados desses comandos é apresentado ao utilizar um controle DataGridView.
- Runspace03 - mostra como usar a classe de PowerShell para executar um script de forma síncrona e como lidar com erros de não terminação. O script recebe uma lista de nomes de processo e, em seguida, obtém esses processos. Os resultados do script, incluindo quaisquer erros de não terminação de mensagens em fila que foram gerados ao executar o script, são exibidos numa janela de consola.
- Runspace04 - mostra como usar a classe de PowerShell para executar comandos e como detetar erros que forem lançados. quando executar os comandos de terminação. Dois comandos são executados, e o último comando é passado um argumento de parâmetro que não é válido. Como resultado, não existem objetos são devolvidos e um erro de terminação é lançado.
- Runspace05 - mostra como adicionar um snap-in a um objeto de InitialSessionState, para que o cmdlet do snap-in está disponível quando o espaço de execução é aberto. O snap-in fornece um cmdlet de Get-Proc (definido pelo exemplo GetProcessSample01), que é executado de forma síncrona ao utilizar um objeto do PowerShell.
- Runspace06 - mostra como adicionar um módulo para um objeto de InitialSessionState para que o módulo é carregado quando o espaço de execução é aberto. O módulo fornece um cmdlet de Get-Proc (definido pelo exemplo GetProcessSample02), que é executado de forma síncrona ao utilizar um objeto do PowerShell.
- Runspace07 - mostra como criar um espaço de execução e, em seguida, utilizar esse espaço de execução para executar dois cmdlets de forma síncrona, utilizando um objeto do PowerShell.
- Runspace08 - mostra como adicionar comandos e argumentos para o pipeline de um objeto do PowerShell e como executar os comandos de forma síncrona.
- Runspace09 - mostra como adicionar um script para o pipeline de um objeto do PowerShell e como executar o script de forma assíncrona. Eventos são usados para manipular a saída do script.
- Runspace10 - mostra como criar um Estado de sessão inicial padrão, como adicionar um cmdlet para o InitialSessionState, como criar um espaço de execução que utiliza o estado da sessão inicial e como executar o comando utilizando um objeto do PowerShell.
- Runspace11 - mostra como usar a classe de ProxyCommand para criar um comando de proxy que chama um cmdlet existente, mas restringe o conjunto de parâmetros. O comando de proxy, em seguida, é adicionado a um Estado de sessão inicial que é utilizado para criar um espaço de execução restrito. Isso significa que o usuário pode acessar a funcionalidade do cmdlet apenas através do comando de proxy.
- PowerShell01 - mostra como criar um espaço de execução restrito, usando um objeto de InitialSessionState.
- PowerShell02 - mostra como utilizar um agrupamento de espaço de execução para executar vários comandos em simultâneo.

#### <a name="host-samples"></a>Exemplos de anfitrião

- Host01 - mostra como implementar um aplicativo de host que usa um host personalizado. Neste exemplo que é criado um espaço de execução que utiliza o anfitrião personalizado e, em seguida, a API do PowerShell é utilizada para executar um script que chama de "Sair". O aplicativo host, em seguida, analisa a saída do script e imprime os resultados.
- Host02 - mostra como escrever um aplicativo de host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de anfitrião personalizado. O aplicativo host define a cultura de anfitrião para o alemão, execuções a `Get-Process` cmdlet e apresenta os resultados à medida que os veria através da utilização pwrsh.exe e, em seguida, imprime os dados atuais e a hora em alemão.
- Host03 - mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.
- Host04 - mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console. Este aplicativo de host também suporta a apresentação de pedidos que permitem ao usuário especificar várias opções.
- Host05 - mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console. Este aplicativo de host também oferece suporte a chamadas para computadores remotos utilizando o `Enter-PsSession` e `Exit-PsSession` cmdlets.
- Host06 - mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console. Além disso, este exemplo utiliza as APIs de atomizador para especificar a cor do texto que é introduzido pelo utilizador.

#### <a name="provider-samples"></a>Exemplos de fornecedor

- AccessDBProviderSample01 - mostra como declarar uma classe de provedor que deriva diretamente a partir da classe CmdletProvider. Ele é incluído aqui apenas para fornecer uma visão completa.

- AccessDBProviderSample02 - mostra como substituir os métodos NewDrive e RemoveDrive para suporte a chamadas para o `New-PSDrive` e `Remove-PSDrive` cmdlets. A classe de fornecedor neste exemplo é derivada da classe DriveCmdletProvider.

- AccessDBProviderSample03 - mostra como substituir os métodos GetItem e SetItem para suporte a chamadas para o `Get-Item` e `Set-Item` cmdlets. A classe de fornecedor neste exemplo é derivada da classe ItemCmdletProvider.

- AccessDBProviderSample04 - mostra como substituir os métodos de contentor para oferecer suporte a chamadas para o `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlets. Esses métodos devem ser implementados quando o arquivo de dados contém itens que são contentores. Um contentor é um grupo de itens filho num item principal comum. A classe de fornecedor neste exemplo é derivada da classe ItemCmdletProvider.

- AccessDBProviderSample05 - mostra como substituir os métodos de contentor para oferecer suporte a chamadas para o `Move-Item` e `Join-Path` cmdlets. Esses métodos devem ser implementados quando o utilizador tem de mover itens dentro de um contêiner e se o arquivo de dados contém contêineres aninhados. A classe de fornecedor neste exemplo é derivada da classe NavigationCmdletProvider.

- AccessDBProviderSample06 - mostra como substituir os métodos de conteúdo para oferecer suporte a chamadas para o `Clear-Content`, `Get-Content`, e `Set-Content` cmdlets. Esses métodos devem ser implementados quando os utilizadores necessitam gerir o conteúdo dos itens no arquivo de dados. A classe de fornecedor neste exemplo é derivada da classe NavigationCmdletProvider e implementa a interface de IContentCmdletProvider.
