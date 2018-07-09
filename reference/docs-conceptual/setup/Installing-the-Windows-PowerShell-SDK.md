---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Instalar o SKD do Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893543"
---
# <a name="installing-the-windows-powershell-sdk"></a>Instalar o SKD do Windows PowerShell

O tópico seguinte descreve como instalar o SDK do PowerShell em diferentes versões do Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Instalar o Windows PowerShell 3.0 SDK para Windows 8 e Windows Server 2012

Windows PowerShell 3.0 é instalado automaticamente com o Windows 8 e Windows Server 2012.
Além disso, pode transferir e instalar os assemblies de referência para o Windows PowerShell 3.0 como parte do SDK do Windows 8.
Esses assemblies permitem-lhe escrever programas de anfitrião, fornecedores e cmdlets para o Windows PowerShell 3.0.
Ao instalar o Windows SDK para Windows 8, os assemblies do Windows PowerShell são instalados automaticamente na pasta de assemblagem de referência, no `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.
Para obter mais informações, consulte a [site de download do SDK do Windows 8](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).
Exemplos de código do Windows PowerShell também estão disponíveis no Centro de desenvolvimento.
Para obter mais informações, consulte a página de exemplo de código de área de trabalho sobre o [site do Centro de desenvolvimento](https://code.msdn.microsoft.com:443/windowsdesktop/).

Além disso, o Windows PowerShell 3.0 está retroativamente compatível com o SDK do Windows PowerShell 2.0, que inclui um número de amostras de código.
Para obter mais informações sobre como transferir o SDK do Windows PowerShell 2.0, veja a seguir.
(Observe que embora os exemplos de 2.0 código são compatíveis com o Windows 8 e Windows PowerShell 3.0, não é possível instalar Windows PowerShell 2.0 numa plataforma Windows 8.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Instalar o Windows PowerShell 3.0 SDK para Windows 7 e Windows Server 2008 R2

Windows 7 e Windows Server 2008 R2 têm automaticamente PowerShell 2.0 instalado.
Além disso, pode instalar o PowerShell 3.0 nesses sistemas.
(Para obter mais informações, consulte [instalar o Windows PowerShell](Installing-Windows-PowerShell.md).).
Conforme descrito acima, também pode instalar o SDK do Windows 8 no Windows 7 e Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Instalar o Windows PowerShell 2.0 SDK para Windows 7, Vista, XP, Server 2003 e o Server 2008

O SDK do Windows PowerShell 2.0 fornece os assemblies de referência necessários para escrever cmdlets, fornecedores e alojamento de aplicações e fornece c# código de exemplo que pode ser usado como o ponto de partida, quando começa a escrever código.

Para instalar este SDK, consulte [SDK do Windows PowerShell 2.0](http://www.microsoft.com/en-us/download/details.aspx?id=2560).

## <a name="reference-assemblies"></a>Assemblies de referência

Assemblies de referência são instalados na seguinte localização por predefinição: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE] 
> Não é possível carregar o código que é compilado contra os assemblies do Windows PowerShell 2.0 em instalações do Windows PowerShell 1.0.
> No entanto, o código que é compilado contra os assemblies do Windows PowerShell 1.0 pode ser carregado para instalações do Windows PowerShell 2.0.

## <a name="samples"></a>Amostras

Exemplos de código são instalados na seguinte localização por predefinição: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

As secções seguintes fornecem uma breve descrição do que faz cada exemplo.

## <a name="cmdlet-samples"></a>Exemplos de cmdlet

### <a name="getprocesssample01"></a>GetProcessSample01

Mostra como escrever um cmdlet simple que obtém todos os processos no computador local.

### <a name="getprocesssample02"></a>GetProcessSample02

Mostra como adicionar parâmetros ao cmdlet.
O cmdlet assume uma ou mais nomes de processo e retorna os processos correspondentes.

### <a name="getprocesssample03"></a>GetProcessSample03

Mostra como adicionar parâmetros que aceitam entrada do pipeline.

### <a name="getprocesssample04"></a>GetProcessSample04

Mostra como lidar com erros de não terminação.

### <a name="getprocesssample05"></a>GetProcessSample05

Mostra como exibir uma lista de processos.

### <a name="selectobject"></a>SelectObject

Mostra como escrever um filtro para selecionar apenas a determinados objetos.

### <a name="selectstring"></a>SelectString

Mostra como procurar ficheiros para padrões especificados.

### <a name="stopprocesssample01"></a>StopProcessSample01

Mostra como implementar um *PassThru* parâmetro e como solicitar comentários do usuário por chamadas para o [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) e [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) métodos.
Os utilizadores podem especificar a *PassThru* parâmetro quando pretendem forçar o cmdlet para retornar um objeto,

### <a name="stopprocesssample02"></a>StopProcessSample02

Mostra como parar um processo específico.

### <a name="stopprocesssample03"></a>StopProcessSample03

Mostra como declarar aliases para os parâmetros e como suportam carateres universais.

### <a name="stopprocesssample04"></a>StopProcessSample04

Mostra como declarar os conjuntos de parâmetros, o objeto que o cmdlet assume como entrada e como especificar o parâmetro predefinido para utilizar.

## <a name="remoting-samples"></a>Exemplos de comunicação remota

### <a name="remoterunspace01"></a>RemoteRunspace01

Mostra como criar um espaço de execução remoto que é utilizado para estabelecer uma ligação remota.

### <a name="remoterunspacepool01"></a>RemoteRunspacePool01

Mostra como construir um conjunto de espaço de execução remoto e como executar vários comandos em simultâneo ao utilizar este conjunto.

### <a name="serialization01"></a>Serialization01

Mostra como examinar uma classe .NET existente e certifique-se de que as informações de propriedades públicas selecionadas dessa classe preservadas na serialização/desserialização.

### <a name="serialization02"></a>Serialization02

Mostra como examinar uma classe .NET existente e certifique-se de que as informações de instância desta classe preservadas na serialização/desserialização quando as informações não estão disponíveis nas propriedades públicas da classe.

### <a name="serialization03"></a>Serialization03

Mostra como examinar uma classe .NET existente e certifique-se de que as instâncias dessa classe e de classes derivadas são desserializadas (reativado) em objetos do .NET em direto.

## <a name="event-samples"></a>Exemplos de evento

### <a name="event01"></a>Event01

Mostra como criar um cmdlet para o registo de eventos derivando de ObjectEventRegistrationBase.

### <a name="event02"></a>Event02

Mostra como mostra a forma receber notificações de eventos do Windows PowerShell que são gerados em computadores remotos.
Ele usa o evento de PSEventReceived exposto por meio da [espaço de execução](/dotnet/api/system.management.automation.runspaces.runspace) classe.

## <a name="hosting-application-samples"></a>Exemplos de aplicações de alojamento

### <a name="runspace01"></a>Runspace01

Mostra como utilizar o [PowerShell](/dotnet/api/system.management.automation.powershell) classe para executar o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet forma síncrona.
O [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet devolve [processo](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objetos para cada processo em execução no computador local.

### <a name="runspace02"></a>Runspace02

Mostra como utilizar o [PowerShell](/dotnet/api/system.management.automation.powershell) classe para executar o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets de forma síncrona.
O [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet devolve [processo](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objetos para cada processo em execução no computador local e o `Sort-Object` classifica os objetos com base no respetivo [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) propriedade.
Os resultados desses comandos são apresentadas utilizando um [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) controle.

### <a name="runspace03"></a>Runspace03

Mostra como utilizar o [PowerShell](/dotnet/api/system.management.automation.powershell) classe para executar um script de forma síncrona e como lidar com erros de não terminação.
O script recebe uma lista de nomes de processo e, em seguida, obtém esses processos.
Os resultados do script, incluindo quaisquer erros de não terminação de mensagens em fila que foram gerados ao executar o script, são exibidos numa janela de consola.

### <a name="runspace04"></a>Runspace04

Mostra como utilizar o [PowerShell](/dotnet/api/system.management.automation.powershell) classe para executar comandos e como erros de terminação de catch que forem lançadas. quando executar os comandos.
Dois comandos são executados, e o último comando é passado um argumento de parâmetro que não é válido.
Como resultado, não existem objetos são devolvidos e um erro de terminação é lançado.

### <a name="runspace05"></a>Runspace05

Mostra como adicionar um snap-in para uma [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) de objeto para que o cmdlet do snap-in está disponível quando o espaço de execução é aberto.
O snap-in fornece um cmdlet de Get-Proc (definido pela [exemplo de GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) que é executado de forma síncrona ao utilizar um [PowerShell](/dotnet/api/system.management.automation.powershell) objeto.

### <a name="runspace06"></a>Runspace06

Mostra como adicionar um módulo para uma [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) de objeto para que o módulo é carregado quando o espaço de execução é aberto.
O módulo fornece um cmdlet de Get-Proc (definido pela [exemplo de GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) que é executado de forma síncrona ao utilizar um [PowerShell](/dotnet/api/system.management.automation.powershell) objeto.

### <a name="runspace07"></a>Runspace07

Mostra como criar um espaço de execução e, em seguida, utilizar esse espaço de execução para executar dois cmdlets de forma síncrona ao utilizar um [PowerShell](/dotnet/api/system.management.automation.powershell) objeto.

### <a name="runspace08"></a>Runspace08

Mostra como adicionar comandos e argumentos para o pipeline de uma [PowerShell](/dotnet/api/system.management.automation.powershell) objeto e como executar os comandos de forma síncrona.

### <a name="runspace09"></a>Runspace09

Mostra como adicionar um script para o pipeline de uma [PowerShell](/dotnet/api/system.management.automation.powershell) objeto e como executar o script de forma assíncrona.
Eventos são usados para manipular a saída do script.

### <a name="runspace10"></a>Runspace10

Mostra como criar um Estado de sessão inicial padrão, como adicionar um cmdlet para o [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), como criar um espaço de execução que utiliza o estado da sessão inicial e como executar o comando utilizando um [PowerShell](/dotnet/api/system.management.automation.powershell)objeto.

### <a name="runspace11"></a>Runspace11

Mostra como utilizar o [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) classe para criar um comando de proxy que chama um cmdlet existente, mas restringe o conjunto de parâmetros.
O comando de proxy, em seguida, é adicionado a um Estado de sessão inicial que é utilizado para criar um espaço de execução restrito.
Isso significa que o usuário pode acessar a funcionalidade do cmdlet apenas através do comando de proxy.

### <a name="powershell01"></a>PowerShell01

Mostra como criar um espaço de execução restrito, usando uma [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) objeto.

### <a name="powershell02"></a>PowerShell02

Mostra como utilizar um agrupamento de espaço de execução para executar vários comandos em simultâneo.

## <a name="host-samples"></a>Exemplos de anfitrião

### <a name="host01"></a>Host01

Mostra como implementar um aplicativo de host que usa um host personalizado.
Neste exemplo é criado um espaço de execução que utiliza o host personalizado, e, em seguida, o [PowerShell](/dotnet/api/system.management.automation.powershell) API é utilizada para executar um script que chama de "Sair".
O aplicativo host, em seguida, analisa a saída do script e imprime os resultados.

### <a name="host02"></a>Host02

Mostra como escrever um aplicativo de host que usa o tempo de execução do Windows PowerShell, juntamente com uma implementação de anfitrião personalizado.
O aplicativo host define a cultura de anfitrião para o alemão, execuções a [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet e apresenta os resultados à medida que os veria através da utilização pwrsh.exe e, em seguida, imprime os dados atuais e a hora em alemão.

### <a name="host03"></a>Host03

Mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.

### <a name="host04"></a>Host04

Mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.
Este aplicativo de host também suporta a apresentação de pedidos que permitem ao usuário especificar várias opções.

### <a name="host05"></a>Host05

Mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.
Este aplicativo de host também oferece suporte a chamadas para computadores remotos utilizando o [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) e [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.

### <a name="host06"></a>Host06

Mostra como criar um aplicativo de host e baseada em console interativo que lê os comandos da linha de comando, executa os comandos e, em seguida, apresenta os resultados no Console.
Além disso, este exemplo utiliza as APIs de atomizador para especificar a cor do texto que é introduzido pelo utilizador.

## <a name="provider-samples"></a>Exemplos de fornecedor

### <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Mostra como declarar uma classe de provedor que deriva diretamente a partir da [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) classe.
Ele é incluído aqui apenas para fornecer uma visão completa.

### <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

Mostra como substituir a [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) e [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) métodos para oferecer suporte a chamadas para o `New-PSDrive` e `Remove-PSDrive` cmdlets.
A classe de fornecedor neste exemplo deriva do [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) classe.

### <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Mostra como substituir a [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) e [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) métodos para oferecer suporte a chamadas para o `Get-Item` e `Set-Item` cmdlets.
A classe de fornecedor neste exemplo deriva do [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) classe.

### <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Mostra como substituir os métodos de contentor para oferecer suporte a chamadas para o `Copy-Item`, `Get-ChildItem`, `New-Item`, e `Remove-Item` cmdlets.
Esses métodos devem ser implementados quando o arquivo de dados contém itens que são contentores.
Um contentor é um grupo de itens filho num item principal comum.
A classe de fornecedor neste exemplo deriva do [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) classe.

### <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

Mostra como substituir os métodos de contentor para oferecer suporte a chamadas para o `Move-Item` e `Join-Path` cmdlets.
Esses métodos devem ser implementados quando o utilizador tem de mover itens dentro de um contêiner e se o arquivo de dados contém contêineres aninhados.
A classe de fornecedor neste exemplo deriva do [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) classe.

### <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Mostra como substituir os métodos de conteúdo para oferecer suporte a chamadas para o `Clear-Content`, `Get-Content`, e `Set-Content` cmdlets.
Esses métodos devem ser implementados quando os utilizadores necessitam gerir o conteúdo dos itens no arquivo de dados.
A classe de fornecedor neste exemplo deriva do [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) classe e ele implementa a [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.