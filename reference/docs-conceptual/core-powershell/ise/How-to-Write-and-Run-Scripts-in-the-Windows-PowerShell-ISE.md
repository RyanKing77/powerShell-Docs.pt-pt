---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Como Escrever e Executar Scripts no ISE do Windows PowerShell
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 77d8ae81cb03f03b3b5d044e6503bbb23cb5b771
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="fecbe-103">Como Escrever e Executar Scripts no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fecbe-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>
<span data-ttu-id="fecbe-104">Este tópico descreve como criar, editar, executar e guardar scripts no painel de Script.</span><span class="sxs-lookup"><span data-stu-id="fecbe-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="fecbe-105">Como criar e executar scripts</span><span class="sxs-lookup"><span data-stu-id="fecbe-105">How to create and run scripts</span></span>
<span data-ttu-id="fecbe-106">Pode abrir e editar ficheiros do Windows PowerShell no painel de Script.</span><span class="sxs-lookup"><span data-stu-id="fecbe-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="fecbe-107">Tipos de ficheiro específicos de interesse no Windows PowerShell são ficheiros de script (. ps1), ficheiros de dados do script (. psd1) e os ficheiros do módulo de script (. psm1).</span><span class="sxs-lookup"><span data-stu-id="fecbe-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="fecbe-108">Estes tipos de ficheiro são sintaxe colorido no editor do painel de Script.</span><span class="sxs-lookup"><span data-stu-id="fecbe-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="fecbe-109">Outros tipos de ficheiro comuns que poderá abrir no painel de Script são ficheiros de configuração (.ps1xml), ficheiros XML e ficheiros de texto.</span><span class="sxs-lookup"><span data-stu-id="fecbe-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="fecbe-110">A política de execução do Windows PowerShell determina se pode executar scripts e carga do Windows PowerShell perfis e ficheiros de configuração.</span><span class="sxs-lookup"><span data-stu-id="fecbe-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="fecbe-111">A política de execução predefinidas, restrito, impede que todos os scripts em execução e impede que os perfis de carregamento.</span><span class="sxs-lookup"><span data-stu-id="fecbe-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="fecbe-112">Para alterar a política de execução para permitir que os perfis a carregar e ser utilizado, consulte [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) e [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span><span class="sxs-lookup"><span data-stu-id="fecbe-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="fecbe-113">Para criar um novo ficheiro de script</span><span class="sxs-lookup"><span data-stu-id="fecbe-113">To create a new script file</span></span>
<span data-ttu-id="fecbe-114">Na barra de ferramentas, clique em **novo** , ou no **ficheiro** menu, clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-114">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="fecbe-115">O ficheiro criado é apresentado num separador novo do ficheiro no separador atual do PowerShell. Lembre-se de que os separadores de PowerShell apenas são visíveis quando existirem mais do que um.</span><span class="sxs-lookup"><span data-stu-id="fecbe-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="fecbe-116">Por predefinição é criado um ficheiro de script de tipo (. ps1), mas podem ser guardado com um novo nome e extensão.</span><span class="sxs-lookup"><span data-stu-id="fecbe-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="fecbe-117">Podem ser criados vários ficheiros de script no mesmo separador do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fecbe-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="fecbe-118">Para abrir um script existente</span><span class="sxs-lookup"><span data-stu-id="fecbe-118">To open an existing script</span></span>
<span data-ttu-id="fecbe-119">Na barra de ferramentas, clique em **abra**, ou no **ficheiro** menu, clique em **abra**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="fecbe-120">No **abrir** diálogo caixa, selecione o ficheiro que pretende abrir.</span><span class="sxs-lookup"><span data-stu-id="fecbe-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="fecbe-121">É apresentado o ficheiro aberto num novo separador.</span><span class="sxs-lookup"><span data-stu-id="fecbe-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="fecbe-122">Para fechar um separador de script</span><span class="sxs-lookup"><span data-stu-id="fecbe-122">To close a script tab</span></span>
<span data-ttu-id="fecbe-123">Clique no separador de script do script que pretende fechar e, em seguida, efetue um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="fecbe-123">Click the script tab of the script you want to close, then do one of the following:</span></span>

1. <span data-ttu-id="fecbe-124">Clique em de **fechar** ícone (X) no separador de script.</span><span class="sxs-lookup"><span data-stu-id="fecbe-124">Click the **Close** icon (X) on the script tab.</span></span>

2. <span data-ttu-id="fecbe-125">No **ficheiro** menu, clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-125">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="fecbe-126">Se o ficheiro tiver sido alterado desde que foi guardada pela última vez, lhe for pedido que guarde ou elimine-lo.</span><span class="sxs-lookup"><span data-stu-id="fecbe-126">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="fecbe-127">Para apresentar o caminho do ficheiro</span><span class="sxs-lookup"><span data-stu-id="fecbe-127">To display the file path</span></span>
<span data-ttu-id="fecbe-128">No separador ficheiros, aponte para o nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="fecbe-128">On the file tab, point to the file name.</span></span> <span data-ttu-id="fecbe-129">O caminho completamente qualificado para o ficheiro de script é apresentada numa descrição.</span><span class="sxs-lookup"><span data-stu-id="fecbe-129">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="fecbe-130">Para executar um script</span><span class="sxs-lookup"><span data-stu-id="fecbe-130">To run a script</span></span>
<span data-ttu-id="fecbe-131">Na barra de ferramentas, clique em **executar Script**, ou no **ficheiro** menu, clique em **executar**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-131">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="fecbe-132">Para executar uma parte de um script</span><span class="sxs-lookup"><span data-stu-id="fecbe-132">To run a portion of a script</span></span>

1. <span data-ttu-id="fecbe-133">No painel de Script, selecione uma parte de um script.</span><span class="sxs-lookup"><span data-stu-id="fecbe-133">In the Script Pane, select a portion of a script.</span></span>

2. <span data-ttu-id="fecbe-134">No **ficheiro** menu, clique em **executar seleção**, ou na barra de ferramentas, clique em **executar seleção**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-134">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="fecbe-135">Para parar um script em execução</span><span class="sxs-lookup"><span data-stu-id="fecbe-135">To stop a running script</span></span>
<span data-ttu-id="fecbe-136">Na barra de ferramentas, clique em **operação parar**, prima CTRL + BREAK, ou no **ficheiro** menu, clique em **operação parar**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-136">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="fecbe-137">Premir **CTRL + C** também funciona, exceto se algum texto atualmente selecionado, caso em que **CTRL + C** mapeia para a função de cópia para o texto seleccionado.</span><span class="sxs-lookup"><span data-stu-id="fecbe-137">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="fecbe-138">Como escrever e editar o texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="fecbe-138">How to write and edit text in the Script Pane</span></span>
<span data-ttu-id="fecbe-139">Utilize os seguintes passos para editar o texto no painel de Script.</span><span class="sxs-lookup"><span data-stu-id="fecbe-139">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="fecbe-140">Pode copiar, cortar, colar, localizar e substituir texto.</span><span class="sxs-lookup"><span data-stu-id="fecbe-140">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="fecbe-141">Também pode anular e Refazer a última ação que apenas efetuada.</span><span class="sxs-lookup"><span data-stu-id="fecbe-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="fecbe-142">Os atalhos de teclado para efetuar estas ações são os mesmos que são utilizados para todas as aplicações do Windows.</span><span class="sxs-lookup"><span data-stu-id="fecbe-142">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="fecbe-143">Introduza o texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="fecbe-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="fecbe-144">Mova o cursor para o painel de Script ao clicar em qualquer lugar no painel de Script, ou clicando **aceda ao painel de Script** no **vista** menu.</span><span class="sxs-lookup"><span data-stu-id="fecbe-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2. <span data-ttu-id="fecbe-145">Crie um script.</span><span class="sxs-lookup"><span data-stu-id="fecbe-145">Create a script.</span></span> <span data-ttu-id="fecbe-146">Sintaxe coloração e conclusão de separador tornar esta uma experiência mais rica no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fecbe-146">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3. <span data-ttu-id="fecbe-147">Consulte [como conclusão de separador de utilização no painel de Script e painel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obter detalhes sobre como utilizar a funcionalidade de conclusão de separador para ajudar a escrever.</span><span class="sxs-lookup"><span data-stu-id="fecbe-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="fecbe-148">Para localizar texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="fecbe-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="fecbe-149">Para localizar texto em qualquer lugar, prima **CTRL + F** ou, no **editar** menu, clique em **localizar no Script**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2. <span data-ttu-id="fecbe-150">Para localizar texto após o cursor, prima **F3** ou, no **editar** menu, clique em **Localizar seguinte script**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3. <span data-ttu-id="fecbe-151">Para localizar texto antes do cursor, prima **SHIFT + F3** ou, no **editar** menu, clique em **Localizar anterior no Script**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="fecbe-152">Para localizar e substituir texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="fecbe-152">To find and replace text in the Script Pane</span></span>
<span data-ttu-id="fecbe-153">Prima **CRTL + H** ou, no **editar** menu, clique em **substituir no Script**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-153">Press **CRTL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="fecbe-154">Introduza o texto que pretende localizar e o texto com o qual pretende substituí-lo e, em seguida, prima **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-154">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="fecbe-155">Ir para uma determinada linha de texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="fecbe-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="fecbe-156">No painel de Script, prima **CTRL + G** ou, no **editar** menu, clique em **aceda a linha**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="fecbe-157">Introduza um número de linha.</span><span class="sxs-lookup"><span data-stu-id="fecbe-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="fecbe-158">Para copiar o texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="fecbe-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="fecbe-159">No painel de Script, selecione o texto que pretende copiar.</span><span class="sxs-lookup"><span data-stu-id="fecbe-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="fecbe-160">Prima **CTRL + C** ou, na barra de ferramentas, clique em de **cópia** ícone, ou no **editar** menu, clique em **cópia**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="fecbe-161">Ao cortar texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="fecbe-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="fecbe-162">No painel de Script, selecione o texto que pretende cortar.</span><span class="sxs-lookup"><span data-stu-id="fecbe-162">In the Script Pane, select the text that you want to cut.</span></span>

2. <span data-ttu-id="fecbe-163">Prima **CTRL + X** ou, na barra de ferramentas, clique em de **Cortar** ícone, ou no **editar** menu, clique em **Cortar**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="fecbe-164">Colar o texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="fecbe-164">To paste text into the Script Pane</span></span>
<span data-ttu-id="fecbe-165">Prima **CTRL + V** ou, na barra de ferramentas, clique em de **colar** ícone, ou no **editar** menu, clique em **colar**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="fecbe-166">Para anular uma ação no painel de Script</span><span class="sxs-lookup"><span data-stu-id="fecbe-166">To undo an action in the Script Pane</span></span>
<span data-ttu-id="fecbe-167">Prima **CTRL + Z** ou, na barra de ferramentas, clique em de **anular** ícone, ou no **editar** menu, clique em **anular**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="fecbe-168">Refazer uma ação no painel de Script</span><span class="sxs-lookup"><span data-stu-id="fecbe-168">To redo an action in the Script Pane</span></span>
<span data-ttu-id="fecbe-169">Prima **CTRL + Y** ou, na barra de ferramentas, clique em de **Refazer** ícone, ou no **editar** menu, clique em **Refazer**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="fecbe-170">Como guardar um script</span><span class="sxs-lookup"><span data-stu-id="fecbe-170">How to save a script</span></span>
<span data-ttu-id="fecbe-171">Utilize os seguintes passos para guardar e nome de um script.</span><span class="sxs-lookup"><span data-stu-id="fecbe-171">Use the following steps to save and name a script.</span></span> <span data-ttu-id="fecbe-172">Um asterisco é apresentado junto ao nome do script para marcar um ficheiro que não foi guardado, desde que foi alterado.</span><span class="sxs-lookup"><span data-stu-id="fecbe-172">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="fecbe-173">O asterisco desaparece quando o ficheiro é guardado.</span><span class="sxs-lookup"><span data-stu-id="fecbe-173">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="fecbe-174">Para guardar um script</span><span class="sxs-lookup"><span data-stu-id="fecbe-174">To save a script</span></span>
<span data-ttu-id="fecbe-175">Prima **CTRL + G** ou, na barra de ferramentas, clique em de **guardar** ícone, ou no **ficheiro** menu, clique em **guardar**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-175">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="fecbe-176">Para guardar e nome de um script</span><span class="sxs-lookup"><span data-stu-id="fecbe-176">To save and name a script</span></span>

1. <span data-ttu-id="fecbe-177">No **ficheiro** menu, clique em **guardar como**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-177">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="fecbe-178">O **guardar como** será apresentada a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="fecbe-178">The **Save As** dialog box will appear.</span></span>

2. <span data-ttu-id="fecbe-179">No **nome de ficheiro** box, introduza um nome para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="fecbe-179">In the **File name** box, enter a name for the file.</span></span>

3. <span data-ttu-id="fecbe-180">No **guardar como tipo** caixa, selecione um tipo de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="fecbe-180">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="fecbe-181">Por exemplo, no **guardar como tipo** caixa, selecione ' œPowerShell Scripts (\* . ps1)'.</span><span class="sxs-lookup"><span data-stu-id="fecbe-181">For example, in the **Save as type** box, select 'œPowerShell Scripts (\* .ps1)'.</span></span>

4. <span data-ttu-id="fecbe-182">Clique em **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="fecbe-182">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="fecbe-183">Para guardar um script num codificação ASCII</span><span class="sxs-lookup"><span data-stu-id="fecbe-183">To save a script in ASCII encoding</span></span>
<span data-ttu-id="fecbe-184">Por predefinição, ISE do Windows PowerShell guarda novos ficheiros de script (. ps1), ficheiros de dados do script (. psd1) e os ficheiros do módulo de script (. psm1) como Unicode (BigEndianUnicode) por predefinição. Â para guardar um script na codificação outro, tais como ASCII (ANSI), utilize o **guardar** ou **SaveAs** os métodos no [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) objeto.</span><span class="sxs-lookup"><span data-stu-id="fecbe-184">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="fecbe-185">O comando seguinte guarda um script novo como MyScript.ps1 com codificação ASCII.</span><span class="sxs-lookup"><span data-stu-id="fecbe-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="fecbe-186">O seguinte comando substitui o ficheiro de script atual com um ficheiro com o mesmo nome mas com codificação ASCII.</span><span class="sxs-lookup"><span data-stu-id="fecbe-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="fecbe-187">O seguinte comando obtém a codificação do ficheiro atual.</span><span class="sxs-lookup"><span data-stu-id="fecbe-187">The following command gets the encoding of the current file.</span></span>

```
$psise.CurrentFile.encoding
```

<span data-ttu-id="fecbe-188">ISE do Windows PowerShell suporta as seguintes opções de codificação: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e predefinido.</span><span class="sxs-lookup"><span data-stu-id="fecbe-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="fecbe-189">O valor da opção predefinida varia de acordo com o sistema.</span><span class="sxs-lookup"><span data-stu-id="fecbe-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="fecbe-190">ISE do Windows PowerShell não altera a codificação de scripts que foram criadas por em outros editores, mesmo quando utiliza o guardar ou guardar como comandos no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fecbe-190">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="fecbe-191">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="fecbe-191">See Also</span></span>
- [<span data-ttu-id="fecbe-192">Explorar o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fecbe-192">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
