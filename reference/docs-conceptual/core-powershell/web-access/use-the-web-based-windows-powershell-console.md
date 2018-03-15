---
ms.date: 2017-08-23
keywords: PowerShell, o cmdlet
title: Utilize a consola web baseado em windows powershell
ms.openlocfilehash: a6c9812253309ba1225141cfd48d0f1c8b8785b5
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="use-the-web-based-windows-powershell-console"></a>Utilizar a Consola do Windows PowerShell baseada na Web

Atualizada: 24 de Junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

Acesso Web Windows PowerShell permite aos utilizadores iniciar sessão para um Web site seguro; Para utilizar sessões, cmdlets e scripts do Windows PowerShell para gerir um computador remoto.

Uma vez a consola do Windows PowerShell é executado num browser, pode ser aberta a partir de uma ampla variedade de dispositivos de cliente quase todos os dispositivos com um browser funcionam.

Consola do Windows PowerShell baseada na web é direcionada para um computador remoto que é especificado por utilizadores como parte do processo de início de sessão. 

Este tópico descreve como iniciar sessão e começar a utilizar a consola do acesso Web Windows PowerShell baseada na web.

Este tópico descreve como utilizar o Windows PowerShell ou executar cmdlets ou scripts. Para obter informações sobre como utilizar o Windows PowerShell e scripts de recursos, consulte o [Consulte também](#see-also) secção no final deste tópico.

## <a name="supported-browsers-and-client-devices"></a>Browsers suportados e dispositivos cliente

Acesso Web Windows PowerShell suporta os browsers seguintes. Embora browsers para dispositivos móveis não são suportados oficialmente, muitos poderá executar a consola do Windows PowerShell baseada na web. Espera-se que outros browsers que aceitam cookies, executam JavaScript e executam Web sites HTTPS funcionem, mas são foram testados oficialmente.

### <a name="supported-desktop-computer-browsers"></a>Browsers para computadores de secretária suportados

- Windows Internet Explorer para Microsoft Windows 8.0, 9.0, 10.0 e 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m para Windows
- Apple Safari 5.1.2 para Windows
- Apple Safari 5.1.2 para Mac SO

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Dispositivos móveis ou browsers testados minimamente

- Windows Phone 7 e 7.5
- Google Android WebKit 3.1 Browser 2.2.1 Android (Kernel 2.6)
- Apple Safari para sistema operativo iPhone 5.0.1
- Apple Safari para sistema de operativo iPad 2 5.0.1

### <a name="browser-requirements"></a>Requisitos de browsers

Para utilizar a consola do acesso Web Windows PowerShell baseada na web, os browsers tem de fazer o seguinte.

- Permita cookies do Web site do gateway de acesso Web Windows PowerShell.
- Ser capaz de abrir e ler páginas HTTPS.
- Abrir e executar Web sites que utilizem JavaScript.

## <a name="signing-in-to-windows-powershell-web-access"></a>Iniciar sessão no Windows PowerShell Web Access

O administrador de acesso Web Windows PowerShell deve fornecer um URL que é o endereço do seu site de gateway do Windows PowerShell Web Access organizações.
Por predefinição, este endereço de Web site é *https://\<server_name\>/pswa*.

Antes de iniciar sessão Windows PowerShell Web Access, lembre-se de que tem o nome ou endereço IP do computador remoto que pretende gerir.
Tem de ser um utilizador autorizado no computador remoto e tem de estar configurado para permitir a gestão remota.
Para obter mais informações sobre como configurar o computador para permitir a gestão remota, consulte [ativar e utilizar comandos remotos no Windows PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting).

O método mais simples de configurar o computador para permitir a gestão remota está a ser executado o **Enable-PSRemoting - force** cmdlet no computador, numa sessão do Windows PowerShell que foi aberta com direitos de utilizador elevados (**Executar como administrador**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Para iniciar sessão no Windows PowerShell Web Access

1. Abra o Web site do acesso Web Windows PowerShell num separador ou janela do browser de Internet.

1. O acesso Web Windows PowerShell-na página sessão, forneça o nome de utilizador de rede, palavra-passe e o nome do computador que pretende gerir (e no qual é um utilizador autorizado). Se o administrador de acesso Web Windows PowerShell instruiu que utilize um URI para um servidor proxy ou site personalizado em vez de um nome de computador, selecione **URI de ligação** no **tipo de ligação** campo e, em seguida, Forneça o URI.

    > ![Tenha em atenção](images/Note.jpeg) **nota**:
    >
    > - Se o computador de destino for um grupo de trabalho, utilize a seguinte sintaxe para fornecer o nome de utilizador e inicie sessão computador: `<workgroup_name>\<user_name>`
    > - Se o computador de destino for o servidor de gateway, pode especificar `localhost` no campo do nome do computador
    > - Se o computador de destino é o servidor de gateway e o servidor de gateway está num grupo de trabalho, tem de utilizar `<workgroup name>\<user_name>` no nome do utilizador registada. Pode utilizar `localhost` no campo do nome do computador.

1. O **definições de ligação opcionais** secção está relacionada com os requisitos de autorização do computador remoto que pretende gerir. Para obter mais informações sobre os parâmetros que são equivalentes às definições de ligação opcionais, consulte o [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession) ajuda do cmdlet.

    Normalmente, as credenciais que utiliza para passar o gateway de acesso Web Windows PowerShell são os mesmos que são reconhecidas pelo computador remoto que pretende gerir. No entanto, se pretender utilizar credenciais diferentes para gerir o computador remoto que especificou no passo 2, expanda o **definições de ligação opcionais** secção e forneça as credenciais alternativas. Caso contrário, avance para o passo 6.

1. Se o administrador de acesso Web Windows PowerShell tiver criado uma configuração de sessão personalizada para utilizadores de acesso Web Windows PowerShell, escreva o nome do nome da configuração de sessão no **nome da configuração** campo. Para obter mais informações sobre configurações de sessão, consulte [about_Session_Configurations](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Manter o **tipo de autenticação** definido como **predefinido** , a menos que tenha sido instruído para fazer de outra forma pelo administrador do acesso Web Windows PowerShell.

1. Clique em **sessão**.

## <a name="signing-out-and-timing-out"></a>Terminar sessão e temporizar

Qualquer um dos seguintes procedimentos termina uma sessão do Windows PowerShell baseada na web.

- Ao clicar em **terminar sessão** no canto inferior direito da consola. (Apenas Windows Server 2012)

- Ao clicar em **guardar** ou **saída** no canto inferior direito da consola (apenas o Windows Server 2012 R2). Ao clicar em **guardar** guarda e fecha a sua sessão do Windows PowerShell Web Access; pode voltar a ligar à sessão mais tarde. Quando inicia sessão no Windows PowerShell Web Access novamente, acesso Web Windows PowerShell mostra uma lista das suas sessões guardadas; pode selecionar e voltar a ligar a uma sessão guardada ou iniciar uma sessão de novo. O número máximo de sessões abertas que os utilizadores têm permissão, guardadas e ativas, é configurado pelo administrador do gateway.

    Ao clicar em **saída** termina a sessão do Windows PowerShell Web Access sem a guardar.

- Tentar iniciar sessão para gerir um computador remoto diferente na mesma sessão de browser ou num novo separador da mesma sessão de browser. (Isto não é aplicável se o servidor de gateway estiver a executar o Windows Server 2012 R2; Windows PowerShell Web Access em execução no Windows Server 2012 R2 permite várias sessões de utilizador em novos separadores na mesma sessão de browser.) Para obter mais informações sobre como utilizar mais do que uma sessão ativa no mesmo computador, consulte o artigo sobre como ligar a vários computadores de destino em simultâneo no [limitações da consola baseada na web](#limitations-of-the-web-based-console) secção deste tópico.

- 20 minutos de inatividade na sessão. O administrador do gateway pode personalizar o período de tempo limite de inatividade; Para obter mais informações, consulte [gestão sessão](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

    - Se estiver desligado de uma sessão na consola baseada na web devido a um erro de rede ou outro encerramento não planeado ou falha, e não porque tem fechou a sessão por si, o Windows PowerShell Web Access sessão continua a executar, ligada para o destino computador até que o período de tempo limite do lado do cliente passe. Por predefinição, este período de tempo limite é 20 minutos e é configurado pelo administrador do gateway. A sessão é desligada após os 20 minutos predefinidos ou após o período de tempo limite especificado pelo administrador do gateway, conforme o que for mais curto.

        Se o servidor de gateway estiver a executar o Windows Server 2012 R2, o acesso Web Windows PowerShell permite que os utilizadores voltem a ligar às sessões numa altura posterior guardadas, mas não pode ver ou voltar a ligar a sessões guardadas até após o período de tempo limite especificado pelo gateway tem de administrador passado.

- Fechar a janela ou separador do browser.

- Desativar o dispositivo de cliente no qual o browser está em execução ou desligá-lo a partir da rede.

- Executar o **saída** comando na consola web. Este comando não funciona se a configuração de sessão ao qual estão ligados ao que está configurada para suportar [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) modo, ou está num espaço de execução restrito.

Se pretender voltar a iniciar sessão, abra a página web do Windows PowerShell Web Access novamente e inicie sessão, seguindo os passos no [iniciar sessão no Windows PowerShell Web Access](#signing-in-to-windows-powershell-web-access) neste tópico.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Diferenças na consola do Windows PowerShell baseada na Web

Depois de iniciarem sessão para o acesso Web Windows PowerShell, uma consola do Windows PowerShell baseada na web é aberto no seu separador ou janela do browser. Porque a consola é ligada ao computador remoto que especificou durante o processo de início de sessão, apenas os cmdlets do Windows PowerShell ou scripts que estão disponíveis no computador remoto podem ser utilizados na consola do. Esta secção descreve outras limitações das consolas do Windows PowerShell Web Access e as diferenças entre consolas de acesso Web Windows PowerShell e o instalado **PowerShell.exe** consola.

### <a name="functional-disparity-with-powershellexe"></a>Disparidade funcional com o PowerShell.exe

A maioria das funcionalidades de anfitrião do Windows PowerShell está disponível na consola do acesso Web Windows PowerShell baseada na web, mas existem algumas funcionalidades que não estão disponíveis.

- Apresenta o progresso aninhado.

  Acesso Web Windows PowerShell apresenta um progresso GUI de cmdlets que progresso de relatório, mas são apresentadas apenas as informações do progresso de nível superior.

- Modificação de cor de entrada.

  Não é possível alterar a cor de entrada (primeiro plano e fundo). O estilo de saída, aviso, verboso e mensagens de erro podem todos ser alterados ao executar um script.

- PSHostRawUserInterface.

  Acesso Web Windows PowerShell é implementado sobre a gestão remota do Windows PowerShell e utiliza um espaço de execução remoto. Acesso Web Windows PowerShell não implementa o alguns métodos esta interface; Por exemplo, qualquer comando que escreve a consola do Windows. Comandos como **PowerTab** não funcionam no Windows PowerShell Web Access.

- Teclas de função.

  Acesso Web Windows PowerShell não suporta algumas teclas de função, em muitos casos porque os comandos estão reservados pelo browser.

### <a name="unsupported-shortcut-keys"></a>Teclas de atalho não suportado

Tecla de função | Ação
-- | --
Ctrl+C | No Windows PowerShell Web Access, **Ctrl + C** é utilizada pelo browser para copiar o conteúdo. A consola oferece um **Cancelar** botão e os utilizadores também podem utilizar **Ctrl + Q** para cancelar comandos.
Alt-space, e, l | Percorra a memória intermédia de ecrã
Alt+Space, e, f | Pesquise por texto na memória intermédia de ecrã
Alt+Space, e, k | Selecione o texto a ser copiado da memória intermédia de ecrã
Alt+Space, e, p | Colar o conteúdo da área de transferência para a consola do Windows PowerShell
Alt+Space, c | Feche a consola do Windows PowerShell
Ctrl+Break | Force a fecho da janela do Windows PowerShell
Ctrl+Home | Elimina a partir do início da linha de comandos atual
Ctrl+End | Elimina para o fim da linha de comandos
F1 | Mova o cursor um caráter para a direita na sua linha de comandos
F2 | Cria um novo comando ao copiar o último comando até ao caráter que escreve
F3 | Conclua a linha de comandos com conteúdo da sua última linha de comandos
F4 | Elimina carateres da posição do cursor
F5 | Percorra para trás o histórico de comando. Para aceder aos comandos no histórico do comando no Windows PowerShell Web Access, clique em de **histórico** desloque botões na consola baseada na web.
F7 | Selecione interativamente um comando a partir do seu histórico de comando
F8 | Percorra os comandos que apresentam o histórico que corresponde ao texto atual
F9 | Execute um comando numerado específico a partir do histórico
Page Up | Execute o primeiro comando no histórico
Page Down | Execute o último comando no histórico
Alt+F7 | Limpe a lista de histórico de comando

### <a name="limitations-of-the-web-based-console"></a>Limitações da consola baseada na Web

- Double-hop

    Pode encontrar o double-hop (ou ligação para um segundo computador a partir da primeira ligação) limitação se tentar criar ou trabalhar uma nova sessão utilizando o acesso Web Windows PowerShell. Acesso Web Windows PowerShell utiliza um espaço de execução remoto, atualmente, **PowerShell.exe** não suporta a estabelecer uma ligação remota para um segundo computador a partir de um espaço de execução remoto. Se tentar ligar a um segundo computador remoto a partir de uma ligação existente utilizando o **Enter-PSSession** cmdlet, por exemplo, pode obter vários erros, tais como €œCannot obter recursos de rede.

    Para evitar erros de double-hop, o administrador deve configurar a autenticação CredSSP no seu ambiente de rede organizações. Para obter mais informações sobre como configurar a autenticação CredSSP, consulte [CredSSP para comunicação remota de Double-hop](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) no site da Microsoft. Também pode fornecer credenciais explícitas quando pretender gerir um segundo computador remoto; é pouco provável que credenciais implícitas permitam o segundo hop.

- Gestão remota

    Acesso Web Windows PowerShell utiliza e tem as mesmas limitações que uma sessão remota do Windows PowerShell. Comandos que chamam diretamente a consola de APIs do Windows, como as de editores baseados na consola ou programas de menu baseados em texto, não funcionam porque os comandos não leem ou gravam pipes padrão de entrada, saída e de erro. Por conseguinte, comandos que iniciam um executável de ficheiros, tais como **notepad.exe**, ou apresentam um GUI, tal como `OpenGridView` ou `ogv`, não funcionam. A experiência é afetada por este comportamento; para si, parece que o acesso Web Windows PowerShell não está a responder ao comando.

- Conclusão de separador

    Conclusão de separador não funciona numa configuração de sessão com um espaço de execução restrito ou um que está a ser **NoLanguage** modo. Embora os administradores possam configurar uma sessão para suportar a conclusão de separador, é desencorajado por motivos de segurança, porque pode expor as seguintes informações para utilizadores não autorizados.

    - Caminhos de sistema de ficheiros internos

    - Pastas partilhadas em computadores internos

    - Variáveis de espaço de execução

    - Tipos carregados ou espaços de nomes .NET Framework

    - Variáveis de ambiente

- **NoLanguage** sessão ou espaço de execução restrito

    Os utilizadores que têm sessão iniciados para um **NoLanguage** não é possível executar a configuração de sessão ou um espaço de execução restrito no Windows PowerShell Web Access o **saída** comandos para terminar a sessão. Para terminar sessão, os utilizadores devem clicar **terminar sessão** na página da consola.

- Ligar a vários computadores de destino em simultâneo.

    Se o servidor de gateway com o Windows Server 2012, o acesso Web Windows PowerShell permite apenas uma ligação ao computador remoto por sessão de browser; não permite aos utilizadores iniciar sessão uma vez e ligar a vários computadores remotos utilizando separadores de browser separados. Quando abre um novo separador ou nova janela do browser, acesso Web Windows PowerShell pede-lhe para desligar a sessão atual e iniciar uma sessão nova, para que possam ligar para o novo (ou ao mesmo) computador remoto. Se forem pretendidas duas ou mais sessões separadas para diferentes computadores remotos, no entanto, uma funcionalidade no Internet Explorer permite-lhe criar uma nova sessão. Para iniciar uma nova sessão de browser no Internet Explorer, prima **ALT**, abra o **ficheiro** e, em seguida, selecione **nova sessão**. Em seguida, abra o Web site do acesso Web Windows PowerShell na nova sessão e inicie sessão para aceder a outro computador remoto.

    Quando o gateway do Windows PowerShell Web Access está em execução no Windows Server 2012 R2, os utilizadores podem abrir várias ligações a computadores remotos no separadores de browser diferente. Se pretender abrir mais de uma ligação a um computador remoto utilizando a consola do Windows PowerShell baseada na web, consulte o administrador de gateway de acesso Web Windows PowerShell para ver se esta funcionalidade é suportada pelo servidor de gateway.

- Sessões persistentes do Windows PowerShell (restabelecimento de ligação).

    Depois de o limite de tempo do gateway de acesso Web Windows PowerShell, a ligação remota entre o gateway e o computador de destino está fechada. Isto para quaisquer cmdlets ou scripts que estão atualmente no processo. É encorajados a utilizar o Windows PowerShell **-tarefa** infraestrutura quando estiver a efetuar tarefas de longa execução, para que possam iniciar tarefas, desligar do computador, voltar a ligar mais tarde e ter as tarefas persistam. Outra vantagem de utilizar **-tarefa** cmdlets é que pode iniciá-los utilizando o acesso Web Windows PowerShell, terminar sessão e, em seguida, voltar a ligar mais tarde, ou ao executar o Windows PowerShell Web Access ou outro anfitrião (por exemplo, o Windows PowerShell Ambiente de script (ISE) integrado).

- Redimensionar a consola.

    O **PowerShell.exe** janela de consola pode ser redimensionada nas seguintes três formas.

    - Arraste e ajuste o tamanho da janela de consola com um rato

    - Altere as propriedades de altura e largura utilizando um GUI de propriedades de consola

    - Alterar a altura e largura das janelas de consola com um cmdlet

        A janela de consola para acesso Web Windows PowerShell pode ser configurada utilizando os cmdlets da seguinte forma. No exemplo seguinte, um utilizador altera a largura da consola de acesso Web Windows PowerShell para **20**.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        Pode alterar a altura da consola de forma semelhante.

        Exemplos adicionais para personalizar a vista da consola estão disponíveis no [blogue da equipa do Windows PowerShell](http://blogs.msdn.com/b/powershell/).

## <a name="see-also"></a>Consulte Também

- [Referência de cmdlets do Windows PowerShell](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
- [Windows PowerShell no Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
- [Repositório do Centro de scripts do TechNet](http://gallery.technet.microsoft.com/scriptcenter)
- [Centro de scripts - Hei, responsável pelo script!](https://technet.microsoft.com/scriptcenter)
- [Blogue da equipa de PowerShell Windows](http://blogs.msdn.com/b/powershell/)
