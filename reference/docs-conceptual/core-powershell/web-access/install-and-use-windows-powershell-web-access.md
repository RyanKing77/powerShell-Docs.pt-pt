---
ms.date: 2017-08-23
keywords: PowerShell, o cmdlet
title: instalar e utilizar o acesso web windows powershell
ms.openlocfilehash: 2ad7a701dbb464088d6ed47d49a8dc3fb9b911f8
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="install-and-use-windows-powershell-web-access"></a>Instalar e Utilizar o Acesso Web Windows PowerShell

Atualizada: 5 de Novembro de 2013 (editado: 23 de Agosto de 2017)

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Introdução

Windows PowerShell Web Access, introduzida pela primeira vez no Windows Server 2012, age como um gateway do Windows PowerShell, proporcionando uma consola do Windows PowerShell baseada na web, que é direcionada para um computador remoto. Permite que os profissionais de TI executar comandos do Windows PowerShell e scripts a partir de uma consola do Windows PowerShell num browser, sem qualquer do Windows PowerShell, o software de gestão remota ou instalação Plug-in do browser necessária no dispositivo cliente. Tudo o que é necessário executar a consola do Windows PowerShell baseada na web é um gateway de acesso Web Windows PowerShell corretamente configurados e um browser do dispositivo cliente que suporte JavaScript e aceite cookies.

Exemplos de dispositivos cliente incluem computadores portáteis, computadores pessoais sem ser de trabalho, computadores emprestados, computadores tablet, quiosques Web, computadores sem sistema operativo baseado em Windows e browsers de telemóvel. Os profissionais de TI podem efetuar tarefas de gestão críticas em servidores remotos baseados no Windows a partir de dispositivos com acesso a uma ligação à Internet e a um browser.

Após a configuração do gateway com êxito e a configuração, os utilizadores podem aceder uma consola do Windows PowerShell, utilizando um browser. Quando os utilizadores abrem o Web site do Windows PowerShell Web Access protegido, podem executar uma consola do Windows PowerShell baseada na web após a autenticação com êxito.

A configuração do acesso Web Windows PowerShell e a configuração é um processo de três passos:

