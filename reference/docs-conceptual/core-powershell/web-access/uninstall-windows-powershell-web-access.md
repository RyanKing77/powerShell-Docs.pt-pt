---
ms.date: 2017-08-23
keywords: PowerShell, o cmdlet
title: desinstalar o acesso web windows powershell
ms.openlocfilehash: b6e6a2374e6b4b2be8742019c5f1e4d5b5d1abe3
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2017
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="8a7be-103">Desinstalar o Acesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a7be-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="8a7be-104">Atualizada: 24 de Junho de 2013</span><span class="sxs-lookup"><span data-stu-id="8a7be-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="8a7be-105">Aplica-se a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="8a7be-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="8a7be-106">Os passos neste tópico remover o Web site do acesso Web Windows PowerShell e a aplicação correspondente do servidor de gateway onde está instalado.</span><span class="sxs-lookup"><span data-stu-id="8a7be-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="8a7be-107">Notificar os utilizadores</span><span class="sxs-lookup"><span data-stu-id="8a7be-107">Notify users</span></span>

<span data-ttu-id="8a7be-108">Antes de começar, notifique os utilizadores da consola baseada na web que está a remover o Web site.</span><span class="sxs-lookup"><span data-stu-id="8a7be-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="8a7be-109">A desinstalar o acesso Web Windows PowerShell não desinstala IIS nem outras funcionalidades que foram instaladas automaticamente porque necessita de acesso Web Windows PowerShell-lhes para executarem.</span><span class="sxs-lookup"><span data-stu-id="8a7be-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="8a7be-110">O processo de desinstalação deixa funcionalidades instaladas no qual estava dependente; acesso Web Windows PowerShell Pode desinstalar essas funcionalidades separadamente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="8a7be-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="8a7be-111">Desinstalação (rápida) recomendada</span><span class="sxs-lookup"><span data-stu-id="8a7be-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="8a7be-112">Os procedimentos nesta secção ajudam a desinstalar:</span><span class="sxs-lookup"><span data-stu-id="8a7be-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="8a7be-113">a aplicação web de acesso Web Windows PowerShell, e</span><span class="sxs-lookup"><span data-stu-id="8a7be-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="8a7be-114">a funcionalidade de acesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a7be-114">the Windows PowerShell Web Access feature</span></span>
 
<span data-ttu-id="8a7be-115">utilizando os cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a7be-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="8a7be-116">Passo 1: Eliminar a aplicação web utilizando cmdlets</span><span class="sxs-lookup"><span data-stu-id="8a7be-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="8a7be-117">Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a7be-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="8a7be-118">No ambiente de trabalho do Windows, clique com botão direito **do Windows PowerShell** na barra de tarefas.</span><span class="sxs-lookup"><span data-stu-id="8a7be-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="8a7be-119">O Windows **iniciar** ecrã, clique em **do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="8a7be-120">Tipo `Uninstall-PswaWebApplication`e, em seguida, prima **Enter**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="8a7be-121">Se tiver especificado o seu próprio nome personalizado do Web site, adicione o parâmetro `-WebsiteName` ao comando e especifique o nome do Web site.</span><span class="sxs-lookup"><span data-stu-id="8a7be-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="8a7be-122">Se tiver utilizado uma aplicação web personalizada (não a aplicação predefinida, **pswa**, adicione o `-WebApplicationName` parâmetro ao comando e especifique o nome da aplicação web.</span><span class="sxs-lookup"><span data-stu-id="8a7be-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="8a7be-123">Se estiver a utilizar um certificado de teste, adicione o parâmetro `DeleteTestCertificate` ao cmdlet, conforme mostrado no exemplo seguinte.</span><span class="sxs-lookup"><span data-stu-id="8a7be-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="8a7be-124">Passo 2: Desinstalar utilizando cmdlets do Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="8a7be-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="8a7be-125">Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados.</span><span class="sxs-lookup"><span data-stu-id="8a7be-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="8a7be-126">Se já tiver sessão aberta, siga para o próximo passo.</span><span class="sxs-lookup"><span data-stu-id="8a7be-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="8a7be-127">No ambiente de trabalho do Windows, com o botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="8a7be-128">O Windows **iniciar** ecrã, faça duplo clique **do Windows PowerShell**e, em seguida, clique em **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="8a7be-129">Escreva o seguinte e, em seguida, prima **Enter**, onde *nome_do_computador* representa um servidor remoto a partir do qual pretende remover o acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a7be-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="8a7be-130">O parâmetro `-Restart` reinicia automaticamente os servidores de destino, se necessário para a remoção.</span><span class="sxs-lookup"><span data-stu-id="8a7be-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="8a7be-131">Para remover funções e funcionalidades de um VHD offline, tem de adicionar o parâmetro `-ComputerName` e o parâmetro `-VHD`.</span><span class="sxs-lookup"><span data-stu-id="8a7be-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="8a7be-132">O parâmetro `-ComputerName` contém o nome do servidor onde pretende montar o VHD, e o parâmetro `-VHD` contém o caminho para o ficheiro VHD no servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="8a7be-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="8a7be-133">Quando a remoção estiver concluída, verifique se removidas acesso Web Windows PowerShell abrindo o **todos os servidores** página no Gestor de servidores, selecionando um servidor de onde removeu a funcionalidade e consultando o **funções e Funcionalidades** mosaico na página para o servidor selecionado.</span><span class="sxs-lookup"><span data-stu-id="8a7be-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="8a7be-134">Também pode executar o `Get-WindowsFeature` cmdlet visada no servidor selecionado (Get-WindowsFeature - ComputerName &lt; *nome_do_computador*&gt;) para ver uma lista de funções e funcionalidades que estão instaladas no servidor.</span><span class="sxs-lookup"><span data-stu-id="8a7be-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="8a7be-135">Desinstalação personalizada</span><span class="sxs-lookup"><span data-stu-id="8a7be-135">Custom uninstallation</span></span>

