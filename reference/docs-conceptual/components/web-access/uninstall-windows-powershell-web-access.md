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
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="8e1e4-103">Desinstalar o Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="8e1e4-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="8e1e4-104">Atualizado: 24 de Junho de 2013</span><span class="sxs-lookup"><span data-stu-id="8e1e4-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="8e1e4-105">Aplica-se a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="8e1e4-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="8e1e4-106">Os passos neste tópico remover o Web site do Windows PowerShell Web Access e o aplicativo correspondente do servidor de gateway, onde está instalado.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="8e1e4-107">Notificar os utilizadores</span><span class="sxs-lookup"><span data-stu-id="8e1e4-107">Notify users</span></span>

<span data-ttu-id="8e1e4-108">Antes de começar, notifique os utilizadores da consola baseada na web que está a remover o Web site.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="8e1e4-109">Desinstalar o Windows PowerShell Web Access não desinstala IIS nem outras funcionalidades que foram instaladas automaticamente porque requer o Windows PowerShell Web Access para serem executadas.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="8e1e4-110">O processo de desinstalação deixa funcionalidades instaladas no qual o Windows PowerShell Web Access estava dependente; Pode desinstalar essas funcionalidades separadamente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="8e1e4-111">Desinstalação (rápida) recomendada</span><span class="sxs-lookup"><span data-stu-id="8e1e4-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="8e1e4-112">Os procedimentos nesta secção ajudam a desinstalar:</span><span class="sxs-lookup"><span data-stu-id="8e1e4-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="8e1e4-113">a aplicação web do Windows PowerShell Web Access, e</span><span class="sxs-lookup"><span data-stu-id="8e1e4-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="8e1e4-114">a funcionalidade do Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="8e1e4-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="8e1e4-115">utilizando os cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="8e1e4-116">Passo 1: Eliminar a aplicação web com os cmdlets</span><span class="sxs-lookup"><span data-stu-id="8e1e4-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="8e1e4-117">Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="8e1e4-118">Na área de trabalho Windows, clique com botão direito **Windows PowerShell** na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="8e1e4-119">Sobre o Windows **começar** ecrã, clique em **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="8e1e4-120">Tipo `Uninstall-PswaWebApplication`e, em seguida, prima **Enter**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="8e1e4-121">Se tiver especificado o nome da sua própria, Web site personalizado, adicione o `-WebsiteName` parâmetro ao comando e especifique o nome do Web site.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="8e1e4-122">Se tiver utilizado um aplicativo da web personalizado (não o aplicativo padrão, **pswa**, adicione o `-WebApplicationName` parâmetro ao comando e especifique o nome da aplicação web.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="8e1e4-123">Se estiver a utilizar um certificado de teste, adicione o `DeleteTestCertificate` parâmetro para o cmdlet, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="8e1e4-124">Passo 2: Desinstalar com os cmdlets do Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="8e1e4-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="8e1e4-125">Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="8e1e4-126">Se uma sessão já estiver aberta, avance para o passo seguinte.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="8e1e4-127">No ambiente de trabalho do Windows, com o botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="8e1e4-128">Sobre o Windows **começar** ecrã, clique com botão direito **Windows PowerShell**e, em seguida, clique em **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="8e1e4-129">Escreva o seguinte e, em seguida, prima **Enter**, onde *computer_name* representa um servidor remoto a partir do qual pretende remover o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="8e1e4-130">O `-Restart` parâmetro reinicia automaticamente servidores de destino quando requerido pela remoção.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="8e1e4-131">Para remover funções e funcionalidades de um VHD offline, tem de adicionar o `-ComputerName` parâmetro e o `-VHD` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="8e1e4-132">O `-ComputerName` parâmetro contém o nome do servidor onde pretende montar o VHD e o `-VHD` parâmetro contém o caminho para o ficheiro VHD no servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="8e1e4-133">Quando a remoção estiver concluída, certifique-se de que removeu o Windows PowerShell Web Access abrindo o **todos os servidores** página no Gestor de servidores, selecionando um servidor a partir do qual removeu a funcionalidade e consultando o **funções e Funcionalidades** mosaico na página do servidor selecionado.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="8e1e4-134">Também pode executar o `Get-WindowsFeature` cmdlet visada no servidor selecionado (Get-WindowsFeature - ComputerName &lt; *computer_name*&gt;) para ver uma lista de funções e funcionalidades que estão instaladas no servidor.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="8e1e4-135">Desinstalação personalizada</span><span class="sxs-lookup"><span data-stu-id="8e1e4-135">Custom uninstallation</span></span>

