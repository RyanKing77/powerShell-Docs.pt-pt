---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Instalar o SKD do Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="installing-the-windows-powershell-sdk"></a>Instalar o SKD do Windows PowerShell

O tópico seguinte descreve como instalar o SDK do PowerShell em diferentes versões do Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Instalar o Windows PowerShell 3.0 SDK para Windows 8 e Windows Server 2012

Windows PowerShell 3.0 é instalado automaticamente com o Windows 8 e Windows Server 2012.
Além disso, pode transferir e instalar as assemblagens de referência para o Windows PowerShell 3.0 como parte do Windows 8 SDK.
Estas assemblagens permitem-lhe escrever cmdlets, fornecedores e programas de anfitrião para o Windows PowerShell 3.0.
Quando instalar o Windows SDK para Windows 8, as assemblagens do Windows PowerShell são instaladas automaticamente na pasta de assemblagem de referência, no \Programas ficheiros (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0.
Para obter mais informações, consulte o [site de transferência do SDK do Windows 8](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).
Exemplos de código do Windows PowerShell também estão disponíveis no Centro de desenvolvimento.
Para obter mais informações, consulte a página de códigos de ambiente de trabalho de exemplo no [site do Dev center](http://code.msdn.microsoft.com/windowsdesktop/).

Além disso, o Windows PowerShell 3.0 é efeitos compatível com o Windows PowerShell 2.0 SDK, que inclui um número de amostras de código.
Para obter mais informações sobre como transferir o SDK do Windows PowerShell 2.0, consulte abaixo.
(Tenha em atenção que enquanto os exemplos de 2.0 código são compatíveis com Windows 8 e Windows PowerShell 3.0, não é possível instalar o Windows PowerShell 2.0 numa plataforma Windows 8.)

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Instalar o Windows PowerShell 3.0 SDK para Windows 7 e Windows Server 2008 R2

Windows 7 e Windows Server 2008 R2 automaticamente a ter o PowerShell 2.0 instalados.
Além disso, pode instalar o PowerShell 3.0 nestes sistemas.
(Para obter mais informações, consulte [instalar o Windows PowerShell](Installing-Windows-PowerShell.md).).
Como descrito acima, também pode instalar o SDK do Windows 8 no Windows 7 e Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Instalar o Windows PowerShell 2.0 SDK para Windows 7, Vista, XP, Server 2003 e Server 2008

O SDK do Windows PowerShell 2.0 fornece as assemblagens de referência necessárias para escrever cmdlets, fornecedores e alojamento de aplicações e fornece c# código de exemplo que pode ser utilizado como ponto de partida, quando começar a escrever código.

Para instalar este SDK, consulte [SDK do Windows PowerShell 2.0](http://go.microsoft.com/fwlink/?LinkId=184611).

## <a name="reference-assemblies"></a>Assemblagens de referência

As assemblagens de referência são instaladas na seguinte localização por predefinição: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> **Tenha em atenção**: não é possível carregar o código que é compilado contra as assemblagens do Windows PowerShell 2.0 em instalações do Windows PowerShell 1.0.
>No entanto, o código que é compilado contra as assemblagens do Windows PowerShell 1.0 pode ser carregado para instalações do Windows PowerShell 2.0.

## <a name="samples"></a>Amostras

Exemplos de código são instalados na seguinte localização por predefinição: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

As secções seguintes fornecem uma breve descrição do que faz cada amostra.

## <a name="cmdlet-samples"></a>Exemplos de cmdlet
**GetProcessSample01**

Demonstra como escrever um simple cmdlet que obtém todos os processos no computador local.

**GetProcessSample02**

Mostra como adicionar parâmetros ao cmdlet.
O cmdlet assume um ou mais nomes de processo e devolve os processos correspondentes.

**GetProcessSample03**

Mostra como adicionar parâmetros que aceitam entrada a partir do pipeline.

**GetProcessSample04**

Mostra como processar erros nonterminating.

**GetProcessSample05**

Mostra como apresentar uma lista de processos especificados.

**SelectObject**

Demonstra como escrever um filtro para selecionar apenas a determinados objetos.

**SelectString**

Mostra como procurar ficheiros de padrões especificados.

**StopProcessSample01**

Mostra como implementar um *PassThru* parâmetro e como pedir comentários dos utilizadores por chamadas para o [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) e [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) métodos.
Os utilizadores especificarem o *PassThru* parâmetro quando pretendem forçar o cmdlet para devolver um objeto

**StopProcessSample02**

Mostra como parar um processo específico.

**StopProcessSample03**

Mostra como declarar aliases para os parâmetros e como suporta carateres universais.

**StopProcessSample04**

Mostra como declarar os conjuntos de parâmetros, o objeto que o cmdlet aceita como entrada e de como especificar o parâmetro predefinido configurado para utilizar.

## <a name="remoting-samples"></a>Exemplos de gestão remota

**RemoteRunspace01**

Mostra como criar um espaço de execução remoto que é utilizado para estabelecer uma ligação remota.

**RemoteRunspacePool01**

Mostra como construir um conjunto de espaço de execução remoto e como executar vários comandos em simultâneo utilizando este conjunto.

**Serialization01**

Mostra como observar uma classe .NET existente e certifique-se de que as informações a partir das propriedades públicas selecionadas desta classe são preservadas em serialização/desserialização.

**Serialization02**

Mostra como observar uma classe .NET existente e certifique-se de que as informações de instância desta classe são preservadas na serialização/desserialização quando as informações não estão disponíveis nas propriedades públicas da classe.

**Serialization03**

Mostra como observar uma classe .NET existente e certifique-se de que as instâncias desta classe e classes derivadas são anular a serialização (rehydrated) em objetos de .NET em direto.

## <a name="event-samples"></a>Exemplos de eventos

**Event01**

Mostra como criar um cmdlet para o registo de eventos ao efetuar a derivação de ObjectEventRegistrationBase.

**Event02**

Mostra como a mostra como receber notificações de eventos do Windows PowerShell que são gerados em computadores remotos.
Utiliza o evento de PSEventReceived exposto através de [espaço de execução](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) classe.

## <a name="hosting-application-samples"></a>Exemplos de aplicações de alojamento

**Runspace01**

Mostra como utilizar o [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) classe para executar o [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet forma síncrona.
O [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet devolve [processo](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objetos para cada processo em execução no computador local.

**Runspace02**

Mostra como utilizar o [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) classe para executar o [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) e [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets de forma síncrona.
O [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet devolve [processo](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objetos para cada processam em execução no computador local e o objeto de ordenação ordena os objetos com base no respetivo [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) propriedade.
Os resultados destes comandos são apresentadas utilizando um [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) controlo.

**Runspace03**

Mostra como utilizar o [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) classe para executar um script de forma síncrona e como processar erros não terminar.
O script recebe uma lista de nomes de processo e, em seguida, obtém desses processos.
Os resultados do script, incluindo quaisquer erros de não interrupção de mensagens em fila que foram gerados ao executar o script, são apresentados numa janela de consola.

**Runspace04**

Mostra como utilizar o [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) classe para executar comandos e como erros de terminação de catch que são emitida ao executar os comandos.
Dois comandos são executados e o último comando é passado um argumento de parâmetro que não é válido.
Como resultado, não existem objetos são devolvidos e um erro de terminação é emitido.

**Runspace05**

Mostra como adicionar um snap-in para um [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) objeto para que o cmdlet do snap-in está disponível quando o espaço de execução é aberto.
O snap-in fornece um cmdlet Get-Process (definido pelo [GetProcessSample01 exemplo](https://technet.microsoft.com/library/ff602028.aspx)) que é executado de forma síncrona utilizando um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objeto.

**Runspace06**

Mostra como adicionar um módulo para um [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) objeto para que o módulo é carregado quando o espaço de execução é aberto.
O módulo fornece um cmdlet Get-Process (definido pelo [GetProcessSample02 exemplo](https://technet.microsoft.com/library/ff602027.aspx)) que é executado de forma síncrona utilizando um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objeto.

**Runspace07**

Mostra como criar um espaço de execução e, em seguida, utilizar esse espaço de execução para executar dois cmdlets de forma síncrona utilizando um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objeto.

**Runspace08**

Mostra como adicionar comandos e argumentos para o pipeline de um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objeto e como executar os comandos de forma síncrona.

**Runspace09**

Mostra como adicionar um script para o pipeline de um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objeto e como executar o script de forma assíncrona.
Os eventos são utilizados para processar o resultado do script.

**Runspace10**

Mostra como criar um Estado de sessão inicial predefinido, como adicionar um cmdlet para o [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), como criar um espaço de execução que utiliza o estado da sessão inicial e como executar o comando utilizando um [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)objeto.

**Runspace11**

Mostra como utilizar o [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) classe para criar um comando de proxy que chama um cmdlet existente, mas que restringe o conjunto de parâmetros disponíveis.
O comando de proxy, em seguida, é adicionado a um Estado de sessão inicial que é utilizado para criar um espaço de execução restrita.
Isto significa que o utilizador pode aceder a funcionalidade do cmdlet apenas através do comando de proxy.

**PowerShell01**

Mostra como criar um espaço de execução restrita, utilizando um [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) objeto.

**PowerShell02**

Mostra como utilizar um conjunto de espaço de execução para executar vários comandos em simultâneo.

## <a name="host-samples"></a>Exemplos de anfitrião

**Host01**

Mostra como implementar uma aplicação de anfitrião que utiliza um anfitrião personalizado.
Neste exemplo é criado um espaço de execução que utiliza o anfitrião personalizado, e, em seguida, o [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API é utilizada para executar um script que chama "Sair".
Em seguida, a aplicação anfitriã analisa o resultado do script e imprime os resultados.

**Host02**

Mostra como escrever uma aplicação de anfitrião que utiliza o tempo de execução do Windows PowerShell, juntamente com uma implementação do anfitrião personalizado.
A aplicação anfitriã define a cultura de anfitrião para alemão, executa a [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet e apresenta os resultados como seria vê-los utilizando pwrsh.exe e, em seguida, impressões saída de dados atuais e a hora em alemão.

**Host03**

Mostra como criar uma aplicação interativa anfitrião baseado em consola que lê os comandos na linha de comandos, executa os comandos e, em seguida, apresenta os resultados para a consola.

**Host04**

Mostra como criar uma aplicação interativa anfitrião baseado em consola que lê os comandos na linha de comandos, executa os comandos e, em seguida, apresenta os resultados para a consola.
Esta aplicação anfitriã também suporta a apresentação de pedidos que permitem ao utilizador especificar múltiplas escolhas.

**Host05**

Mostra como criar uma aplicação interativa anfitrião baseado em consola que lê os comandos na linha de comandos, executa os comandos e, em seguida, apresenta os resultados para a consola.
Esta aplicação de anfitrião que também suporta chamadas para computadores remotos utilizando o [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) e [sair-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.

**Host06**

Mostra como criar uma aplicação interativa anfitrião baseado em consola que lê os comandos na linha de comandos, executa os comandos e, em seguida, apresenta os resultados para a consola.
Além disso, este exemplo utiliza os APIs de atomizador para especificar a cor do texto que é introduzido pelo utilizador.

## <a name="provider-samples"></a>Exemplos de fornecedor

**AccessDBProviderSample01**

Mostra como declarar uma classe de fornecedor que deriva de diretamente o [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) classe.
Está incluído aqui apenas por questões de exaustividade.

**AccessDBProviderSample02**

Mostra como substituir o [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) e [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) métodos para suportar chamadas para os cmdlets New-PSDrive e Remove-PSDrive.
A classe de fornecedor neste exemplo deriva de [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) classe.

**AccessDBProviderSample03**

Mostra como substituir o [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) e [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) métodos para suportar chamadas para os cmdlets do Item de Get e Set-Item.
A classe de fornecedor neste exemplo deriva de [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) classe.

**AccessDBProviderSample04**

Mostra como substituir métodos de contentor para suportar chamadas para o Copy-Item, Get-ChildItem Novo Item e Remover Item cmdlets.
Estes métodos devem ser implementados quando o arquivo de dados contém itens que são contentores.
Um contentor é um grupo de itens subordinados sob um item principal comum.
A classe de fornecedor neste exemplo deriva de [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) classe.

**AccessDBProviderSample05**

Mostra como substituir métodos de contentor para suportar chamadas para os cmdlets de mover Item e o caminho de associação.
Estes métodos devem ser implementados quando o utilizador tem de mover itens dentro de um contentor e se o arquivo de dados contém contentores aninhadas.
A classe de fornecedor neste exemplo deriva de [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) classe.

**AccessDBProviderSample06**

Mostra como substituir métodos de conteúdo para suportar chamadas para o conteúdo encriptado, Get-conteúdo e conteúdo do conjunto de cmdlets.
Estes métodos devem ser implementados quando o utilizador precisa de gerir o conteúdo dos itens no arquivo de dados.
A classe de fornecedor neste exemplo deriva de um a [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) classe e implementa o [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.