1. [Instalar o acesso Web Windows PowerShell](#install-windows-powershell-web-access)
1. [Configurar o Gateway](#configure-the-gateway)
1. [Configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule)

Antes de instalar e configurar o acesso Web Windows PowerShell, recomendamos que leia deste guia completo, que inclui instruções sobre como instalar, proteger e desinstalar o acesso Web Windows PowerShell.
O [utilizar a consola do PowerShell baseada na Web do Windows](https://technet.microsoft.com/library/hh831417(v=ws.11).aspx) tópico descreve a forma como os utilizadores iniciam sessão consola baseada na web e abrange as limitações e diferenças entre a consola do Windows PowerShell baseada na web e o  **PowerShell.exe** consola. Os utilizadores finais da consola baseada na web devem ler [utilize Web com base em consola do Windows PowerShell](use-the-web-based-windows-powershell-console.md), mas não é necessário ler o resto deste guia.

Este tópico fornece orientações de operações do servidor Web IIS aprofundadas; apenas os passos necessários para configurar o gateway de acesso Web Windows PowerShell são descritos neste tópico. Para mais informações sobre como configurar e proteger Web sites no IIS, consulte os recursos da documentação do IIS na secção Consulte Também.

O diagrama seguinte mostra como funciona o acesso Web Windows PowerShell.

![Diagrama do Acesso Web do Windows PowerShell](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Requisitos para executar o Acesso Web Windows PowerShell

Acesso Web Windows PowerShell requer o servidor Web (IIS), .NET Framework 4.5 e Windows PowerShell 3.0 ou estar em execução no servidor no qual pretende executar o gateway do Windows PowerShell 4.0. Pode instalar acesso Web Windows PowerShell num servidor que está a executar o Windows Server 2012 R2 ou Windows Server 2012 utilizando o ou o Assistente Adicionar funções e funcionalidades no Gestor de servidores ou cmdlets de implementação do Windows PowerShell para o Gestor de servidor. Quando instalar o acesso Web Windows PowerShell utilizando o Gestor de servidores ou os cmdlets de implementação, funções e funcionalidades necessárias são adicionadas automaticamente como parte do processo de instalação.

Acesso Web Windows PowerShell permite que os utilizadores remotos aceder a computadores na sua organização através do Windows PowerShell num web browser. Embora o acesso Web Windows PowerShell é uma ferramenta de gestão prática e poderosa, o acesso baseado na web tem riscos de segurança e deve ser configurado de forma mais segura possível. Recomendamos que os administradores que configurarem o gateway de acesso Web Windows PowerShell utilizam camadas de segurança disponíveis, ambas as regras de autorização baseada em cmdlet incluídos com o acesso Web Windows PowerShell e segurança camadas que estão disponíveis no servidor Web ( IIS) e aplicações de terceiros. Esta documentação inclui exemplos não seguros apenas recomendados para ambientes de teste e exemplos recomendados para implementações seguras.

## <a name="browser-and-client-device-support"></a>Suporte de browsers e dispositivos cliente

Acesso Web Windows PowerShell suporta os browsers seguintes.
Embora browsers para dispositivos móveis não são suportados oficialmente, muitos poderá executar a consola do Windows PowerShell baseada na web. Espera-se que outros browsers que aceitam cookies, executam JavaScript e executam Web sites HTTPS funcionem, mas são foram testados oficialmente.

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

## <a name="recommended-quick-deployment"></a>Implementação rápida recomendada

Pode instalar o gateway de acesso Web Windows PowerShell num servidor que está a executar o Windows Server 2012 R2 ou Windows Server 2012, utilizando qualquer um dos cmdlets do Windows PowerShell ou utilizando o Assistente de funcionalidades que aberto a partir do Gestor de servidores e adicionar funções. Para instalação e configuração rápidas, utilize os cmdlets do Windows PowerShell, conforme descrito nesta secção.

1. [Instalar o acesso Web Windows PowerShell](#install-Windows-powershell-web-access)
1. [Configurar o Gateway](#configure-the-gateway)
1. [Configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access"></a>Instalar o acesso Web Windows PowerShell

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Para instalar o Acesso Web Windows PowerShell utilizando cmdlets do Windows PowerShell

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados.
    - No ambiente de trabalho do Windows, com o botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **Executar como administrador**.
    - O Windows **iniciar** ecrã, faça duplo clique **do Windows PowerShell**e, em seguida, clique em **executar como administrador**.

    >**![Tenha em atenção](images/note.jpeg) nota** no Windows PowerShell 3.0 e 4.0, é necessário importar o módulo de cmdlet do Gestor de servidor para a sessão do Windows PowerShell antes de executar os cmdlets que fazem parte do módulo. Um módulo é importado automaticamente na primeira vez que executa um cmdlet que faz parte do módulo. Além disso, os cmdlets do Windows PowerShell não são maiúsculas e minúsculas.

1. Escreva o seguinte e, em seguida, prima **Enter**, onde *nome_do_computador* representa um computador remoto no qual pretende instalar o acesso Web Windows PowerShell, se aplicável. O parâmetro `-Restart` reinicia automaticamente os servidores de destino, se necessário.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   >**![Tenha em atenção](images/note.jpeg) nota**
   >
   >Instalar o acesso Web Windows PowerShell utilizando cmdlets do Windows PowerShell não adicionar ferramentas de gestão de servidor Web (IIS) por predefinição. Se pretender instalar as ferramentas de gestão no mesmo servidor que o gateway de acesso Web Windows PowerShell, adicionar o `-IncludeManagementTools` parâmetro para o comando de instalação (conforme indicado neste passo). Se estiver a gerir o site do acesso Web Windows PowerShell de um computador remoto, instale o snap-in Gestor do IIS instalando [remoto servidor administração Toolsfor Windows 8.1](http://go.microsoft.com/fwlink/?LinkID=304145) ou [administração remota do servidor Ferramentas para o Windows 8](http://go.microsoft.com/fwlink/p/?LinkID=238560) no computador a partir do qual pretende gerir o gateway.
   
   Para instalar funções e funcionalidades num VHD offline, tem de adicionar o parâmetro `-ComputerName` e o parâmetro `-VHD`. O parâmetro `-ComputerName` contém o nome do servidor onde pretende montar o VHD, e o parâmetro `-VHD` contém o caminho para o ficheiro VHD no servidor especificado.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Quando a instalação estiver concluída, certifique-se de que o acesso Web Windows PowerShell foi instalado nos servidores de destino executando o **Get-WindowsFeature** cmdlet num servidor de destino, numa consola do Windows PowerShell que foi aberta com direitos de utilizador elevados. Também pode verificar que o acesso Web Windows PowerShell foi instalado na consola do Gestor de servidores, selecionando um servidor de destino no **todos os servidores** página e, em seguida, visualizar o **funções e funcionalidades** mosaico para o servidor selecionado. Também pode ver o ficheiro Leia-me do acesso Web Windows PowerShell.

1. Depois do acesso Web Windows PowerShell está instalado, lhe for pedido para rever o ficheiro Leia-me, o qual contém instruções de configuração básicas e necessárias para o gateway. Estas instruções de configuração também estão na secção seguinte, [configurar o Gateway](#configure-the-gateway). O caminho para o ficheiro Leia-me é **c:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt**.

### <a name="configure-the-gateway"></a>Configurar o Gateway

O **Install-PswaWebApplication** cmdlet é uma forma rápida de obter acesso Web Windows PowerShell configurados. Embora possa adicionar o parâmetro `UseTestCertificate` ao cmdlet `Install-PswaWebApplication` para instalar um certificado SSL autoassinado para efeitos de teste, não é um procedimento seguro; para um ambiente de produção seguro, utilize sempre um certificado SSL válido assinado por uma autoridade de certificação (AC).
Os administradores podem substituir o certificado de teste por um certificado assinado à sua escolha utilizando a consola do Gestor do IIS.

Pode concluir a configuração de aplicação web do Windows PowerShell Web Access executando o `Install-PswaWebApplication` cmdlet ou efetuando os passos de configuração baseada na GUI no Gestor do IIS. Por predefinição, o cmdlet instala a aplicação web, **pswa** (e um conjunto aplicacional, **pswa_pool**), além de **Default Web Site** contentor, conforme mostrado no Gestor do IIS; se assim o desejar, pode instruir o cmdlet para alterar o contentor de sites predefinido da aplicação web. O Gestor do IIS oferece opções de configuração disponíveis para aplicações Web, como alterar o número de porta ou o certificado SSL (Secure Sockets Layer).

>**![Nota de segurança](images/securitynote.jpeg) nota de segurança**
> 
>Recomendamos vivamente que os administradores configurem o gateway para utilizar um certificado válido assinado por uma AC. 

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Para configurar o gateway do Acesso Web Windows PowerShell com um certificado de teste utilizando Install-PswaWebApplication

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell.

    - No ambiente de trabalho do Windows, clique com botão direito **do Windows PowerShell** na barra de tarefas.

    - O Windows **iniciar** ecrã, clique em **do Windows PowerShell**.

2. Escreva o seguinte e, em seguida, prima **Enter**.

    **Install-PswaWebApplication -UseTestCertificate**

  >**![Nota de segurança](images/securitynote.jpeg) nota de segurança**
  >
  >O parâmetro `UseTestCertificate` só deve ser utilizado num ambiente de teste privado. Para um ambiente de produção seguro, recomendamos que utilize um certificado válido assinado por uma AC.

Executar o cmdlet instala a aplicação de web de acesso Web Windows PowerShell no contentor IIS Default Web Site. O cmdlet cria a infraestrutura necessária para executar o acesso Web Windows PowerShell no Web site predefinido, `https://<server_name>/pswa`. Para instalar a aplicação Web num Web site diferentes, forneça o nome do Web site adicionando o parâmetro `WebSiteName`. Para alterar o nome da aplicação Web (a predefinição é `pswa`), adicione o parâmetro `WebApplicationName`.

As definições seguintes são configuradas ao executar o cmdlet. Pode alterá-las manualmente na consola do Gestor do IIS, se pretender.

- Path: /pswa
- ApplicationPool: pswa_pool
- EnabledProtocols: http
- PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

**Exemplo**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

Neste exemplo, o Web site resultante para o acesso Web Windows PowerShell é https://\<*server_name*\>/myWebApp.

>**![Tenha em atenção](images/note.jpeg) nota** 
> 
>Não é possível iniciar sessão até que tenha sido concedido acesso ao site aos utilizadores adicionando regras de autorização. Para obter mais informações, consulte [configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule) e [regras de autorização e segurança funcionalidades de acesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Para configurar o gateway do Acesso Web Windows PowerShell com um certificado genuíno utilizando Install-PswaWebApplication e o Gestor do IIS

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell.

    - No ambiente de trabalho do Windows, clique com botão direito **do Windows PowerShell** na barra de tarefas.

    - O Windows **iniciar** ecrã, clique em **do Windows PowerShell**.

2. Escreva o seguinte e, em seguida, prima **Enter**.

    **Install-PswaWebApplication**

    As definições de gateway seguintes são configuradas ao executar o cmdlet.
    Pode alterá-las manualmente na consola do Gestor do IIS, se pretender.
    Também pode especificar valores para os parâmetros `WebsiteName` e `WebApplicationName` do cmdlet `Install-PswaWebApplication`.

    - Path: /pswa

    - ApplicationPool: pswa_pool

    - EnabledProtocols: http

    - PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

3. Abra a consola do Gestor do IIS efetuando um dos procedimentos seguintes.

    - No ambiente de trabalho do Windows, inicie o Gestor de servidores, clicando em **Gestor de servidor** na barra de tarefas do Windows. No **ferramentas** menu no Gestor de servidores, clique em **Gestor dos serviços de informação Internet (IIS)**.

    - O Windows **iniciar** ecrã, clique em **Gestor de servidor**.

4. No painel de árvore do Gestor de IIS, expanda o nó para o servidor no qual o acesso Web Windows PowerShell está instalado até o **Sites** pasta está visível. Expanda o **Sites** pasta.

5. Selecione o Web site no qual instalou a aplicação web do acesso Web Windows PowerShell. No **ações** painel, clique em **enlaces**.

6. No **enlace de Site** caixa de diálogo, clique em **adicionar**.

7. No **Adicionar enlace de Site** caixa de diálogo a **tipo** campo, selecione **https**.

8. No **certificado SSL** campo, selecione o certificado assinado no menu pendente. Clique em **OK**. Consulte [para configurar um certificado SSL no Gestor do IIS](#to-configure-an-ssl-certificate-in-iis-Manager) neste tópico para obter mais informações sobre como obter um certificado.

    A aplicação web do Windows PowerShell Web Access está agora configurada para utilizar o certificado SSL assinado.

    Pode aceder ao acesso Web Windows PowerShell abrindo **https://\<server_name\>/pswa** numa janela do browser.

>**![Tenha em atenção](images/note.jpeg) nota** 
> 
>Não é possível iniciar sessão até que tenha sido concedido acesso ao site aos utilizadores adicionando regras de autorização. 
>Para obter mais informações, consulte [configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule), neste tópico, e [regras de autorização e segurança funcionalidades de acesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Configurar uma regra de autorização restrita

Depois de acesso Web Windows PowerShell está instalado e o gateway está configurado, os utilizadores podem abrir a página de início de sessão num browser, mas não conseguirão iniciar sessão até que o administrador do acesso Web Windows PowerShell conceda explicitamente acesso de utilizadores. Controlo de acesso de acesso Web Windows PowerShell é gerido utilizando o conjunto de cmdlets do Windows PowerShell descritos na seguinte tabela. Não existe nenhuma GUI comparável para adicionar ou gerir regras de autorização. Para obter mais informações sobre os cmdlets de acesso Web Windows PowerShell, consulte os tópicos de referência de cmdlet, [Cmdlets do Windows PowerShell Web Access](cmdlets/web-access-cmdlets.md).

Para obter mais detalhes sobre regras de autorização de acesso Web Windows PowerShell e a segurança, consulte [regras de autorização e segurança funcionalidades de acesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Para adicionar uma regra de autorização restrita

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados.

    - No ambiente de trabalho do Windows, com o botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **Executar como administrador**.

    - O Windows **iniciar** ecrã, faça duplo clique **do Windows PowerShell**e, em seguida, clique em **executar como administrador**.

2. Passo opcional para restringir o acesso de utilizador utilizando configurações de sessão: Certifique-se de que as configurações de sessão que pretende utilizar nas suas regras já existem. Se ainda não tiver sido criados, utilize as instruções para a criação de configurações de sessão no [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Escreva o seguinte e, em seguida, prima **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Esta regra de autorização permite um acesso de utilizador específico a um computador na rede a que normalmente tenham acesso, com o acesso a uma configuração específica de sessão que tem um âmbito ao scripting típico do utilizador e tem de cmdlet.
   
   No exemplo seguinte, é concedido o acesso a um utilizador com o nome `JSmith` no domínio `Contoso` para gerir o computador `Contoso_214` e utilizar uma configuração de sessão com o nome `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Certifique-se de que a regra foi criada através da execução de `Get-PswaAuthorizationRule` cmdlet, ou `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

5. Por exemplo, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Depois de ter configurado uma regra de autorização, está pronto para os utilizadores autorizados iniciar sessão na consola baseada na web e começar a utilizar o acesso Web Windows PowerShell.

## <a name="custom-deployment"></a>Implementação personalizada

Pode instalar o gateway de acesso Web Windows PowerShell num servidor que está a executar o Windows Server 2012 R2 ou Windows Server 2012, utilizando a adicionar assistente funções e funcionalidades no Gestor de servidores. Depois do acesso Web Windows PowerShell está instalado, pode personalizar a configuração do gateway no Gestor do IIS.

### <a name="install-windows-powershell-web-access"></a>Instalar o acesso Web Windows PowerShell

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a>Para instalar o Acesso Web Windows PowerShell utilizando o Assistente para Adicionar Funções e Funcionalidades

1. Se o Gestor de servidor já estiver aberto, avance para o passo seguinte. Se o Gestor de servidor já não estiver aberto, abra-o efetuando um dos seguintes procedimentos.

    - No ambiente de trabalho do Windows, inicie o Gestor de servidores, clicando em **Gestor de servidor** na barra de tarefas do Windows.

    - O Windows **iniciar** ecrã, clique em **Gestor de servidor**.

2. No **gerir** menu, clique em **para adicionar funções e funcionalidades**.

3. No **selecionar tipo de instalação** página, selecione **instalação baseada em funções ou baseada em funcionalidade**. Clique em **Seguinte**.

4. No **servidor de destino selecione** página, selecione um servidor no agrupamento de servidores ou selecione um VHD offline. Para selecionar um VHD offline como servidor de destino, primeiro selecione o servidor em que pretende montar o VHD e, em seguida, selecione o ficheiro VHD. Para informações sobre como adicionar servidores ao agrupamento de servidores, consulte a ajuda do Gestor de servidor. Depois de selecionar o servidor de destino, clique em **seguinte**.

5. No **selecionar funcionalidades** página do assistente, expanda **do Windows PowerShell**e, em seguida, selecione **acesso Web Windows PowerShell**.

6. Tenha em atenção que lhe é pedido para adicionar funcionalidades necessárias, como o .NET Framework 4.5 e serviços de função do Servidor Web (IIS). Adicione as funcionalidades necessárias e continue.

    >**![Tenha em atenção](images/note.jpeg) nota** 
    >
    >Também instalar acesso Web Windows PowerShell utilizando o Assistente de funcionalidades de adicionar funções e instala o servidor Web (IIS), incluindo o snap-in Gestor do IIS. O snap-in e outras ferramentas de gestão do IIS são instaladas por predefinição se utilizar o Assistente Adicionar funções e funcionalidades. Se instalar acesso Web Windows PowerShell utilizando cmdlets do Windows PowerShell, conforme descrito no procedimento seguinte, as ferramentas de gestão não foram adicionadas por predefinição.

7. No **confirmar seleções de instalação** página, se os ficheiros de funcionalidade para acesso Web Windows PowerShell não são armazenadas no servidor de destino que selecionou no passo 4, clique em **especificar um caminho de origem alternativo**e forneça o caminho para os ficheiros de funcionalidade. Caso contrário, clique em **instalar**.

8. Depois de clicar em **instalar**, a **progresso da instalação** página apresenta o progresso da instalação, os resultados e mensagens, tais como avisos, falhas ou passos de configuração de pós-instalação que são necessário para o acesso Web Windows PowerShell. Depois do acesso Web Windows PowerShell está instalado, lhe for pedido para rever o ficheiro Leia-me, o qual contém instruções de configuração básicas e necessárias para o gateway. Estas instruções também estão incluídas neste tópico. O caminho para o ficheiro Leia-me é `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Configurar o gateway

As instruções nesta secção destinam-se a instalar a aplicação de web de acesso Web Windows PowerShell num subdiretório e não no diretório raiz do seu Web site. Este procedimento é o equivalente baseado na GUI das ações efetuadas pelo cmdlet `Install-PswaWebApplication`. Esta secção também inclui instruções sobre como utilizar o Gestor de IIS para configurar o gateway de acesso Web Windows PowerShell como um site de raiz.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>Para utilizar o Gestor do IIS para configurar o gateway num Web site existente

1. Abra a consola do Gestor do IIS efetuando um dos procedimentos seguintes.

    - No ambiente de trabalho do Windows, inicie o Gestor de servidores, clicando em **Gestor de servidor** na barra de tarefas do Windows. No **ferramentas** menu no Gestor de servidores, clique em **Gestor dos serviços de informação Internet (IIS)**.

    - O Windows **iniciar** ecrã, escreva qualquer parte do nome **Gestor dos serviços de informação Internet (IIS)**. Clique no atalho quando for apresentada na **aplicações** resultados.

2. Crie um novo conjunto aplicacional para o acesso Web Windows PowerShell. Expanda o nó do servidor de gateway no painel de árvore Gestor de IIS, selecione **conjuntos aplicacionais**e clique em **adicionar conjunto aplicacional** no **ações** painel.

3. Adicionar um novo conjunto aplicacional com o nome **pswa_pool**, ou forneça outro nome. Clique em **OK**.

4. No painel de árvore do Gestor de IIS, expanda o nó para o servidor no qual o acesso Web Windows PowerShell está instalado até o **Sites** pasta está visível. Selecione o **Sites** pasta.

5. Clique com o botão direito do Web site (por exemplo, **Web Site predefinido**) ao qual pretende adicionar o Web site do acesso Web Windows PowerShell e, em seguida, clique em **Adicionar aplicação**.

6. No **Alias** campo, escreva pswa ou forneça outro alias. O alias torna-se o nome de diretório virtual. Por exemplo, **pswa** no URL seguinte representa o alias especificado neste passo: **https://\<nome do servidor\>/pswa**.

7. No **conjunto aplicacional** campo, selecione o conjunto aplicacional que criou no passo 3.

8. No **caminho físico** campo, procure a localização da aplicação. Pode utilizar a localização predefinida, %windir%/Web/PowerShellWebAccess/wwwroot. Clique em **OK**.

9. Siga os passos do procedimento para configurar um certificado SSL no IIS manager](#to-configure-an-ssl-certificate-in-iis-Manager) neste tópico.

10. ![](images/SecurityNote.jpeg) Passo opcional de segurança:

    Com o site selecionado no painel de árvore, faça duplo clique em **as definições de SSL** no painel de conteúdo. Selecione **exigir SSL**e, em seguida, no **ações** painel, clique em **aplicar**. Opcionalmente, no **as definições de SSL** painel, pode exigir que os utilizadores a ligar ao Web site do acesso Web Windows PowerShell têm certificados de cliente. Os certificados de cliente ajudam a verificar a identidade de um utilizador do dispositivo cliente. Para obter mais informações sobre como os certificados de cliente podem aumentar a segurança de acesso Web Windows PowerShell, consulte [regras de autorização e segurança funcionalidades de acesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md) neste guia.

11. Abra uma sessão de browser num dispositivo cliente. Para obter mais informações sobre dispositivos e browsers suportados, consulte [Browser e o dispositivo de cliente suportar](#browser-and-client-device-support) neste tópico.

12. Abrir o novo site de acesso Web Windows PowerShell, **https://\<*nome de servidor de gateway*\>/pswa**.

    O browser deve apresentar o acesso Web Windows PowerShell início de sessão page da consola.

    >**![Tenha em atenção](images/note.jpeg) nota** 
    > 
    >Não é possível iniciar sessão até que tenha sido concedido acesso ao site aos utilizadores adicionando regras de autorização. 
    >Para obter mais informações, consulte [configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule), neste tópico, e [regras de autorização e segurança funcionalidades de acesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. Numa sessão do Windows PowerShell que foi aberta com direitos de utilizador elevados (executar como administrador), execute o script seguinte, no qual *nome_conjunto_aplicacional* representa o nome do conjunto aplicacional que criou no passo 3, Para conceder ao conjunto aplicacional direitos de acesso ao ficheiro de autorização.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Para ver os direitos de acesso existentes no ficheiro de autorização, execute o seguinte comando:

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>Para utilizar o Gestor do IIS para configurar o gateway como um Web site de raiz com um certificado de teste

1. Abra a consola do Gestor do IIS efetuando um dos procedimentos seguintes.

    - No ambiente de trabalho do Windows, inicie o Gestor de servidores, clicando em **Gestor de servidor** na barra de tarefas do Windows. No **ferramentas** menu no Gestor de servidores, clique em **Gestor dos serviços de informação Internet (IIS)**.

    - O Windows **iniciar** ecrã, escreva qualquer parte do nome **Gestor dos serviços de informação Internet (IIS)**. Clique no atalho quando for apresentada na **aplicações** resultados.

2. No painel de árvore do Gestor de IIS, expanda o nó para o servidor no qual o acesso Web Windows PowerShell está instalado até o **Sites** pasta está visível. Selecione o **Sites** pasta.

3. No **ações** painel, clique em **adicionar Web site**.

4. Escreva um nome para o Web site, tais como **acesso Web Windows PowerShell**.

5. É criado automaticamente um conjunto aplicacional para o novo Web site. Para utilizar um conjunto aplicacional diferente, clique em **selecione** para selecionar um conjunto aplicacional para associar o novo Web site. Selecione o conjunto aplicacional alternativo no **selecionar conjunto aplicacional** caixa de diálogo e, em seguida, clique em **OK**.

6. No **caminho físico** texto caixa, navegue para %*windir*% / Web/PowerShellWebAccess/wwwroot.

7. No **tipo** campo a **enlace** área selecione **https**.

8. Atribua um número de porta ao Web site que ainda não esteja a ser utilizado por outro site ou aplicação. Para localizar portas abertas, pode executar o **netstat** comando numa janela de linha de comandos. O número de porta predefinido é 443.

    Altere a porta predefinida se outro Web site já estiver a utilizar a 443 ou se tiver outros motivos de segurança para alterar o número de porta. Se outro Web site que está a executar no seu servidor de gateway estiver a utilizar a porta selecionada, é apresentado um aviso quando clicar em **OK** no **adicionar Web site** caixa de diálogo. Tem de utilizar uma porta não utilizada para executar o acesso Web Windows PowerShell.

9. Opcionalmente, se for necessário para a sua organização, especifique um nome de anfitrião que faz sentido para a sua organização e utilizadores, tais como **www.contoso.com**. Clique em **OK**.

10. Para um ambiente de produção mais seguro, recomendamos vivamente que forneça um certificado válido assinado por uma AC. Tem de fornecer um certificado SSL, porque os utilizadores só podem ligar para o acesso Web Windows PowerShell através de um Web site HTTPS. Consulte [para configurar um certificado SSL no Gestor de IIS](#to-configure-an-ssl-certificate-in-iis-Manager) neste tópico para obter mais informações sobre como obter um certificado.

11. Clique em **OK** para fechar o **adicionar Web site** caixa de diálogo.

12. Numa sessão do Windows PowerShell que foi aberta com direitos de utilizador elevados (executar como administrador), execute o script seguinte, no qual *nome_conjunto_aplicacional* representa o nome do conjunto aplicacional que criou no passo 4, Para conceder ao conjunto aplicacional direitos de acesso ao ficheiro de autorização.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Para ver os direitos de acesso existentes no ficheiro de autorização, execute o seguinte comando:

        c:\windows\system32\icacls.exe $authorizationFile

13. Com o novo site selecionado no painel de árvore do Gestor de IIS, clique em **iniciar** no **ações** painel para iniciar o Web site.

14. Abra uma sessão de browser num dispositivo cliente. Para obter mais informações sobre dispositivos e browsers suportados, consulte [Browser e o dispositivo de cliente suportar](#browser-and-client-device-support) neste documento.

15. Abra o novo Web site do acesso Web Windows PowerShell.

    Porque o Web site de raiz aponta para a pasta de acesso Web Windows PowerShell, o browser deve apresentar a página de início de sessão do acesso Web Windows PowerShell quando abrir **https://\<*nome_servidor_gateway* \>**. Não deverá necessitar de adicionar **/pswa** para o URL.

    >**![Tenha em atenção](images/note.jpeg) nota** 
    > 
    >Não é possível iniciar sessão até que tenha sido concedido acesso ao site aos utilizadores adicionando regras de autorização. 
    >Para obter mais informações, consulte [configurar uma regra de autorização restrita](#configure-a-restrictive-authorization-rule), neste tópico, e [regras de autorização e segurança funcionalidades de acesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Configurar uma regra de autorização restrita

Depois de acesso Web Windows PowerShell está instalado e o gateway está configurado, os utilizadores podem abrir a página de início de sessão num browser, mas não conseguirão iniciar sessão até que o administrador do acesso Web Windows PowerShell conceda explicitamente acesso de utilizadores. Controlo de acesso de acesso Web Windows PowerShell é gerido utilizando o conjunto de cmdlets do Windows PowerShell descritos na seguinte tabela. Não existe nenhuma GUI comparável para adicionar ou gerir regras de autorização. Para obter mais informações sobre os cmdlets de acesso Web Windows PowerShell, consulte os tópicos de referência de cmdlet, [Cmdlets do Windows PowerShell Web Access](cmdlets/web-access-cmdlets.md).

Para obter mais detalhes sobre regras de autorização de acesso Web Windows PowerShell e a segurança, consulte [regras de autorização e segurança funcionalidades de acesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Para adicionar uma regra de autorização restrita

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados.

    - No ambiente de trabalho do Windows, com o botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **Executar como administrador**.

    - O Windows **iniciar** ecrã, faça duplo clique **do Windows PowerShell**e, em seguida, clique em **executar como administrador**.

2. ![Nota de segurança](images/SecurityNote.jpeg) Passo opcional para restringir o acesso de utilizador utilizando configurações de sessão:

    Certifique-se de que as configurações de sessão que pretende utilizar nas suas regras já existem. Se ainda não tiver sido criados, utilize as instruções para a criação de configurações de sessão no [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Escreva o seguinte e, em seguida, prima **Enter**.

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    Esta regra de autorização permite um acesso de utilizador específico a um computador na rede a que normalmente tenham acesso, com o acesso a uma configuração específica de sessão que está confinada para o utilizador '™ necessidades de cmdlet e de scripting típicas no s. 
    
    No exemplo seguinte, é concedido o acesso a um utilizador com o nome `JSmith` no domínio `Contoso` para gerir o computador `Contoso_214` e utilizar uma configuração de sessão com o nome `NewAdminsOnly`.

        Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4. Certifique-se de que a regra foi criada através da execução de `Get-PswaAuthorizationRule` cmdlet, ou `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`. 

    Por exemplo, `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Depois de ter configurado uma regra de autorização, está pronto para os utilizadores autorizados iniciar sessão na consola baseada na web e começar a utilizar o acesso Web Windows PowerShell.

## <a name="configure-a-genuine-certificate"></a>Configurar um certificado genuíno

Num ambiente de produção seguro, utilize sempre um certificado SSL válido assinado por uma autoridade de certificação (AC). O procedimento nesta secção descreve como obter e aplicar um certificado SSL válido a partir de uma AC.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Para configurar um certificado SSL no Gestor do IIS

1. No painel de árvore do Gestor de IIS, selecione o servidor no qual o acesso Web Windows PowerShell está instalado.

2. No painel de conteúdo, faça duplo clique **certificados de servidor**.

3. No **ações** painel, efetue um dos seguintes procedimentos. Para obter mais informações sobre como configurar certificados de servidor no IIS, consulte [configurar certificados de servidor no IIS 7](https://technet.microsoft.com/library/cc732230.aspx).

    - Clique em **importar** para importar um certificado válido existente a partir de uma localização na sua rede.

    - Clique em **criar pedido de certificado** para pedir um certificado a partir de uma AC, tal como [VeriSign](http://www.verisign.com/), [Thawte](https://www.thawte.com/), ou [GeoTrust](https://www.geotrust.com/). O nome comum do certificado tem de corresponder ao cabeçalho do anfitrião no pedido.

      Por exemplo, se o browser cliente pedir http://www.contoso.com/, em seguida, o nome comum também tem de ser http://www.contoso.com/. Esta é a opção mais segura e recomendada para fornecer o gateway de acesso Web Windows PowerShell com um certificado.

    - Clique em **criar um certificado autoassinado** para criar um certificado que pode utilizar imediatamente e ser assinado mais tarde por uma AC se assim o desejar. Especifique um nome amigável para o certificado autoassinado, tal como **acesso Web Windows PowerShell**. Esta opção não é considerada segura e é recomendada apenas para um ambiente de teste privado.

4. Depois de criar ou obter um certificado, selecione o Web site ao qual o certificado é aplicado (por exemplo, **Web Site predefinido**) no Gestor do IIS painel de árvore e, em seguida, clique em **enlaces** no **Ações** painel.

5. No **Adicionar enlace de Site** diálogo caixa, adicione um **https** enlace para o site, se um não for apresentado. Se não estiver a utilizar um certificado autoassinado, especifique o nome de anfitrião a partir do passo 3 deste procedimento. Se estiver a utilizar um certificado autoassinado, este passo não é necessário.

6. Selecione o certificado obtido ou criado no passo 3 deste procedimento e, em seguida, clique em **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>Utilizar a consola do Windows PowerShell baseada na Web

Depois de acesso Web Windows PowerShell está instalado e a configuração do gateway está concluída conforme descrito neste tópico, está pronta a utilizar a consola do Windows PowerShell baseada na web. Para obter mais informações sobre como obter iniciado na consola baseada na web, consulte [utilizar a consola do PowerShell baseada na Web do Windows](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Consulte Também

- [Serviços de informação Internet (IIS) 7.0 documentação](https://technet.microsoft.com/library/cc753433.aspx)
- [Ajuda do IIS 7.0 do Gestor](https://technet.microsoft.com/library/cc732664.aspx)
- [Configurar a segurança do servidor Web (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
- [Recursos de implementação de IPsec](https://technet.microsoft.com/network/bb531150)
