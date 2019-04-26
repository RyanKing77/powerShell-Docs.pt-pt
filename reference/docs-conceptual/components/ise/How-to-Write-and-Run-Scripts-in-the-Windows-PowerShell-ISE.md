---
ms.date: 08/14/2018
keywords: PowerShell, o cmdlet
title: Como Escrever e Executar Scripts no ISE do Windows PowerShell
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 61db5e18f05e8e334cd9ba6dab2cf15dee7390cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086855"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="dabf9-103">Como Escrever e Executar Scripts no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dabf9-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="dabf9-104">Este artigo descreve como criar, editar, executar e guardar a scripts no painel de Script.</span><span class="sxs-lookup"><span data-stu-id="dabf9-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="dabf9-105">Como criar e executar scripts</span><span class="sxs-lookup"><span data-stu-id="dabf9-105">How to create and run scripts</span></span>

<span data-ttu-id="dabf9-106">Pode abrir e editar ficheiros do Windows PowerShell no painel de Script.</span><span class="sxs-lookup"><span data-stu-id="dabf9-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="dabf9-107">Tipos de ficheiro específicas de interesse no Windows PowerShell são arquivos de script (. ps1), arquivos de dados de script (. psd1) e arquivos de módulo de script (. psm1).</span><span class="sxs-lookup"><span data-stu-id="dabf9-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="dabf9-108">Estes tipos de ficheiro são sintaxe colorido no editor do painel de Script.</span><span class="sxs-lookup"><span data-stu-id="dabf9-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="dabf9-109">Outros tipos de ficheiros comuns, que pode abrir o no painel de Script são arquivos de configuração (.ps1xml), arquivos XML e arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="dabf9-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="dabf9-110">A política de execução do Windows PowerShell determina se pode executar scripts e carregar ficheiros de configuração e de perfis do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dabf9-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="dabf9-111">A diretiva de execução padrão Restricted, impede que todos os scripts em execução e impede que os perfis de carregamento.</span><span class="sxs-lookup"><span data-stu-id="dabf9-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="dabf9-112">Para alterar a diretiva de execução para permitir que os perfis de carga e ser utilizado, consulte [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) e [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="dabf9-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="dabf9-113">Para criar um novo ficheiro de script</span><span class="sxs-lookup"><span data-stu-id="dabf9-113">To create a new script file</span></span>

<span data-ttu-id="dabf9-114">Na barra de ferramentas, clique em **New**, ou no **ficheiro** menu, clique em **New**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="dabf9-115">O ficheiro criado é apresentado num novo separador do arquivo sob a guia atual do PowerShell. Lembre-se de que as guias do PowerShell só estão visíveis quando há mais do que um.</span><span class="sxs-lookup"><span data-stu-id="dabf9-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="dabf9-116">Por predefinição é criado um ficheiro de script de tipo (. ps1), mas pode ser salvo com um novo nome e a extensão.</span><span class="sxs-lookup"><span data-stu-id="dabf9-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="dabf9-117">Podem ser criados vários ficheiros de script no mesmo separador do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dabf9-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="dabf9-118">Para abrir um script existente</span><span class="sxs-lookup"><span data-stu-id="dabf9-118">To open an existing script</span></span>

<span data-ttu-id="dabf9-119">Na barra de ferramentas, clique em **aberto**, ou no **ficheiro** menu, clique em **aberto**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="dabf9-120">Na **abra** diálogo caixa, selecione o ficheiro que pretende abrir.</span><span class="sxs-lookup"><span data-stu-id="dabf9-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="dabf9-121">É apresentado o arquivo aberto num novo separador.</span><span class="sxs-lookup"><span data-stu-id="dabf9-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="dabf9-122">Para fechar um separador de script</span><span class="sxs-lookup"><span data-stu-id="dabf9-122">To close a script tab</span></span>

<span data-ttu-id="dabf9-123">Clique nas **feche** ícone (X) do separador de ficheiro que pretende fechar ou selecione o **ficheiro** menu e clique em **fechar**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-123">Click the **Close** icon (X) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="dabf9-124">Se o ficheiro foi alterado desde que foi guardado pela última vez, lhe for pedido para guardar ou rejeitá-lo.</span><span class="sxs-lookup"><span data-stu-id="dabf9-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="dabf9-125">Para exibir o caminho de ficheiro</span><span class="sxs-lookup"><span data-stu-id="dabf9-125">To display the file path</span></span>

<span data-ttu-id="dabf9-126">No separador ficheiro, aponte para o nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="dabf9-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="dabf9-127">O caminho totalmente qualificado para o ficheiro de script é apresentado numa descrição.</span><span class="sxs-lookup"><span data-stu-id="dabf9-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="dabf9-128">Para executar um script</span><span class="sxs-lookup"><span data-stu-id="dabf9-128">To run a script</span></span>

