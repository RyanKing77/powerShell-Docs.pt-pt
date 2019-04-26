---
ms.date: 08/23/2017
keywords: PowerShell, o cmdlet
title: utilizar a consola web com base do windows powershell
ms.openlocfilehash: 2bb9c6ef486ef32012a15f9890997cf2fa6a3a0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086646"
---
# <a name="use-the-web-based-windows-powershell-console"></a>Utilizar a consola do PowerShell de Windows baseado na Web

Atualizado: 24 de Junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell Web Access permite aos utilizadores iniciar sessão para um site seguro; Para utilizar sessões, cmdlets e scripts do Windows PowerShell para gerir um computador remoto.

Como a consola do Windows PowerShell é executado num navegador da web, pode ser aberta a partir de uma grande variedade de dispositivos de cliente quase todos os dispositivos com um navegador da web funcionam.

A consola do Windows PowerShell baseada na web é direcionada para um computador remoto que é especificado por utilizadores como parte do processo de início de sessão.

Este tópico descreve como iniciar sessão e começar a utilizar a consola baseada na web do Windows PowerShell Web Access.

Este tópico não descreve como utilizar o Windows PowerShell ou executar cmdlets ou scripts.
Para obter informações sobre como utilizar o Windows PowerShell e recursos de scripts, consulte a [ver também](#see-also) secção no final deste tópico.

## <a name="supported-browsers-and-client-devices"></a>Dispositivos de cliente e browsers suportados

Windows PowerShell Web Access suporta os seguintes navegadores de Internet.
Apesar de browsers para dispositivos móveis não serem suportados oficialmente, muitos podem ser capazes de executar a consola do Windows PowerShell baseada na web.
Outros browsers que aceitam cookies, executam JavaScript e executam Web sites HTTPS devem funcionem, mas são oficialmente não testados.

### <a name="supported-desktop-computer-browsers"></a>Computador de secretária browsers suportados

- Windows Internet Explorer para Microsoft Windows 8.0, 9.0, 10.0 e 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m para Windows
- Apple Safari 5.1.2 para Windows
- Apple Safari 5.1.2 para Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Dispositivos móveis testados minimamente ou browsers

- Windows Phone 7 e 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1 do buildship (Kernel 2.6)
- Apple Safari para sistema de operativo iPhone 5.0.1
- Apple Safari para sistema de operativo iPad 2 5.0.1

### <a name="browser-requirements"></a>Requisitos de browser

Para utilizar a consola baseada na web do Windows PowerShell Web Access, os browsers tem de fazer o seguinte.

- Permita cookies do site de gateway do Windows PowerShell Web Access.
- Ser capaz de abrir e ler páginas HTTPS.
- Abra e execute o Web sites que utilizem JavaScript.

## <a name="signing-in-to-windows-powershell-web-access"></a>O início de sessão no Windows PowerShell Web Access

O administrador do Windows PowerShell Web Access deve fornecer um URL que é o endereço do seu site de gateway do Windows PowerShell Web Access de organizações.
Por predefinição, este endereço de Web site é *https://\<server_name\>/pswa*.

Antes de iniciar sessão para o Windows PowerShell Web Access, certifique-se de que tem o nome ou endereço IP do computador remoto que pretende gerir.
Tem de ser um utilizador autorizado no computador remoto e tem de ser configurada para permitir a gestão remota.
Para obter mais informações sobre como configurar o seu computador para permitir a gestão remota, consulte [ativar e utilizar comandos remoto no Windows PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting).

O método mais simples de configurar o computador para permitir a gestão remota é executar o **Enable-PSRemoting - force** cmdlet no computador, numa sessão do Windows PowerShell que foi aberta com direitos de utilizador de elevados (**Executar como administrador**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Para iniciar sessão no Windows PowerShell Web Access

1. Abra o site do Windows PowerShell Web Access num separador ou janela do browser de Internet.

1. Na página do Windows PowerShell Web Access início de sessão, forneça o nome de utilizador de rede, palavra-passe e o nome do computador que pretende gerir (e no qual é um utilizador autorizado). Se o administrador do Windows PowerShell Web Access instruiu que utilize um URI para um servidor proxy ou um site personalizado em vez de um nome de computador, selecione **URI de ligação** no **tipo de ligação** campo e, em seguida, Forneça o URI.

    > ![Tenha em atenção](images/Note.jpeg) **nota**:
    >
    > - Se o computador de destino está num grupo de trabalho, utilize a seguinte sintaxe para fornecer o nome de utilizador e inicie sessão computador: `<workgroup_name>\<user_name>`
    > - Se o computador de destino for o servidor de gateway, pode especificar `localhost` no campo de nome do computador
    > - Se o computador de destino é o servidor de gateway e o servidor de gateway estiver num grupo de trabalho, tem de utilizar `<workgroup name>\<user_name>` o nome de usuário arquivado. Pode usar `localhost` no campo de nome do computador.

1. O **definições de ligação opcionais** secção está relacionada com os requisitos de autorização do computador remoto que pretende gerir. Para obter mais informações sobre os parâmetros que são equivalentes às definições de ligação opcionais, consulte a [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession) ajuda do cmdlet.

    Normalmente, as credenciais que utiliza para passar através do gateway do Windows PowerShell Web Access são os mesmos que são reconhecidas pelo computador remoto que pretende gerir. No entanto, se pretender utilizar credenciais diferentes para gerir o computador remoto que especificou no passo 2, expanda o **definições de ligação opcionais** secção e forneça as credenciais alternativas. Caso contrário, avance para o passo 6.

1. Se o administrador do Windows PowerShell Web Access tiver criado uma configuração de sessão personalizada para utilizadores do Windows PowerShell Web Access, escreva o nome do nome de configuração de sessão na **nome da configuração** campo. Para obter mais informações sobre configurações de sessão, consulte [about_Session_Configurations](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Manter o **tipo de autenticação** definida como **predefinido** , a menos que tenha sido instruído para fazer de outra forma pelo administrador do Windows PowerShell Web Access.

1. Clique em **iniciar sessão**.

## <a name="signing-out-and-timing-out"></a>A terminar sessão e temporizar

Qualquer um dos seguintes procedimentos termina uma sessão do Windows PowerShell baseada na web.

- Clicar **terminar sessão** no canto inferior direito da consola. (Apenas Windows Server 2012)

- Clicar **salvar** ou **saída** no canto inferior direito da consola (apenas o Windows Server 2012 R2). Clicar **guardar** guarda e fecha a sua sessão do Windows PowerShell Web Access; pode voltar a ligar à sessão mais tarde. Quando iniciar sessão Windows PowerShell Web Access novamente, o Windows PowerShell Web Access apresenta uma lista das suas sessões guardadas; pode selecionar e voltar a ligar a uma sessão guardada ou iniciar uma nova sessão. O número máximo de sessões abertas que os utilizadores têm permissão, guardadas e ativas, é configurado pelo administrador do gateway.

    Clicar **saída** termina a sessão do Windows PowerShell Web Access sem salvá-lo.

- A tentar iniciar sessão para gerir um computador remoto diferente na mesma sessão de browser ou num novo separador da mesma sessão de browser. (Isso não é aplicável se o servidor de gateway estiver a executar o Windows Server 2012 R2; Windows PowerShell Web Access em execução no Windows Server 2012 R2 permite que várias sessões de utilizador em novos separadores na mesma sessão de browser.) Para obter mais informações sobre como utilizar mais do que uma sessão ativa no mesmo computador, consulte a ligar a vários computadores de destino em simultâneo no [limitações da consola baseada na web](#limitations-of-the-web-based-console) secção deste tópico.

- 20 minutos de inatividade na sessão. O administrador de gateway pode personalizar o período de tempo limite de inatividade; Para obter mais informações, consulte [gerenciamento de sessões](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

    - Se estiver desligado de uma sessão na consola baseada na web devido a um erro de rede ou outro encerramento não planeado ou falha, e não porque a sessão por conta própria, o Windows PowerShell Web Access sessão continua a executar, ligada para o destino computador, até que o período de tempo limite para o mercado de lado do cliente. Por predefinição, este período de tempo limite é 20 minutos e é configurado pelo administrador do gateway. A sessão é desligada após a predefinição de 20 minutos ou após o período de tempo limite especificado pelo administrador do gateway, que for mais curto.

        Se o servidor de gateway estiver a executar o Windows Server 2012 R2, Windows PowerShell Web Access permite aos utilizadores que voltem a ligar às sessões num momento posterior guardadas, mas não é possível ver ou voltar a ligar a sessões guardadas até após o período de tempo limite especificado pelo gateway tem de administrador passado.

- A fechar o separador ou janela do browser.

- Desativar o dispositivo de cliente no qual o browser está em execução ou desligá-lo a partir da rede.

- A executar o **saída** comando na consola web. Este comando não funcionar se a configuração de sessão ao qual está ligado à está configurada para suportar [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) modo, ou está num espaço de execução restrito.

Se pretender voltar a iniciar sessão, abra novamente a página da web Windows PowerShell Web Access e iniciar sessão, seguindo os passos em [iniciar sessão no Windows PowerShell Web Access](#signing-in-to-windows-powershell-web-access) neste tópico.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Diferenças na consola do Windows PowerShell baseada na web

Depois de entrar Windows PowerShell Web Access, a consola do Windows PowerShell baseada na web é aberto no seu separador ou janela do browser. Uma vez que a consola está ligada ao computador remoto que especificou durante o processo de início de sessão, apenas esses cmdlets do Windows PowerShell ou scripts que estão disponíveis no computador remoto podem ser utilizados na consola do. Esta secção descreve outras limitações das consolas do Windows PowerShell Web Access e diferenças entre consolas do Windows PowerShell Web Access e o instalado **PowerShell.exe** consola.

### <a name="functional-disparity-with-powershellexe"></a>Disparidade funcional com PowerShell.exe

A maioria da funcionalidade de anfitrião do Windows PowerShell está disponível na consola baseada na web do Windows PowerShell Web Access, mas existem algumas funcionalidades que não estão disponíveis.

- Apresenta o progresso aninhado.

  Acesso Web do Windows PowerShell apresenta um progresso GUI de cmdlets que informa o progresso, mas são apresentadas apenas as informações de progresso de nível superior.

- Modificação de cor de entrada.

  Não é possível alterar a cor de entrada (primeiro plano e fundo). O estilo de saída, aviso, verboso e mensagens de erro pode todos ser alterado ao executar um script.

- PSHostRawUserInterface.

  Windows PowerShell Web Access é implementado sobre a gestão remota do Windows PowerShell e utiliza um espaço de execução remoto. Windows PowerShell Web Access não implementa alguns métodos nesta interface; Por exemplo, qualquer comando que escreve para a consola do Windows. Por exemplo, os comandos **PowerTab** não funcionam no Windows PowerShell Web Access.

- Teclas de função.

  Windows PowerShell Web Access não suporta algumas teclas de função, em muitos casos porque os comandos estão reservados pelo browser.

### <a name="unsupported-shortcut-keys"></a>Teclas de atalho não suportado

Tecla de função | Ação
-- | --
Ctrl+C | No Windows PowerShell Web Access, **Ctrl + C** é usado pelo navegador para copiar o conteúdo. A consola oferece um **Cancelar** também podem utilizar o botão e os utilizadores **Ctrl + Q** para cancelar comandos.
Alt-space, e, l | Percorra a memória intermédia de ecrã
Alt+Space, e, f | Pesquise por texto na memória intermédia de ecrã
Alt+Space, e, k | Selecione o texto a ser copiado da memória intermédia de ecrã
Alt+Space, e, p | Cole o conteúdo de área de transferência no console do Windows PowerShell
ALT + espaço, c | Feche a consola do Windows PowerShell
CTRL + Break | Force a fecho da janela do Windows PowerShell
CTRL + Home | Elimina desde o início da linha de comandos atual
Ctrl+End | Elimina para o fim da linha de comandos
F1 | Mover o cursor um caráter para a direita na sua linha de comandos
F2 | Cria um novo comando ao copiar o último comando até ao caráter que escreve
F3 | Conclua a linha de comandos com conteúdo da sua última linha de comandos
F4 | Elimina carateres da posição do cursor
F5 | Percorra para trás o histórico de comando. Para aceder aos comandos no histórico do comando no Windows PowerShell Web Access, clique nas **histórico** desloque-se de botões na consola baseada na web.
F7 | Selecione interativamente um comando do seu histórico de comando
F8 | Analisar o histórico de comandos que corresponde ao texto atual a apresentar
F9 | Executar um comando numerado específico a partir do histórico
Página para cima | Execute o primeiro comando no histórico
Página para baixo | Execute o último comando no histórico
Alt+F7 | Limpar a lista de histórico de comando

### <a name="limitations-of-the-web-based-console"></a>Limitações da consola baseada na web

- Double-hop

    Pode encontrar o double-hop (ou ligação para um segundo computador a partir da primeira ligação) limitação se tentar criar uma nova sessão utilizando o Windows PowerShell Web Access. Windows PowerShell Web Access usa um espaço de execução remoto e, atualmente, **PowerShell.exe** não suporta a estabelecer uma ligação remota para um segundo computador a partir de um espaço de execução remoto. Se tentar ligar a um segundo computador remoto a partir de uma ligação existente utilizando o **Enter-PSSession** cmdlet, por exemplo, pode obter vários erros, tais como €œCannot obter recursos de rede.

    Para evitar erros de double-hop, o administrador deve configurar a autenticação CredSSP no seu ambiente de rede de organizações. Para obter mais informações sobre como configurar a autenticação CredSSP, consulte [CredSSP para comunicação remota do segundo salto](https://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) no site da Microsoft. Também pode fornecer credenciais explícitas quando pretender gerir um segundo computador remoto; credenciais implícitas são pouco provável que permitam o segundo hop.

- Comunicação remota

    Windows PowerShell Web Access usa e tem as mesmas limitações que uma sessão remota do Windows PowerShell. Comandos que chamam diretamente a consola do Windows APIs, como os de editores baseados na consola ou programas de menu baseados em texto, não funcionam porque os comandos não leem ou escrever para pipes padrão de entrada, saída e de erro. Por conseguinte, comandos que iniciam um executável de ficheiros, tal como **notepad.exe**, ou apresentam um GUI, tal como `OpenGridView` ou `ogv`, não funcionam. A experiência é afetada por este comportamento; para si, parece que o Windows PowerShell Web Access não está a responder ao comando.

- Conclusão de tabulação

    Conclusão de tabulação não funciona numa configuração de sessão com um espaço de execução restrito ou um que esteja no **NoLanguage** modo. Embora os administradores podem configurar uma sessão para suportar a conclusão de tabulação, é desencorajado por motivos de segurança, porque pode expor as seguintes informações para utilizadores não autorizados.

    - Caminhos do sistema de arquivos internos

    - Pastas partilhadas em computadores internos

    - Variáveis de espaço de execução

    - Tipos carregados or.NET Framework espaços de nomes

    - Variáveis de ambiente

- **NoLanguage** sessão ou espaço de execução restrito

    Os utilizadores que têm sessão iniciados numa **NoLanguage** configuração de sessão ou um espaço de execução restrito no Windows PowerShell Web Access não é possível executar o **saída** comandos para terminar a sessão. Para terminar sessão, os utilizadores devem clicar **terminar sessão** na página da consola.

- Ligar a vários computadores de destino em simultâneo.

    Se o servidor de gateway com o Windows Server 2012, Windows PowerShell Web Access permite apenas uma ligação do computador remoto por sessão de browser; não permite aos utilizadores iniciar sessão uma vez e ligar a vários computadores remotos utilizando separadores de browser separados. Quando abre um novo separador ou nova janela do browser, Windows PowerShell Web Access pede-lhe para desligar a sessão atual e iniciar uma sessão nova, para que possa ligar para o novo (ou o mesmo) computador remoto. Se forem pretendidas duas ou mais sessões separadas para diferentes computadores remotos, no entanto, uma funcionalidade no Internet Explorer permite-lhe criar uma nova sessão. Para iniciar uma nova sessão de browser no Internet Explorer, prima **ALT**, abra o **ficheiro** menu e, em seguida, selecione **nova sessão**. Em seguida, abra o site do Windows PowerShell Web Access na nova sessão e inicie sessão aceder a outro computador remoto.

    Quando o gateway do Windows PowerShell Web Access está em execução no Windows Server 2012 R2, os utilizadores podem abrir várias ligações a computadores remotos no separadores de browser diferentes. Se pretender abrir mais de uma ligação a um computador remoto utilizando a consola do Windows PowerShell baseada na web, contacte o administrador de gateway do Windows PowerShell Web Access para ver se esta funcionalidade é suportada pelo servidor de gateway.

- Sessões persistentes do Windows PowerShell (restabelecimento de ligação).

    Após tempo limite do gateway do Windows PowerShell Web Access, a ligação remota entre o gateway e o computador de destino é fechada. Isso deixa a quaisquer cmdlets ou scripts que estão atualmente no processo. É encorajado a utilizar o Windows PowerShell **-tarefa** infraestrutura quando estiver a efetuar tarefas de longa execução, para que pode iniciar tarefas, desligar do computador, voltar a ligar mais tarde e fazer com tarefas persistam. Outra vantagem de utilizar **-tarefa** cmdlets é que pode iniciá-los utilizando o Windows PowerShell Web Access, terminar sessão e, em seguida, voltar a ligar mais tarde, ao Windows PowerShell Web Access em execução ou outro anfitrião (por exemplo, o Windows PowerShell Integrated Scripting Environment (ISE)).

- Redimensionar a consola.

    O **PowerShell.exe** janela de console pode ser redimensionada nas seguintes três formas.

    - Arraste e ajuste o tamanho da janela de consola com um mouse

    - Alterar as propriedades de altura e largura utilizando um GUI para propriedades de consola

    - Alterar a altura e largura das janelas de consola com um cmdlet

        A janela da consola do Windows PowerShell Web Access pode ser configurada utilizando os cmdlets da seguinte forma. No exemplo a seguir, um utilizador altera a largura da consola do Windows PowerShell Web Access para **20**.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        Pode alterar a altura da consola de forma semelhante.

        Exemplos adicionais para personalizar a vista da consola estão disponíveis no [Blog da Equipe do Windows PowerShell](https://blogs.msdn.com/b/powershell/).

## <a name="see-also"></a>Veja Também

- [Referência de cmdlets do Windows PowerShell](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
- [Windows PowerShell no Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
- [TechNet Script Center Repository](https://gallery.technet.microsoft.com/scriptcenter)
- [Centro de scripts - ei, equipe de scripts!](https://technet.microsoft.com/scriptcenter)
- [Blog da Equipe do PowerShell do Windows](https://blogs.msdn.com/b/powershell/)