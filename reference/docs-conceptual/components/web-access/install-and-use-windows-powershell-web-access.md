---
ms.date: 08/23/2017
keywords: PowerShell, o cmdlet
title: instalar e utilizar o acesso web windows powershell
ms.openlocfilehash: 53558f9be5065c7f630f06e535ddab4d7ad72d9e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056724"
---
# <a name="install-and-use-windows-powershell-web-access"></a>Instalar e Utilizar o Acesso Web Windows PowerShell

Atualizado: 5 de Novembro de 2013 (editá-lo: 23 de Agosto de 2017)

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Introdução

Windows PowerShell Web Access, introduzido pela primeira vez no Windows Server 2012, atua como um gateway do Windows PowerShell, fornecendo uma consola do Windows PowerShell baseada na web que é direcionada para um computador remoto. Permite que os profissionais de TI executar comandos do Windows PowerShell e scripts a partir de uma consola do Windows PowerShell num navegador da web, sem Windows PowerShell, o software de gestão remota ou a instalação Plug-in do browser necessária no dispositivo cliente. Tudo o que é necessário para executar a consola do Windows PowerShell baseada na web é um gateway de acesso do Windows PowerShell Web configurado corretamente e um browser de dispositivo do cliente que suporte a JavaScript e aceite cookies.

Exemplos de dispositivos cliente incluem computadores portáteis, computadores pessoais sem ser de trabalho, computadores emprestados, computadores tablet, quiosques Web, computadores sem sistema operativo baseado em Windows e browsers de telemóvel. Os profissionais de TI podem efetuar tarefas de gestão críticas em servidores remotos baseados no Windows a partir de dispositivos com acesso a uma ligação à Internet e a um browser.

Após a instalação de gateway com êxito e a configuração, os utilizadores podem aceder a consola do Windows PowerShell, utilizando um navegador da web. Quando os utilizadores abrem o site seguro do Windows PowerShell Web Access, eles podem ser executados uma consola do Windows PowerShell baseada na web após a autenticação com êxito.

Configuração do Windows PowerShell Web Access e a configuração é um processo em três etapas:

1. [Instalar o Windows PowerShell Web Access](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Configurar o Gateway](#configure-the-gateway)
1. [Configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule)

Antes de instalar e configurar o Windows PowerShell Web Access, recomendamos que leia este guia completo, que inclui instruções sobre como instalar, proteger e desinstalar o Windows PowerShell Web Access. O [utilizar a consola do PowerShell baseada na Web do Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11)) tópico descreve a forma como os utilizadores iniciam sessão na consola baseada na web e abrange as limitações e diferenças entre a consola do Windows PowerShell baseada na web e o  **PowerShell.exe** consola. Os utilizadores finais da consola baseada na web devem ler [utilizam o Web baseado em Windows PowerShell consola](use-the-web-based-windows-powershell-console.md), mas não é necessário ler o restante deste guia.

Este tópico fornece orientações detalhadas de operações servidor Web IIS; apenas os passos necessários para configurar o gateway do Windows PowerShell Web Access são descritos neste tópico. Para mais informações sobre como configurar e proteger Web sites no IIS, consulte os recursos da documentação do IIS na secção Consulte Também.

O diagrama seguinte mostra como funciona o Windows PowerShell Web Access.

