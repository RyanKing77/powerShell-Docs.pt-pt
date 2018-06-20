---
ms.date: 08/23/2017
keywords: PowerShell, o cmdlet
title: desinstalar o acesso web windows powershell
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952958"
---
# <a name="uninstall-windows-powershell-web-access"></a>Desinstalar o Acesso Web Windows PowerShell

Atualizada: 24 de Junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

Os passos neste tópico remover o Web site do acesso Web Windows PowerShell e a aplicação correspondente do servidor de gateway onde está instalado.

## <a name="notify-users"></a>Notificar os utilizadores

Antes de começar, notifique os utilizadores da consola baseada na web que está a remover o Web site.

A desinstalar o acesso Web Windows PowerShell não desinstala IIS nem outras funcionalidades que foram instaladas automaticamente porque necessita de acesso Web Windows PowerShell-lhes para executarem.
O processo de desinstalação deixa funcionalidades instaladas no qual estava dependente; acesso Web Windows PowerShell Pode desinstalar essas funcionalidades separadamente, se necessário.

## <a name="recommended-quick-uninstallation"></a>Desinstalação (rápida) recomendada

Os procedimentos nesta secção ajudam a desinstalar:

- a aplicação web de acesso Web Windows PowerShell, e
- a funcionalidade de acesso Web Windows PowerShell

utilizando os cmdlets do Windows PowerShell.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Passo 1: Eliminar a aplicação web utilizando cmdlets

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell.

    -   No ambiente de trabalho do Windows, clique com botão direito **do Windows PowerShell** na barra de tarefas.

    -   O Windows **iniciar** ecrã, clique em **do Windows PowerShell**.

2. Tipo `Uninstall-PswaWebApplication`e, em seguida, prima **Enter**.
   1. Se tiver especificado o seu próprio nome personalizado do Web site, adicione o parâmetro `-WebsiteName` ao comando e especifique o nome do Web site.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Se tiver utilizado uma aplicação web personalizada (não a aplicação predefinida, **pswa**, adicione o `-WebApplicationName` parâmetro ao comando e especifique o nome da aplicação web.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Se estiver a utilizar um certificado de teste, adicione o parâmetro `DeleteTestCertificate` ao cmdlet, conforme mostrado no exemplo seguinte.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Passo 2: Desinstalar utilizando cmdlets do Windows PowerShell Web Access

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados. Se já tiver sessão aberta, siga para o próximo passo.

    -   No ambiente de trabalho do Windows, com o botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **Executar como administrador**.

    -   O Windows **iniciar** ecrã, faça duplo clique **do Windows PowerShell**e, em seguida, clique em **executar como administrador**.

1. Escreva o seguinte e, em seguida, prima **Enter**, onde *nome_do_computador* representa um servidor remoto a partir do qual pretende remover o acesso Web Windows PowerShell. O parâmetro `-Restart` reinicia automaticamente os servidores de destino, se necessário para a remoção.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Para remover funções e funcionalidades de um VHD offline, tem de adicionar o parâmetro `-ComputerName` e o parâmetro `-VHD`. O parâmetro `-ComputerName` contém o nome do servidor onde pretende montar o VHD, e o parâmetro `-VHD` contém o caminho para o ficheiro VHD no servidor especificado.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Quando a remoção estiver concluída, verifique se removidas acesso Web Windows PowerShell abrindo o **todos os servidores** página no Gestor de servidores, selecionando um servidor de onde removeu a funcionalidade e consultando o **funções e Funcionalidades** mosaico na página para o servidor selecionado.

    Também pode executar o `Get-WindowsFeature` cmdlet visada no servidor selecionado (Get-WindowsFeature - ComputerName &lt; *nome_do_computador*&gt;) para ver uma lista de funções e funcionalidades que estão instaladas no servidor.

## <a name="custom-uninstallation"></a>Desinstalação personalizada

Os procedimentos nesta secção ajudam a desinstalar a aplicação web do acesso Web Windows PowerShell e a funcionalidade de acesso Web Windows PowerShell utilizando remover funções e funcionalidades do assistente no Gestor de servidor e a consola do Gestor de IIS.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Passo 1: Eliminar a aplicação web utilizando o Gestor de IIS


1. Abra a consola do Gestor do IIS efetuando um dos procedimentos seguintes. Se já estiver aberta, siga para o próximo passo.

    -   No ambiente de trabalho do Windows, inicie o Gestor de servidores, clicando em **Gestor de servidor** na barra de tarefas do Windows. No **ferramentas** menu no Gestor de servidores, clique em **Gestor dos serviços de informação Internet (IIS)**.

    -   O Windows **iniciar** ecrã, escreva qualquer parte do nome **Gestor dos serviços de informação Internet (IIS)**. Clique no atalho quando for apresentada na **aplicações** resultados.

1. No painel de árvore do Gestor de IIS, selecione o Web site que está a executar a aplicação web do acesso Web Windows PowerShell.

1. No **ações** painel, em **gerir Web site**, clique em **parar**.

1. No painel de árvore, faça duplo clique na aplicação web no Web site que está a executar a aplicação web do acesso Web Windows PowerShell e, em seguida, clique em **remover**.

1. No painel de árvore, selecione **conjuntos aplicacionais**, selecione a pasta de agrupamento de aplicações do acesso Web Windows PowerShell, clique em **parar** no **ações** painel e, em seguida, clique em  **Remover** no painel de conteúdo.

1. Feche o Gestor do IIS.

> ![Nota de aviso](images/SecurityNote.jpeg)**nota**:
>
> O certificado não é eliminado durante a desinstalação.
>
> Se criou um certificado autoassinado ou utilizou um certificado de teste e pretende removê-lo, elimine o certificado no Gestor do IIS.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Passo 2: Desinstalar o acesso Web Windows PowerShell utilizando o Assistente de funcionalidades e para remover funções

1. Se o Gestor de servidor já estiver aberto, avance para o passo seguinte. Se o Gestor de servidor já não estiver aberto, abra-o efetuando um dos seguintes procedimentos.

    -   No ambiente de trabalho do Windows, inicie o Gestor de servidores, clicando em **Gestor de servidor** na barra de tarefas do Windows.

    -   O Windows **iniciar** ecrã, clique em **Gestor de servidor**.

1. No **gerir** menu, clique em **remover funções e funcionalidades**.

1. No **servidor de destino selecione** página, selecione o servidor ou offline VHD a partir do qual pretende remover a funcionalidade. Para selecionar um VHD offline, primeiro selecione o servidor onde pretende montar o VHD e, em seguida, selecione o ficheiro VHD. Depois de selecionar o servidor de destino, clique em **seguinte**.

1. Clique em **seguinte** novamente para avançar para o **remover funcionalidades** página.

1. Desmarque a caixa de verificação **acesso Web Windows PowerShell**e, em seguida, clique em **seguinte**.

1. No **confirmar seleções de remoção** página, clique em **remover**.

## <a name="see-also"></a>Consulte Também

- [Instalar e utilizar o acesso Web Windows PowerShell](install-and-use-windows-powershell-web-access.md)
- [Ajuda do IIS 7.0 do Gestor](https://technet.microsoft.com/library/cc732664.aspx)