<span data-ttu-id="8e1e4-136">Os procedimentos nesta secção ajudam a desinstalar a aplicação web do Windows PowerShell Web Access e a funcionalidade do Windows PowerShell Web Access, utilizando a remover funções e funcionalidades assistente no Gestor de servidor e a consola do Gestor de IIS.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="8e1e4-137">Passo 1: Eliminar a aplicação web utilizando o Gestor do IIS</span><span class="sxs-lookup"><span data-stu-id="8e1e4-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="8e1e4-138">Abra a consola do Gestor do IIS efetuando um dos seguintes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="8e1e4-139">Se já estiver aberto, avance para o passo seguinte.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="8e1e4-140">Na área de trabalho Windows, inicie o Gestor de servidor clicando **Gestor de servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="8e1e4-141">Sobre o **ferramentas** menu no Gestor de servidores, clique em **Gestor de serviços de informação Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="8e1e4-142">Sobre o Windows **começar** ecrã, escreva qualquer parte do nome **Gestor de serviços de informação Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="8e1e4-143">Clique no atalho será apresentado no **aplicações** resultados.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="8e1e4-144">No painel de árvore do Gerenciador do IIS, selecione o Web site que está a executar a aplicação web do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="8e1e4-145">Na **ações** painel, em **gerir Web site**, clique em **parar**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="8e1e4-146">No painel de árvore, clique com o botão direito a aplicação web no Web site que está a executar a aplicação web do Windows PowerShell Web Access e, em seguida, clique em **remover**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="8e1e4-147">No painel de árvore, selecione **Pools de aplicativos**, selecione a pasta de conjunto de aplicativos do Windows PowerShell Web Access, clique em **parar** no **ações** painel e, em seguida, clique em  **Remover** no painel de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="8e1e4-148">Feche o Gestor de IIS.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-148">Close IIS Manager.</span></span>

> <span data-ttu-id="8e1e4-149">![Nota de aviso](images/SecurityNote.jpeg)**nota**:</span><span class="sxs-lookup"><span data-stu-id="8e1e4-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="8e1e4-150">Não é possível eliminar o certificado durante a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-150">The certificate is not deleted during uninstallation.</span></span>
>
> <span data-ttu-id="8e1e4-151">Se criou um certificado autoassinado ou utilizou um certificado de teste e pretende removê-lo, elimine o certificado no Gestor do IIS.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="8e1e4-152">Passo 2: Desinstalar o Windows PowerShell Web Access com o Assistente de funcionalidades e para remover funções</span><span class="sxs-lookup"><span data-stu-id="8e1e4-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="8e1e4-153">Se o Gestor de servidor já estiver aberto, avance para o passo seguinte.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="8e1e4-154">Se o Gestor de servidor não esteja ainda aberto, abra-o efetuando um dos seguintes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="8e1e4-155">Na área de trabalho Windows, inicie o Gestor de servidor clicando **Gestor de servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="8e1e4-156">Sobre o Windows **começar** ecrã, clique em **Gestor de servidor**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="8e1e4-157">Sobre o **Manage** menu, clique em **remover funções e funcionalidades**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="8e1e4-158">Sobre o **selecionar servidor de destino** página, selecione o servidor ou offline VHD a partir do qual pretende remover a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="8e1e4-159">Para selecionar um VHD offline, primeiro selecione o servidor onde pretende montar o VHD e, em seguida, selecione o ficheiro VHD.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="8e1e4-160">Depois de selecionar o servidor de destino, clique em **seguinte**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="8e1e4-161">Clique em **próxima** novamente para avançar para o **remover funcionalidades** página.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="8e1e4-162">Desmarque a caixa de verificação **Windows PowerShell Web Access**e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="8e1e4-163">Sobre o **confirmar seleções de remoção** página, clique em **remover**.</span><span class="sxs-lookup"><span data-stu-id="8e1e4-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e1e4-164">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8e1e4-164">See Also</span></span>

- [<span data-ttu-id="8e1e4-165">Instalar e utilizar o Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="8e1e4-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="8e1e4-166">Ajuda do IIS Manager 7.0</span><span class="sxs-lookup"><span data-stu-id="8e1e4-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)