![Diagrama do Acesso Web do Windows PowerShell](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Requisitos para executar o Acesso Web Windows PowerShell

Acesso Web do Windows PowerShell requer o servidor Web (IIS), o .NET Framework 4.5 e o Windows PowerShell 3.0 ou o Windows PowerShell 4.0 em execução no servidor no qual pretende executar o gateway. Pode instalar o Windows PowerShell Web Access num servidor que está a executar o Windows Server 2012 R2 ou Windows Server 2012, utilizando a adicionar funções e funcionalidades assistente no Gestor de servidores ou cmdlets de implementação do Windows PowerShell para o Gestor de servidores. Quando instala o Windows PowerShell Web Access, utilizando o Gestor de servidores ou respetivos cmdlets de implementação, funções e funcionalidades necessárias são adicionadas automaticamente como parte do processo de instalação.

Windows PowerShell Web Access permite aos utilizadores remotos aceder a computadores na sua organização utilizando o Windows PowerShell num navegador da web. Embora o Windows PowerShell Web Access é uma ferramenta de gestão prática e poderosa, o acesso baseado na web tem riscos de segurança e deve ser configurado de forma mais segura possível. Recomendamos que os administradores que configurarem o gateway do Windows PowerShell Web Access utilizam camadas de segurança disponíveis, ambas as regras de autorização baseadas em cmdlets incluídas no Windows PowerShell Web Access e segurança camadas que estão disponíveis no servidor Web ( IIS) e aplicações de terceiros. Esta documentação inclui exemplos não seguros apenas recomendados para ambientes de teste e exemplos recomendados para implementações seguras.

## <a name="browser-and-client-device-support"></a>Suporte de browsers e dispositivos cliente

Windows PowerShell Web Access suporta os seguintes navegadores de Internet. Apesar de browsers para dispositivos móveis não serem suportados oficialmente, muitos podem ser capazes de executar a consola do Windows PowerShell baseada na web.
Espera-se que outros browsers que aceitam cookies, executam JavaScript e executam Web sites HTTPS funcionem, mas são foram testados oficialmente.

### <a name="supported-desktop-computer-browsers"></a>Browsers para computadores de secretária suportados

- Windows Internet Explorer para Microsoft Windows 8.0, 9.0, 10.0 e 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m para Windows
- Apple Safari 5.1.2 para Windows
- Apple Safari 5.1.2 para Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Dispositivos móveis ou browsers testados minimamente

- Windows Phone 7 e 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)
- Apple Safari para sistema operativo iPhone 5.0.1
- Apple Safari para sistema operativo iPad 2 5.0.1

### <a name="browser-requirements"></a>Requisitos de browsers

Para utilizar a consola baseada na web do Windows PowerShell Web Access, os browsers tem de fazer o seguinte.

- Permita cookies do site de gateway do Windows PowerShell Web Access.
- Ser capaz de abrir e ler páginas HTTPS.
- Abrir e executar Web sites que utilizem JavaScript.

## <a name="recommended-quick-deployment"></a>Implementação rápida recomendada

Pode instalar o gateway do Windows PowerShell Web Access num servidor que está a executar o Windows Server 2012 R2 ou Windows Server 2012, utilizando qualquer um dos cmdlets do Windows PowerShell ou com a adicionar assistente funções e funcionalidades que é aberto a partir do Gestor de servidores. Para instalação e configuração rápidas, utilize os cmdlets do Windows PowerShell, conforme descrito nesta secção.