<span data-ttu-id="dabf9-129">Na barra de ferramentas, clique em **executar Script**, ou no **ficheiro** menu, clique em **executar**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="dabf9-130">Para executar uma parte de um script</span><span class="sxs-lookup"><span data-stu-id="dabf9-130">To run a portion of a script</span></span>

1. <span data-ttu-id="dabf9-131">No painel de Script, selecione uma parte de um script.</span><span class="sxs-lookup"><span data-stu-id="dabf9-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="dabf9-132">Sobre o **arquivo** menu, clique em **Run Selection**, ou na barra de ferramentas, clique em **Run Selection**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="dabf9-133">Para parar um script em execução</span><span class="sxs-lookup"><span data-stu-id="dabf9-133">To stop a running script</span></span>

<span data-ttu-id="dabf9-134">Existem várias formas de parar um script em execução.</span><span class="sxs-lookup"><span data-stu-id="dabf9-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="dabf9-135">Clique em **operação parar** na barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="dabf9-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="dabf9-136">Prima CTRL + BREAK</span><span class="sxs-lookup"><span data-stu-id="dabf9-136">Press CTRL+BREAK</span></span>
- <span data-ttu-id="dabf9-137">Selecione o **arquivo** menu e clique em **parar a operação**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="dabf9-138">Premir **CTRL + C** também funciona, a menos que algum texto atualmente selecionado, caso em que **CTRL + C** mapeia para a função de cópia para o texto selecionado.</span><span class="sxs-lookup"><span data-stu-id="dabf9-138">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="dabf9-139">Como escrever e editar texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="dabf9-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="dabf9-140">Pode copiar, cortar, colar, localizar e substituir texto no painel de Script.</span><span class="sxs-lookup"><span data-stu-id="dabf9-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="dabf9-141">Também pode desfazer e Refazer a última ação que acabou de executar.</span><span class="sxs-lookup"><span data-stu-id="dabf9-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="dabf9-142">Os atalhos de teclado para estas ações são os mesmo atalhos utilizados para todos os aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="dabf9-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="dabf9-143">Introduza o texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="dabf9-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="dabf9-144">Mover o cursor para o painel de scripts ao clicar em qualquer lugar no painel de Script, ou ao clicar **vá para Painel de Script** no **vista** menu.</span><span class="sxs-lookup"><span data-stu-id="dabf9-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="dabf9-145">Crie um script.</span><span class="sxs-lookup"><span data-stu-id="dabf9-145">Create a script.</span></span> <span data-ttu-id="dabf9-146">Sintaxe colorida e conclusão de tabulação fornecem uma experiência mais rica de edição no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dabf9-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="dabf9-147">Ver [como uso de conclusão de tabulação no painel de Script e o painel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obter detalhes sobre como utilizar a funcionalidade de conclusão de separador para ajudar a escrever.</span><span class="sxs-lookup"><span data-stu-id="dabf9-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="dabf9-148">Para localizar texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="dabf9-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="dabf9-149">Para localizar o texto em qualquer lugar, prima **CTRL + F** ou, no **editar** menu, clique em **encontrar no Script**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="dabf9-150">Para localizar o texto após o cursor, prima **F3** ou, no **editar** menu, clique em **Localizar seguinte no Script**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="dabf9-151">Para localizar texto antes do cursor, prima **SHIFT+F3** ou, no **editar** menu, clique em **encontrar anteriores no Script**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="dabf9-152">Para localizar e substituir textos no painel de Script</span><span class="sxs-lookup"><span data-stu-id="dabf9-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="dabf9-153">Prima **CTRL + H** ou, no **editar** menu, clique em **substituir no Script**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="dabf9-154">Introduza o texto que pretende para localizar e o texto de substituição, em seguida, prima **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-154">Enter the text you want to find and the replacement text, then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="dabf9-155">Para ir para uma determinada linha de texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="dabf9-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="dabf9-156">No painel de Script, prima **CTRL + G** ou, no **editar** menu, clique em **vá para a linha**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="dabf9-157">Introduza um número de linha.</span><span class="sxs-lookup"><span data-stu-id="dabf9-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="dabf9-158">Para copiar o texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="dabf9-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="dabf9-159">No painel de Script, selecione o texto que pretende copiar.</span><span class="sxs-lookup"><span data-stu-id="dabf9-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="dabf9-160">Prima **CTRL + C** ou, na barra de ferramentas, clique nas **cópia** ícone, ou no **editar** menu, clique em **cópia**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="dabf9-161">Cortar o texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="dabf9-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="dabf9-162">No painel de Script, selecione o texto que pretende cortar.</span><span class="sxs-lookup"><span data-stu-id="dabf9-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="dabf9-163">Prima **CTRL + X** ou, na barra de ferramentas, clique nas **Cortar** ícone, ou no **editar** menu, clique em **Cortar**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="dabf9-164">Colar o texto no painel de Script</span><span class="sxs-lookup"><span data-stu-id="dabf9-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="dabf9-165">Prima **CTRL + V** ou, na barra de ferramentas, clique nas **colar** ícone, ou no **editar** menu, clique em **colar**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="dabf9-166">Para anular uma ação no painel de Script</span><span class="sxs-lookup"><span data-stu-id="dabf9-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="dabf9-167">Prima **CTRL + Z** ou, na barra de ferramentas, clique nas **anular** ícone, ou no **editar** menu, clique em **anular**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="dabf9-168">Refazer uma ação no painel de Script</span><span class="sxs-lookup"><span data-stu-id="dabf9-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="dabf9-169">Prima **CTRL + Y** ou, na barra de ferramentas, clique nas **Refazer** ícone, ou no **editar** menu, clique em **Refazer**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="dabf9-170">Como guardar um script</span><span class="sxs-lookup"><span data-stu-id="dabf9-170">How to save a script</span></span>

<span data-ttu-id="dabf9-171">Um asterisco é apresentado junto ao nome do script para marcar um arquivo que ainda não foram guardado, desde que foi alterada.</span><span class="sxs-lookup"><span data-stu-id="dabf9-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="dabf9-172">O asterisco desaparece quando o ficheiro é guardado.</span><span class="sxs-lookup"><span data-stu-id="dabf9-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="dabf9-173">Para guardar um script</span><span class="sxs-lookup"><span data-stu-id="dabf9-173">To save a script</span></span>

<span data-ttu-id="dabf9-174">Prima **CTRL + S** ou, na barra de ferramentas, clique nas **guardar** ícone, ou no **ficheiro** menu, clique em **guardar**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-174">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="dabf9-175">Para guardar e nome de um script</span><span class="sxs-lookup"><span data-stu-id="dabf9-175">To save and name a script</span></span>

1. <span data-ttu-id="dabf9-176">Sobre o **arquivo** menu, clique em **guardar como**.</span><span class="sxs-lookup"><span data-stu-id="dabf9-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="dabf9-177">O **guardar como** será apresentada a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="dabf9-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="dabf9-178">Na **nome de ficheiro** , introduza um nome para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="dabf9-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="dabf9-179">Na **guardar como tipo** caixa, selecione um tipo de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="dabf9-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="dabf9-180">Por exemplo, no **guardar como tipo** caixa, selecione "Scripts do PowerShell (\*. ps1)".</span><span class="sxs-lookup"><span data-stu-id="dabf9-180">For example, in the **Save as type** box, select 'PowerShell Scripts (\*.ps1)'.</span></span>
4. <span data-ttu-id="dabf9-181">Clique em **Save** (Guardar).</span><span class="sxs-lookup"><span data-stu-id="dabf9-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="dabf9-182">Para guardar um script na codificação ASCII</span><span class="sxs-lookup"><span data-stu-id="dabf9-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="dabf9-183">Por predefinição, o ISE do Windows PowerShell salva novos arquivos de script (. ps1), arquivos de dados de script (. psd1) e arquivos de módulo de script (. psm1) como Unicode (BigEndianUnicode) por predefinição. Â para guardar um script em outra codificação, como o ASCII (ANSI), utilize o **salvar** ou **SaveAs** métodos no [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="dabf9-183">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="dabf9-184">O comando seguinte guarda um novo script como MyScript.ps1 com codificação ASCII.</span><span class="sxs-lookup"><span data-stu-id="dabf9-184">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="dabf9-185">O comando seguinte substitui o ficheiro de script atual com um ficheiro com o mesmo nome, mas com codificação ASCII.</span><span class="sxs-lookup"><span data-stu-id="dabf9-185">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="dabf9-186">O comando seguinte obtém a codificação do ficheiro atual.</span><span class="sxs-lookup"><span data-stu-id="dabf9-186">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="dabf9-187">ISE do Windows PowerShell suporta as seguintes opções de codificação: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e padrão.</span><span class="sxs-lookup"><span data-stu-id="dabf9-187">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="dabf9-188">O valor da opção predefinida varia de acordo com o sistema.</span><span class="sxs-lookup"><span data-stu-id="dabf9-188">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="dabf9-189">ISE do Windows PowerShell não altera a codificação de ficheiros de script, quando utiliza o guardar ou guardar como comandos.</span><span class="sxs-lookup"><span data-stu-id="dabf9-189">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="dabf9-190">Veja Também</span><span class="sxs-lookup"><span data-stu-id="dabf9-190">See Also</span></span>

- [<span data-ttu-id="dabf9-191">Explorar o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dabf9-191">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