<span data-ttu-id="8a7be-136">Os procedimentos nesta secção ajudam a desinstalar a aplicação web do acesso Web Windows PowerShell e a funcionalidade de acesso Web Windows PowerShell utilizando remover funções e funcionalidades do assistente no Gestor de servidor e a consola do Gestor de IIS.</span><span class="sxs-lookup"><span data-stu-id="8a7be-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="8a7be-137">Passo 1: Eliminar a aplicação web utilizando o Gestor de IIS</span><span class="sxs-lookup"><span data-stu-id="8a7be-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="8a7be-138">Abra a consola do Gestor do IIS efetuando um dos procedimentos seguintes.</span><span class="sxs-lookup"><span data-stu-id="8a7be-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="8a7be-139">Se já estiver aberta, siga para o próximo passo.</span><span class="sxs-lookup"><span data-stu-id="8a7be-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="8a7be-140">No ambiente de trabalho do Windows, inicie o Gestor de servidores, clicando em **Gestor de servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="8a7be-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="8a7be-141">No **ferramentas** menu no Gestor de servidores, clique em **Gestor dos serviços de informação Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="8a7be-142">O Windows **iniciar** ecrã, escreva qualquer parte do nome **Gestor dos serviços de informação Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="8a7be-143">Clique no atalho quando for apresentada na **aplicações** resultados.</span><span class="sxs-lookup"><span data-stu-id="8a7be-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="8a7be-144">No painel de árvore do Gestor de IIS, selecione o Web site que está a executar a aplicação web do acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a7be-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="8a7be-145">No **ações** painel, em **gerir Web site**, clique em **parar**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="8a7be-146">No painel de árvore, faça duplo clique na aplicação web no Web site que está a executar a aplicação web do acesso Web Windows PowerShell e, em seguida, clique em **remover**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="8a7be-147">No painel de árvore, selecione **conjuntos aplicacionais**, selecione a pasta de agrupamento de aplicações do acesso Web Windows PowerShell, clique em **parar** no **ações** painel e, em seguida, clique em  **Remover** no painel de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="8a7be-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="8a7be-148">Feche o Gestor do IIS.</span><span class="sxs-lookup"><span data-stu-id="8a7be-148">Close IIS Manager.</span></span>

> <span data-ttu-id="8a7be-149">![Nota de aviso](images/SecurityNote.jpeg)**nota**:</span><span class="sxs-lookup"><span data-stu-id="8a7be-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="8a7be-150">O certificado não é eliminado durante a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="8a7be-150">The certificate is not deleted during uninstallation.</span></span> 
>
> <span data-ttu-id="8a7be-151">Se criou um certificado autoassinado ou utilizou um certificado de teste e pretende removê-lo, elimine o certificado no Gestor do IIS.</span><span class="sxs-lookup"><span data-stu-id="8a7be-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span> 

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="8a7be-152">Passo 2: Desinstalar o acesso Web Windows PowerShell utilizando o Assistente de funcionalidades e para remover funções</span><span class="sxs-lookup"><span data-stu-id="8a7be-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="8a7be-153">Se o Gestor de servidor já estiver aberto, avance para o passo seguinte.</span><span class="sxs-lookup"><span data-stu-id="8a7be-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="8a7be-154">Se o Gestor de servidor já não estiver aberto, abra-o efetuando um dos seguintes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="8a7be-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="8a7be-155">No ambiente de trabalho do Windows, inicie o Gestor de servidores, clicando em **Gestor de servidor** na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="8a7be-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="8a7be-156">O Windows **iniciar** ecrã, clique em **Gestor de servidor**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="8a7be-157">No **gerir** menu, clique em **remover funções e funcionalidades**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="8a7be-158">No **servidor de destino selecione** página, selecione o servidor ou offline VHD a partir do qual pretende remover a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="8a7be-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="8a7be-159">Para selecionar um VHD offline, primeiro selecione o servidor onde pretende montar o VHD e, em seguida, selecione o ficheiro VHD.</span><span class="sxs-lookup"><span data-stu-id="8a7be-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="8a7be-160">Depois de selecionar o servidor de destino, clique em **seguinte**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="8a7be-161">Clique em **seguinte** novamente para avançar para o **remover funcionalidades** página.</span><span class="sxs-lookup"><span data-stu-id="8a7be-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="8a7be-162">Desmarque a caixa de verificação **acesso Web Windows PowerShell**e, em seguida, clique em **seguinte**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="8a7be-163">No **confirmar seleções de remoção** página, clique em **remover**.</span><span class="sxs-lookup"><span data-stu-id="8a7be-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a7be-164">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8a7be-164">See Also</span></span>

- [<span data-ttu-id="8a7be-165">Instalar e utilizar o acesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a7be-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="8a7be-166">Ajuda do IIS 7.0 do Gestor</span><span class="sxs-lookup"><span data-stu-id="8a7be-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)