1. [Instalar o Windows PowerShell Web Access](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Configurar o Gateway](#configure-the-gateway)
1. [Configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access-using-powershell-cmdlets"></a>Instalar o Windows PowerShell Web Access com cmdlets do PowerShell

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Para instalar o Acesso Web Windows PowerShell utilizando cmdlets do Windows PowerShell

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados.

   - No ambiente de trabalho do Windows, com o botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **Executar como administrador**.
   - Sobre o Windows **começar** ecrã, clique com botão direito **Windows PowerShell**e, em seguida, clique em **executar como administrador**.

   > [!NOTE]
   > No Windows PowerShell 3.0 e 4.0, não é necessário para importar o módulo de cmdlet do Gestor de servidor para a sessão do Windows PowerShell antes de executar cmdlets que fazem parte do módulo. Um módulo é importado automaticamente na primeira vez que executa um cmdlet que faz parte do módulo.
   > Além disso, os cmdlets do Windows PowerShell não diferenciam maiúsculas de minúsculas.

1. Escreva o seguinte e, em seguida, prima **Enter**, onde *computer_name* representa um computador remoto no qual pretende instalar o Windows PowerShell Web Access, se aplicável. O parâmetro `-Restart` reinicia automaticamente os servidores de destino, se necessário.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   > [!NOTE]
   > Instalar o Windows PowerShell Web Access, utilizando cmdlets do Windows PowerShell não adicionar ferramentas de gestão de servidor Web (IIS) por predefinição. Se pretende instalar as ferramentas de gestão no mesmo servidor que o gateway do Windows PowerShell Web Access, adicione o `-IncludeManagementTools` parâmetro para o comando de instalação (conforme indicado neste passo). Se estiver a gerir o site do Windows PowerShell Web Access num computador remoto, instale o snap-in Gestor do IIS instalando [remoto Server Administration Tools para Windows 8.1](https://www.microsoft.com/en-us/download/details.aspx?id=39296) ou [administração remota do servidor Ferramentas para o Windows 8](https://www.microsoft.com/en-us/download/details.aspx?id=28972) no computador do qual pretende gerir o gateway.

   Para instalar funções e funcionalidades num VHD offline, tem de adicionar o parâmetro `-ComputerName` e o parâmetro `-VHD`. O parâmetro `-ComputerName` contém o nome do servidor onde pretende montar o VHD, e o parâmetro `-VHD` contém o caminho para o ficheiro VHD no servidor especificado.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Quando a instalação estiver concluída, certifique-se de que o Windows PowerShell Web Access foi instalado nos servidores de destino ao executar o `Get-WindowsFeature` cmdlet num servidor de destino, numa consola do Windows PowerShell que foi aberta com direitos de utilizador de elevados. Também pode verificar que o Windows PowerShell Web Access foi instalado na consola do Gestor de servidor, ao selecionar um servidor de destino no **todos os servidores** página e, em seguida, visualizar os **funções e funcionalidades** mosaico para o servidor selecionado. Também pode ver o ficheiro Leia-me para o Windows PowerShell Web Access.

1. Após a instalação do Windows PowerShell Web Access, lhe for pedido para rever o ficheiro Leia-me, que contém instruções de configuração básicas e necessárias para o gateway. Estas instruções de configuração também estão na seção a seguir [configurar o Gateway](#configure-the-gateway). O caminho para o arquivo Leiame é `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Configurar o Gateway

O **Install-PswaWebApplication** cmdlet é uma forma rápida de obter o Windows PowerShell Web Access configurado. Embora possa adicionar o parâmetro `UseTestCertificate` ao cmdlet `Install-PswaWebApplication` para instalar um certificado SSL autoassinado para efeitos de teste, não é um procedimento seguro; para um ambiente de produção seguro, utilize sempre um certificado SSL válido assinado por uma autoridade de certificação (AC). Os administradores podem substituir o certificado de teste por um certificado assinado à sua escolha utilizando a consola do Gestor do IIS.

Pode concluir a configuração de aplicação web do Windows PowerShell Web Access executando o `Install-PswaWebApplication` cmdlet ou efetuando os passos de configuração baseado na GUI no Gestor do IIS.
Por predefinição, o cmdlet instala a aplicação web, **pswa** (e um conjunto aplicacional para o mesmo, **pswa_pool**), no **Web Site predefinido** contentor, conforme mostrado no Gestor do IIS; se assim o desejar, pode instruir o cmdlet para alterar o contentor de sites predefinido do aplicativo web. O Gestor do IIS oferece opções de configuração disponíveis para aplicações Web, como alterar o número de porta ou o certificado SSL (Secure Sockets Layer).

> **![Nota de segurança](images/securitynote.jpeg) nota de segurança** é altamente recomendável que os administradores configurem o gateway para utilizar um certificado válido assinado por uma AC.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Para configurar o gateway do Acesso Web Windows PowerShell com um certificado de teste utilizando Install-PswaWebApplication

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell.

   - Na área de trabalho Windows, clique com botão direito **Windows PowerShell** na barra de tarefas.
   - Sobre o Windows **começar** ecrã, clique em **Windows PowerShell**.

2. Escreva o seguinte e, em seguida, prima **Enter**.

   `Install-PswaWebApplication -UseTestCertificate`

   > **![Nota de segurança](images/securitynote.jpeg) nota de segurança** o `UseTestCertificate` parâmetro só deve ser utilizado num ambiente de teste privado. Para um ambiente de produção seguro, recomendamos que utilize um certificado válido assinado por uma AC.

   Executar o cmdlet instala a aplicação web do Windows PowerShell Web Access dentro do contentor do IIS Default Web Site. O cmdlet cria a infraestrutura necessária para executar o Windows PowerShell Web Access no Web site predefinido, `https://<server_name>/pswa`. Para instalar a aplicação Web num Web site diferentes, forneça o nome do Web site adicionando o parâmetro `WebSiteName`. Para alterar o nome da aplicação Web (a predefinição é `pswa`), adicione o parâmetro `WebApplicationName`.

   As definições seguintes são configuradas ao executar o cmdlet. Pode alterá-las manualmente na consola do Gestor do IIS, se pretender.

   - Path: /pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

   **Exemplo**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

   Neste exemplo, o Web site resultante para o Windows PowerShell Web Access é `https://<server_name>/myWebApp`.

   > [!NOTE]
   > Não é possível iniciar sessão até que tenha sido concedido acesso ao site aos utilizadores adicionando regras de autorização. Para obter mais informações, consulte [configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule) e [regras de autorização e segurança recursos do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Para configurar o gateway do Acesso Web Windows PowerShell com um certificado genuíno utilizando Install-PswaWebApplication e o Gestor do IIS

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell.

   - Na área de trabalho Windows, clique com botão direito **Windows PowerShell** na barra de tarefas.
   - Sobre o Windows **começar** ecrã, clique em **Windows PowerShell**.

2. Escreva o seguinte e, em seguida, prima **Enter**.

   `Install-PswaWebApplication`

   As definições de gateway seguintes são configuradas ao executar o cmdlet. Pode alterá-las manualmente na consola do Gestor do IIS, se pretender. Também pode especificar valores para os parâmetros `WebsiteName` e `WebApplicationName` do cmdlet `Install-PswaWebApplication`.

   - Path: /pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

3. Abra a consola do Gestor do IIS efetuando um dos procedimentos seguintes.

   - Na área de trabalho Windows, inicie o Gestor de servidor clicando **Gestor de servidor** na barra de tarefas do Windows. Sobre o **ferramentas** menu no Gestor de servidores, clique em **Gestor de serviços de informação Internet (IIS)**.
   - Sobre o Windows **começar** ecrã, clique em **Gestor de servidor**.

4. No painel de árvore do Gerenciador do IIS, expanda o nó para o servidor no qual o Windows PowerShell Web Access está instalado até as **Sites** pasta está visível. Expanda a **Sites** pasta.

5. Selecione o Web site no qual instalou a aplicação web do Windows PowerShell Web Access.
   Na **ações** painel, clique em **enlaces**.

6. Na **enlace de Site** caixa de diálogo, clique em **Add**.

7. Na **Adicionar enlace de Site** caixa de diálogo a **tipo** campo, selecione **https**.

8. Na **certificado SSL** campo, selecione o certificado assinado no menu pendente.
   Clique em **OK**. Ver [para configurar um certificado SSL no Gestor do IIS](#to-configure-an-ssl-certificate-in-iis-manager) neste tópico para obter mais informações sobre como obter um certificado.

   A aplicação web do Windows PowerShell Web Access está agora configurada para utilizar o seu certificado SSL assinado.

   Pode acessar o Windows PowerShell Web Access abrindo `https://<server_name>/pswa` numa janela do browser.

   > [!NOTE]
   > Não é possível iniciar sessão até que tenha sido concedido acesso ao site aos utilizadores adicionando regras de autorização. Para obter mais informações, consulte [configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule), neste tópico, e [regras de autorização e segurança recursos do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Configurar uma regra de autorização restrita

Após instalação do Windows PowerShell Web Access e o gateway está configurado, os utilizadores podem abrir a página de início de sessão num browser, mas não consigo iniciar sessão até que o administrador do Windows PowerShell Web Access conceda explicitamente acesso de utilizadores. Controlo de acesso do Windows PowerShell Web Access é gerido com o conjunto de cmdlets do Windows PowerShell descritos na tabela seguinte. Não existe nenhuma GUI comparável para adicionar ou gerir regras de autorização. Para obter mais informações sobre os cmdlets do Windows PowerShell Web Access, consulte os tópicos de referência do cmdlet [Cmdlets do Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Para obter mais detalhes sobre regras de autorização do Windows PowerShell Web Access e a segurança, consulte [regras de autorização e segurança recursos do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Para adicionar uma regra de autorização restrita

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados.

   - No ambiente de trabalho do Windows, com o botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **Executar como administrador**.
   - Sobre o Windows **começar** ecrã, clique com botão direito **Windows PowerShell**e, em seguida, clique em **executar como administrador**.

2. Passo opcional para restringir o acesso de utilizador utilizando configurações de sessão: Certifique-se de que as configurações de sessão que pretende utilizar nas suas regras já existem. Se ainda não tiver sido criados, utilize as instruções para a criação de configurações de sessão no [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Escreva o seguinte e, em seguida, prima **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Esta regra de autorização permite um acesso de utilizador específico a um computador na rede à qual tenham acesso, com acesso a uma configuração específica de sessão que tem um âmbito ao scripting típico do utilizador e às necessidades de cmdlet.

   No exemplo seguinte, é concedido o acesso a um utilizador com o nome `JSmith` no domínio `Contoso` para gerir o computador `Contoso_214` e utilizar uma configuração de sessão com o nome `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Certifique-se de que a regra foi criada através da execução do `Get-PswaAuthorizationRule` cmdlet, ou `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

   Por exemplo, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Depois de ter configurado uma regra de autorização, está pronto para os utilizadores autorizados iniciar sessão na consola baseada na web e começar a utilizar o Windows PowerShell Web Access.

## <a name="custom-deployment"></a>Implementação personalizada

Pode instalar o gateway do Windows PowerShell Web Access num servidor que está a executar o Windows Server 2012 R2 ou Windows Server 2012, utilizando a adicionar assistente funções e funcionalidades no Gestor de servidores.
Após a instalação do Windows PowerShell Web Access, pode personalizar a configuração do gateway no Gerenciador do IIS.

### <a name="install-windows-powershell-web-access-using-the-add-roles-and-features-wizard"></a>Instalar o Windows PowerShell Web Access com o Assistente de funcionalidades e para adicionar funções

1. Se o Gestor de servidor já estiver aberto, avance para o passo seguinte. Se o Gestor de servidor não esteja ainda aberto, abra-o efetuando um dos seguintes procedimentos.

   - Na área de trabalho Windows, inicie o Gestor de servidor clicando **Gestor de servidor** na barra de tarefas do Windows.
   - Sobre o Windows **começar** ecrã, clique em **Gestor de servidor**.

2. Sobre o **Manage** menu, clique em **para adicionar funções e funcionalidades**.

3. Na página **Selecionar tipo de instalação**, selecione **Instalação baseada em funções ou baseada em funcionalidades**.
   Clique em **Seguinte**.

4. Sobre o **selecionar servidor de destino** página, selecione um servidor no agrupamento de servidores ou selecione um VHD offline. Para selecionar um VHD offline como servidor de destino, primeiro selecione o servidor em que pretende montar o VHD e, em seguida, selecione o ficheiro VHD. Para obter informações sobre como adicionar servidores ao agrupamento de servidores, consulte a ajuda do Gestor de servidores. Depois de selecionar o servidor de destino, clique em **seguinte**.

5. Sobre o **selecionar funcionalidades** página do assistente, expanda **Windows PowerShell**e, em seguida, selecione **Windows PowerShell Web Access**.

6. Tenha em atenção que lhe é pedido para adicionar funcionalidades necessárias, como o .NET Framework 4.5 e serviços de função do Servidor Web (IIS). Adicione as funcionalidades necessárias e continue.

   > [!NOTE]
   > Também é instalar o Windows PowerShell Web Access, utilizando o Assistente de funcionalidades de adicionar funções e instala o servidor Web (IIS), incluindo o snap-in Gestor do IIS. O snap-in e outras ferramentas de gestão do IIS são instaladas por predefinição se utilizar o Assistente Adicionar funções e funcionalidades. Se instalar o Windows PowerShell Web Access, utilizando cmdlets do Windows PowerShell, conforme descrito no procedimento seguinte, as ferramentas de gestão não são adicionadas por predefinição.

7. Sobre o **confirmar seleções de instalação** página, se os ficheiros de funcionalidade para Windows PowerShell Web Access não são armazenadas no servidor de destino que selecionou no passo 4, clique em **Especifica um caminho de origem alternativo**e forneça o caminho para os ficheiros de funcionalidade. Caso contrário, clique em **instalar**.

8. Depois de clicar em **instale**, o **progresso da instalação** página apresenta o progresso da instalação, os resultados e mensagens, tais como avisos, falhas ou passos de configuração de pós-instalação necessário para o Windows PowerShell Web Access. Após a instalação do Windows PowerShell Web Access, lhe for pedido para rever o ficheiro Leia-me, que contém instruções de configuração básicas e necessárias para o gateway. Estas instruções também estão incluídas neste tópico. O caminho para o arquivo Leiame é `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Configurar o gateway

As instruções nesta secção destinam-se instalar a aplicação web do Windows PowerShell Web Access num subdiretório e não no diretório de raiz do seu Web site. Este procedimento é o equivalente baseado na GUI das ações efetuadas pelo cmdlet `Install-PswaWebApplication`. Esta secção também inclui instruções sobre como utilizar o Gestor de IIS para configurar o gateway do Windows PowerShell Web Access como um Web site de raiz.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>Para utilizar o Gestor do IIS para configurar o gateway num Web site existente

1. Abra a consola do Gestor do IIS efetuando um dos procedimentos seguintes.

   - Na área de trabalho Windows, inicie o Gestor de servidor clicando **Gestor de servidor** na barra de tarefas do Windows. Sobre o **ferramentas** menu no Gestor de servidores, clique em **Gestor de serviços de informação Internet (IIS)**.
   - Sobre o Windows **começar** ecrã, escreva qualquer parte do nome **Gestor de serviços de informação Internet (IIS)**. Clique no atalho será apresentado no **aplicações** resultados.

2. Crie um novo conjunto aplicacional para o Windows PowerShell Web Access. Expanda o nó do servidor de gateway no painel de árvore do Gerenciador do IIS, selecione **Pools de aplicativos**e clique em **adicionar conjunto aplicacional** no **ações** painel.

3. Adicionar um novo conjunto aplicacional com o nome **pswa_pool**, ou forneça outro nome. Clique em **OK**.

4. No painel de árvore do Gerenciador do IIS, expanda o nó para o servidor no qual o Windows PowerShell Web Access está instalado até as **Sites** pasta está visível. Selecione o **Sites** pasta.

5. Com o botão direito do Web site (por exemplo, **Web Site predefinido**) para que gostaria de adicionar o site do Windows PowerShell Web Access e, em seguida, clique em **Adicionar aplicação**.

6. Na **Alias** campo, escreva pswa ou forneça outro alias. O alias torna-se o nome de diretório virtual. Por exemplo, **pswa** no URL seguinte representa o alias especificado neste passo: `https://<server-name>/pswa`.

7. Na **conjunto aplicacional** campo, selecione o conjunto aplicacional que criou no passo 3.

8. Na **caminho físico** campo, navegue para a localização do aplicativo. Pode utilizar a localização predefinida, `$env:windir/Web/PowerShellWebAccess/wwwroot`. Clique em **OK**.

9. Siga os passos no procedimento [para configurar um certificado SSL no Gestor do IIS](#to-configure-an-ssl-certificate-in-iis-manager) neste tópico.

10. ![](images/SecurityNote.jpeg) Passo opcional de segurança:

    Com o site selecionado no painel de árvore, faça duplo clique em **definições de SSL** no painel de conteúdo.
    Selecione **exigir SSL**e, em seguida, no **ações** painel, clique em **aplicar**. Opcionalmente, na **definições de SSL** painel, pode exigir que os utilizadores a ligar ao site do Windows PowerShell Web Access têm certificados de cliente. Os certificados de cliente ajudam a verificar a identidade de um utilizador do dispositivo cliente. Para obter mais informações sobre como os certificados de cliente podem aumentar a segurança do Windows PowerShell Web Access, consulte [regras de autorização e segurança recursos do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md) neste guia.

11. Abra uma sessão de browser num dispositivo cliente. Para obter mais informações sobre dispositivos e browsers suportados, consulte [Browser e de dispositivo do cliente suportar](#browser-and-client-device-support) neste tópico.

12. Abra o novo Web site do Windows PowerShell Web Access **https://\<*nome do servidor gateway*\>/pswa**.

    O browser deve exibir a consola início de sessão página do Windows PowerShell Web Access.

    > [!NOTE]
    > Não é possível iniciar sessão até que tenha sido concedido acesso ao site aos utilizadores adicionando regras de autorização. Para obter mais informações, consulte [configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule), neste tópico, e [regras de autorização e segurança recursos do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. Numa sessão do Windows PowerShell que foi aberta com direitos de utilizador elevados (executar como administrador), execute o script seguinte, no qual *nome_conjunto_aplicacional* representa o nome do conjunto aplicacional que criou no passo 3, Para conceder o conjunto aplicacional direitos de acesso ao ficheiro de autorização.

    ```powershell
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Para ver os direitos de acesso existentes no ficheiro de autorização, execute o seguinte comando:

    ```powershell
    c:\windows\system32\icacls.exe $authorizationFile
    ```

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>Para utilizar o Gestor do IIS para configurar o gateway como um Web site de raiz com um certificado de teste

1. Abra a consola do Gestor do IIS efetuando um dos procedimentos seguintes.

   - Na área de trabalho Windows, inicie o Gestor de servidor clicando **Gestor de servidor** na barra de tarefas do Windows. Sobre o **ferramentas** menu no Gestor de servidores, clique em **Gestor de serviços de informação Internet (IIS)**.
   - Sobre o Windows **começar** ecrã, escreva qualquer parte do nome **Gestor de serviços de informação Internet (IIS)**. Clique no atalho será apresentado no **aplicações** resultados.

1. No painel de árvore do Gerenciador do IIS, expanda o nó para o servidor no qual o Windows PowerShell Web Access está instalado até as **Sites** pasta está visível. Selecione o **Sites** pasta.

1. Na **ações** painel, clique em **adicionar Web site**.

1. Escreva um nome para o Web site, tal como **Windows PowerShell Web Access**.

1. É criado automaticamente um conjunto aplicacional para o novo Web site. Para utilizar um conjunto aplicacional diferente, clique em **selecione** para selecionar um conjunto aplicacional para associar o novo Web site. Selecione o conjunto aplicacional alternativo na **selecionar conjunto aplicacional** caixa de diálogo e clique em **OK**.

1. Na **caminho físico** texto caixa, navegue até % windir%/Web/PowerShellWebAccess/wwwroot.

1. Na **tipo** campo a **enlace** área, selecione **https**.

1. Atribua um número de porta ao Web site que ainda não esteja a ser utilizado por outro site ou aplicação.
   Para localizar portas abertas, pode executar o **netstat** comando numa janela de linha de comando. O número de porta predefinido é 443.

   Altere a porta predefinida se outro Web site já estiver a utilizar a 443 ou se tiver outros motivos de segurança para alterar o número de porta. Se outro Web site que está a executar no seu servidor de gateway estiver a utilizar a porta selecionada, um aviso é apresentado quando clica **OK** no **adicionar Web site** caixa de diálogo. Tem de utilizar uma porta não utilizada para executar o Windows PowerShell Web Access.

1. Opcionalmente, se for necessário para a sua organização, especifique um nome de anfitrião que faça sentido para sua organização e utilizadores, tal como **`www.contoso.com`**. Clique em **OK**.

1. Para um ambiente de produção mais seguro, recomendamos vivamente que forneça um certificado válido assinado por uma AC. Tem de fornecer um certificado SSL, uma vez que os utilizadores só podem ligar para o Windows PowerShell Web Access por meio de um Web site HTTPS. Ver [para configurar um certificado SSL no Gestor do IIS](#to-configure-an-ssl-certificate-in-iis-manager) neste tópico para obter mais informações sobre como obter um certificado.

1. Clique em **OK** para fechar a **adicionar Web site** caixa de diálogo.

1. Numa sessão do Windows PowerShell que foi aberta com direitos de utilizador elevados (executar como administrador), execute o script seguinte, no qual _nome_conjunto_aplicacional_ representa o nome do conjunto aplicacional que criou no passo 4, Para conceder o conjunto aplicacional direitos de acesso ao ficheiro de autorização.

   ```powershell
   $applicationPoolName = "<application_pool_name>"
   $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
   c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
   ```

   Para ver os direitos de acesso existentes no ficheiro de autorização, execute o seguinte comando:

   ```powershell
   c:\windows\system32\icacls.exe $authorizationFile
   ```

1. Com o novo site selecionado no painel de árvore do Gestor de IIS, clique em **começar** no **ações** painel para iniciar o Web site.

1. Abra uma sessão de browser num dispositivo cliente. Para obter mais informações sobre dispositivos e browsers suportados, consulte [Browser e de dispositivo do cliente suportar](#browser-and-client-device-support) neste documento.

1. Abra o novo site do Windows PowerShell Web Access.

   Uma vez que o Web site de raiz aponta para a pasta do Windows PowerShell Web Access, o browser deverá apresentar a página de início de sessão do Windows PowerShell Web Access, quando abre `https://<gateway_server_name>`. Não é preciso adicionar **/pswa** para o URL.

   > [!NOTE]
   > Não é possível iniciar sessão até que tenha sido concedido acesso ao site aos utilizadores adicionando regras de autorização. Para obter mais informações, consulte [configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule), neste tópico, e [regras de autorização e segurança recursos do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configuring-a-restrictive-authorization-rule"></a>Configurar uma regra de autorização restrita

Após instalação do Windows PowerShell Web Access e o gateway está configurado, os utilizadores podem abrir a página de início de sessão num browser, mas não consigo iniciar sessão até que o administrador do Windows PowerShell Web Access conceda explicitamente acesso de utilizadores. Controlo de acesso do Windows PowerShell Web Access é gerido com o conjunto de cmdlets do Windows PowerShell descritos na tabela seguinte. Não existe nenhuma GUI comparável para adicionar ou gerir regras de autorização. Para obter mais informações sobre os cmdlets do Windows PowerShell Web Access, consulte os tópicos de referência do cmdlet [Cmdlets do Windows PowerShell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Para obter mais detalhes sobre regras de autorização do Windows PowerShell Web Access e a segurança, consulte [regras de autorização e segurança recursos do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="adding-a-restrictive-authorization-rule"></a>Adicionar uma regra de autorização restrita

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados.

   - No ambiente de trabalho do Windows, com o botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **Executar como administrador**.
   - Sobre o Windows **começar** ecrã, clique com botão direito **Windows PowerShell**e, em seguida, clique em **executar como administrador**.

1. ![Nota de segurança](images/SecurityNote.jpeg) Passo opcional para restringir o acesso de utilizador utilizando configurações de sessão:

   Certifique-se de que as configurações de sessão que pretende utilizar nas suas regras já existem. Se ainda não tiver sido criados, utilize as instruções para a criação de configurações de sessão no [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Escreva o seguinte e, em seguida, prima **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Esta regra de autorização permite um acesso de utilizador específico a um computador na rede para os quais normalmente tenham acesso, com acesso a uma configuração específica de sessão que tem um âmbito para o utilizador '™ necessidades de criação de scripts e o cmdlet típicas no s.

   No exemplo seguinte, é concedido o acesso a um utilizador com o nome `JSmith` no domínio `Contoso` para gerir o computador `Contoso_214` e utilizar uma configuração de sessão com o nome `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

1. Certifique-se de que a regra foi criada através da execução de `Get-PswaAuthorizationRule` cmdlet, ou `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`.

   Por exemplo, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

   Depois de ter configurado uma regra de autorização, está pronto para os utilizadores autorizados iniciar sessão na consola baseada na web e começar a utilizar o Windows PowerShell Web Access.

## <a name="configure-a-genuine-certificate"></a>Configurar um certificado genuíno

Num ambiente de produção seguro, utilize sempre um certificado SSL válido assinado por uma autoridade de certificação (AC). O procedimento nesta secção descreve como obter e aplicar um certificado SSL válido a partir de uma AC.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Para configurar um certificado SSL no Gestor do IIS

1. No painel de árvore do Gerenciador do IIS, selecione o servidor no qual está instalado o Windows PowerShell Web Access.

1. No painel de conteúdo, faça duplo clique **certificados de servidor**.

1. Na **ações** painel, efetue um dos seguintes procedimentos. Para obter mais informações sobre como configurar certificados de servidor no IIS, consulte [configurar certificados de servidor no IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).

   - Clique em **importar** para importar um certificado válido existente a partir de uma localização na sua rede.
   - Clique em **criar pedido de certificado** para pedir um certificado a partir de uma AC, tal como [VeriSign](https://www.verisign.com/), [Thawte](https://www.thawte.com/), ou [GeoTrust](https://www.geotrust.com/). O nome comum do certificado tem de corresponder ao cabeçalho do anfitrião no pedido.

     Por exemplo, se o browser cliente pedir `http://www.contoso.com/`, em seguida, o nome comum também tem de ser `http://www.contoso.com/`. Esta é a opção mais segura e recomendada para fornecer o gateway do Windows PowerShell Web Access com um certificado.

   - Clique em **criar um certificado autoassinado** para criar um certificado que pode utilizar imediatamente e ser assinado mais tarde por uma AC se assim o desejar. Especifique um nome amigável para o certificado autoassinado, tal como **Windows PowerShell Web Access**. Esta opção não é considerada segura e é recomendada apenas para um ambiente de teste privado.

1. Depois de criar ou obter um certificado, selecione o Web site ao qual o certificado é aplicado (por exemplo, **Web Site predefinido**) no Gerenciador do IIS painel de árvore e, em seguida, clique em **enlaces** no **Ações** painel.

1. Na **Adicionar enlace de Site** caixa de diálogo caixa, adicione um **https** de enlace para o site, se um não estiver em exibição. Se não estiver a utilizar um certificado autoassinado, especifique o nome de anfitrião a partir do passo 3 deste procedimento. Se estiver a utilizar um certificado autoassinado, este passo não é necessário.

1. Selecione o certificado obtido ou criado no passo 3 deste procedimento e, em seguida, clique em **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>Utilizar a consola do Windows PowerShell baseada na Web

Após instalação do Windows PowerShell Web Access e a configuração do gateway está concluída conforme descrito neste tópico, está pronta a utilizar a consola do Windows PowerShell baseada na web. Para obter mais informações sobre como obter a utilizar na consola baseada na web, consulte [utilizar a consola do PowerShell baseada na Web do Windows](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Veja Também

[Serviços de informação Internet (IIS) 7.0 documentação](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10))

[Ajuda do IIS Manager 7.0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732664(v=ws.11))

[Configurar a segurança do servidor Web (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731278(v=ws.10))

[Recursos de implantação de IPsec](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10))
