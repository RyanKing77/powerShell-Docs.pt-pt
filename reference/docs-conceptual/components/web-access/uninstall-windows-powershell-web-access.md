---
ms.date: 08/23/2017
keywords: PowerShell, o cmdlet
title: desinstalar o acesso web windows powershell
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058148"
---
# <a name="uninstall-windows-powershell-web-access"></a>Desinstalar o Windows PowerShell Web Access

Atualizado: 24 de Junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

Os passos neste tópico remover o Web site do Windows PowerShell Web Access e o aplicativo correspondente do servidor de gateway, onde está instalado.

## <a name="notify-users"></a>Notificar os utilizadores

Antes de começar, notifique os utilizadores da consola baseada na web que está a remover o Web site.

Desinstalar o Windows PowerShell Web Access não desinstala IIS nem outras funcionalidades que foram instaladas automaticamente porque requer o Windows PowerShell Web Access para serem executadas.
O processo de desinstalação deixa funcionalidades instaladas no qual o Windows PowerShell Web Access estava dependente; Pode desinstalar essas funcionalidades separadamente, se necessário.

## <a name="recommended-quick-uninstallation"></a>Desinstalação (rápida) recomendada

Os procedimentos nesta secção ajudam a desinstalar:

- a aplicação web do Windows PowerShell Web Access, e
- a funcionalidade do Windows PowerShell Web Access

utilizando os cmdlets do Windows PowerShell.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Passo 1: Eliminar a aplicação web com os cmdlets

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell.

    -   Na área de trabalho Windows, clique com botão direito **Windows PowerShell** na barra de tarefas.

    -   Sobre o Windows **começar** ecrã, clique em **Windows PowerShell**.

2. Tipo `Uninstall-PswaWebApplication`e, em seguida, prima **Enter**.
   1. Se tiver especificado o nome da sua própria, Web site personalizado, adicione o `-WebsiteName` parâmetro ao comando e especifique o nome do Web site.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Se tiver utilizado um aplicativo da web personalizado (não o aplicativo padrão, **pswa**, adicione o `-WebApplicationName` parâmetro ao comando e especifique o nome da aplicação web.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Se estiver a utilizar um certificado de teste, adicione o `DeleteTestCertificate` parâmetro para o cmdlet, conforme mostrado no exemplo a seguir.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Passo 2: Desinstalar com os cmdlets do Windows PowerShell Web Access

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados. Se uma sessão já estiver aberta, avance para o passo seguinte.

    -   No ambiente de trabalho do Windows, com o botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **Executar como administrador**.

    -   Sobre o Windows **começar** ecrã, clique com botão direito **Windows PowerShell**e, em seguida, clique em **executar como administrador**.

1. Escreva o seguinte e, em seguida, prima **Enter**, onde *computer_name* representa um servidor remoto a partir do qual pretende remover o Windows PowerShell Web Access. O `-Restart` parâmetro reinicia automaticamente servidores de destino quando requerido pela remoção.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Para remover funções e funcionalidades de um VHD offline, tem de adicionar o `-ComputerName` parâmetro e o `-VHD` parâmetro. O `-ComputerName` parâmetro contém o nome do servidor onde pretende montar o VHD e o `-VHD` parâmetro contém o caminho para o ficheiro VHD no servidor especificado.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Quando a remoção estiver concluída, certifique-se de que removeu o Windows PowerShell Web Access abrindo o **todos os servidores** página no Gestor de servidores, selecionando um servidor a partir do qual removeu a funcionalidade e consultando o **funções e Funcionalidades** mosaico na página do servidor selecionado.

    Também pode executar o `Get-WindowsFeature` cmdlet visada no servidor selecionado (Get-WindowsFeature - ComputerName &lt; *computer_name*&gt;) para ver uma lista de funções e funcionalidades que estão instaladas no servidor.

## <a name="custom-uninstallation"></a>Desinstalação personalizada

Os procedimentos nesta secção ajudam a desinstalar a aplicação web do Windows PowerShell Web Access e a funcionalidade do Windows PowerShell Web Access, utilizando a remover funções e funcionalidades assistente no Gestor de servidor e a consola do Gestor de IIS.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Passo 1: Eliminar a aplicação web utilizando o Gestor do IIS


1. Abra a consola do Gestor do IIS efetuando um dos seguintes procedimentos. Se já estiver aberto, avance para o passo seguinte.

    -   Na área de trabalho Windows, inicie o Gestor de servidor clicando **Gestor de servidor** na barra de tarefas do Windows. Sobre o **ferramentas** menu no Gestor de servidores, clique em **Gestor de serviços de informação Internet (IIS)**.

    -   Sobre o Windows **começar** ecrã, escreva qualquer parte do nome **Gestor de serviços de informação Internet (IIS)**. Clique no atalho será apresentado no **aplicações** resultados.

1. No painel de árvore do Gerenciador do IIS, selecione o Web site que está a executar a aplicação web do Windows PowerShell Web Access.

1. Na **ações** painel, em **gerir Web site**, clique em **parar**.

1. No painel de árvore, clique com o botão direito a aplicação web no Web site que está a executar a aplicação web do Windows PowerShell Web Access e, em seguida, clique em **remover**.

1. No painel de árvore, selecione **Pools de aplicativos**, selecione a pasta de conjunto de aplicativos do Windows PowerShell Web Access, clique em **parar** no **ações** painel e, em seguida, clique em  **Remover** no painel de conteúdo.

1. Feche o Gestor de IIS.

> ![Nota de aviso](images/SecurityNote.jpeg)**nota**:
>
> Não é possível eliminar o certificado durante a desinstalação.
>
> Se criou um certificado autoassinado ou utilizou um certificado de teste e pretende removê-lo, elimine o certificado no Gestor do IIS.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Passo 2: Desinstalar o Windows PowerShell Web Access com o Assistente de funcionalidades e para remover funções

1. Se o Gestor de servidor já estiver aberto, avance para o passo seguinte. Se o Gestor de servidor não esteja ainda aberto, abra-o efetuando um dos seguintes procedimentos.

    -   Na área de trabalho Windows, inicie o Gestor de servidor clicando **Gestor de servidor** na barra de tarefas do Windows.

    -   Sobre o Windows **começar** ecrã, clique em **Gestor de servidor**.

1. Sobre o **Manage** menu, clique em **remover funções e funcionalidades**.

1. Sobre o **selecionar servidor de destino** página, selecione o servidor ou offline VHD a partir do qual pretende remover a funcionalidade. Para selecionar um VHD offline, primeiro selecione o servidor onde pretende montar o VHD e, em seguida, selecione o ficheiro VHD. Depois de selecionar o servidor de destino, clique em **seguinte**.

1. Clique em **próxima** novamente para avançar para o **remover funcionalidades** página.

1. Desmarque a caixa de verificação **Windows PowerShell Web Access**e, em seguida, clique em **próxima**.

1. Sobre o **confirmar seleções de remoção** página, clique em **remover**.

## <a name="see-also"></a>Veja Também

- [Instalar e utilizar o Windows PowerShell Web Access](install-and-use-windows-powershell-web-access.md)
- [Ajuda do IIS Manager 7.0](https://technet.microsoft.com/library/cc732664.aspx)