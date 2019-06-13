---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Novidades no PowerShell 50 ISE
ms.openlocfilehash: 52e8926a7320f86f2ab8970a7778faba6a14a714
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030028"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a><span data-ttu-id="e0651-103">O que&#39;novidade do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0651-103">What&#39;s New in the Windows PowerShell ISE</span></span>
<span data-ttu-id="e0651-104">Este tópico explica os recursos novos e atualizados que foram introduzidos em versões do Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="e0651-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell  Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="e0651-105">Descrição da funcionalidade</span><span class="sxs-lookup"><span data-stu-id="e0651-105">Feature description</span></span>
<span data-ttu-id="e0651-106">ISE do Windows PowerShell é um aplicativo de host que permite-lhe escrever, executar e testar scripts e módulos num ambiente de gráfico e intuitivo.</span><span class="sxs-lookup"><span data-stu-id="e0651-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="e0651-107">Funcionalidades vitais, como a sintaxe de codificação por cores, separador de conclusão, depuração visual, conformidade de Unicode e ajuda sensível ao contexto fornecem uma Rica experiência de criação de scripts.</span><span class="sxs-lookup"><span data-stu-id="e0651-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="e0651-108">Para uma descrição geral do ISE do Windows PowerShell, consulte [descrição geral do Windows PowerShell Integrated Scripting ambiente](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span><span class="sxs-lookup"><span data-stu-id="e0651-108">For an overview of Windows PowerShell ISE, see [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span></span>

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a><span data-ttu-id="e0651-109">Funcionalidades novas e alteradas no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0651-109">New and changed functionality in Windows PowerShell ISE</span></span>
<span data-ttu-id="e0651-110">A tabela seguinte lista as funcionalidades novas e alteradas para esta versão do Windows PowerShell ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0651-110">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

|<span data-ttu-id="e0651-111">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="e0651-111">Feature/functionality</span></span>|<span data-ttu-id="e0651-112">Windows PowerShell ISE 4.0</span><span class="sxs-lookup"><span data-stu-id="e0651-112">Windows PowerShell ISE 4.0</span></span>|<span data-ttu-id="e0651-113">Windows PowerShell ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="e0651-113">Windows PowerShell ISE 3.0</span></span>|<span data-ttu-id="e0651-114">Windows PowerShell ISE 2.0</span><span class="sxs-lookup"><span data-stu-id="e0651-114">Windows PowerShell ISE 2.0</span></span>|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|<span data-ttu-id="e0651-115">**[IntelliSense](#intellisense)**</span><span class="sxs-lookup"><span data-stu-id="e0651-115">**[IntelliSense](#intellisense)**</span></span>|<span data-ttu-id="e0651-116">X</span><span class="sxs-lookup"><span data-stu-id="e0651-116">X</span></span>|<span data-ttu-id="e0651-117">X</span><span class="sxs-lookup"><span data-stu-id="e0651-117">X</span></span>||
|<span data-ttu-id="e0651-118">**[Trechos de código](#snippets)**</span><span class="sxs-lookup"><span data-stu-id="e0651-118">**[Snippets](#snippets)**</span></span>|<span data-ttu-id="e0651-119">X</span><span class="sxs-lookup"><span data-stu-id="e0651-119">X</span></span>|<span data-ttu-id="e0651-120">X</span><span class="sxs-lookup"><span data-stu-id="e0651-120">X</span></span>||
|<span data-ttu-id="e0651-121">**[Ferramentas de suplemento](#add-on-tools)**</span><span class="sxs-lookup"><span data-stu-id="e0651-121">**[Add-on Tools](#add-on-tools)**</span></span>|<span data-ttu-id="e0651-122">X</span><span class="sxs-lookup"><span data-stu-id="e0651-122">X</span></span>|<span data-ttu-id="e0651-123">X</span><span class="sxs-lookup"><span data-stu-id="e0651-123">X</span></span>||
|<span data-ttu-id="e0651-124">**[Gerenciador de reinicialização e salvamento automático](#restart-manager-and-auto-save)**</span><span class="sxs-lookup"><span data-stu-id="e0651-124">**[Restart Manager and Auto-save](#restart-manager-and-auto-save)**</span></span>|<span data-ttu-id="e0651-125">X</span><span class="sxs-lookup"><span data-stu-id="e0651-125">X</span></span>|<span data-ttu-id="e0651-126">X</span><span class="sxs-lookup"><span data-stu-id="e0651-126">X</span></span>||
|<span data-ttu-id="e0651-127">**[Mais recentemente utilizado lista](#most-recently-used-list)**</span><span class="sxs-lookup"><span data-stu-id="e0651-127">**[Most-recently used list](#most-recently-used-list)**</span></span>|<span data-ttu-id="e0651-128">X</span><span class="sxs-lookup"><span data-stu-id="e0651-128">X</span></span>|<span data-ttu-id="e0651-129">X</span><span class="sxs-lookup"><span data-stu-id="e0651-129">X</span></span>||
|<span data-ttu-id="e0651-130">**[Painel de consola](#console-pane)**</span><span class="sxs-lookup"><span data-stu-id="e0651-130">**[Console Pane](#console-pane)**</span></span>|<span data-ttu-id="e0651-131">X</span><span class="sxs-lookup"><span data-stu-id="e0651-131">X</span></span>|<span data-ttu-id="e0651-132">X</span><span class="sxs-lookup"><span data-stu-id="e0651-132">X</span></span>||
|<span data-ttu-id="e0651-133">**[Opções da linha de comandos](#command-line-switches)**</span><span class="sxs-lookup"><span data-stu-id="e0651-133">**[Command-line switches](#command-line-switches)**</span></span>|<span data-ttu-id="e0651-134">X</span><span class="sxs-lookup"><span data-stu-id="e0651-134">X</span></span>|<span data-ttu-id="e0651-135">X</span><span class="sxs-lookup"><span data-stu-id="e0651-135">X</span></span>||
|<span data-ttu-id="e0651-136">**[Novos recursos do editor](#new-editor-features)**</span><span class="sxs-lookup"><span data-stu-id="e0651-136">**[New editor features](#new-editor-features)**</span></span>|<span data-ttu-id="e0651-137">X</span><span class="sxs-lookup"><span data-stu-id="e0651-137">X</span></span>|<span data-ttu-id="e0651-138">X</span><span class="sxs-lookup"><span data-stu-id="e0651-138">X</span></span>||
|<span data-ttu-id="e0651-139">**[Nova janela de Visualizador da ajuda](#new-help-viewer-window)**</span><span class="sxs-lookup"><span data-stu-id="e0651-139">**[New Help viewer window](#new-help-viewer-window)**</span></span>|<span data-ttu-id="e0651-140">X</span><span class="sxs-lookup"><span data-stu-id="e0651-140">X</span></span>|<span data-ttu-id="e0651-141">X</span><span class="sxs-lookup"><span data-stu-id="e0651-141">X</span></span>||
|<span data-ttu-id="e0651-142">**[Cmdlet de comando show](#show-command-cmdlet)**</span><span class="sxs-lookup"><span data-stu-id="e0651-142">**[Show-Command cmdlet](#show-command-cmdlet)**</span></span>|<span data-ttu-id="e0651-143">X</span><span class="sxs-lookup"><span data-stu-id="e0651-143">X</span></span>|<span data-ttu-id="e0651-144">X</span><span class="sxs-lookup"><span data-stu-id="e0651-144">X</span></span>||

### <a name="intellisense"></a><span data-ttu-id="e0651-145">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="e0651-145">IntelliSense</span></span>
<span data-ttu-id="e0651-146">**Adicionado no ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="e0651-146">**Added in ISE 3.0**</span></span>

<span data-ttu-id="e0651-147">IntelliSense é uma funcionalidade de assistência de preenchimento automático que faz parte do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0651-147">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span> <span data-ttu-id="e0651-148">O IntelliSense apresenta clicáveis menus de potencialmente correspondentes cmdlets, parâmetros, valores de parâmetros, ficheiros ou pastas à medida que escreve.</span><span class="sxs-lookup"><span data-stu-id="e0651-148">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="e0651-149">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="e0651-149">**What value does this change add?**</span></span>

<span data-ttu-id="e0651-150">Com a adição do IntelliSense, é mais fácil detetar os cmdlets e sintaxe ao utilizar o ISE do Windows PowerShell para criar scripts.</span><span class="sxs-lookup"><span data-stu-id="e0651-150">With the addition of IntelliSense, it is easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="e0651-151">Também pode utilizar o ISE do Windows PowerShell para obter o Windows PowerShell enquanto cria novos scripts.</span><span class="sxs-lookup"><span data-stu-id="e0651-151">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="e0651-152">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="e0651-152">**What works differently?**</span></span>

<span data-ttu-id="e0651-153">Quando escreve cmdlets no Windows PowerShell ISE 3.0 ou posterior, apresenta um menu rolável e clicável, permitindo que navegue e selecione os comandos apropriados.</span><span class="sxs-lookup"><span data-stu-id="e0651-153">When you type cmdlets in the Windows PowerShell ISE 3.0 or later, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

### <a name="snippets"></a><span data-ttu-id="e0651-154">Trechos de código</span><span class="sxs-lookup"><span data-stu-id="e0651-154">Snippets</span></span>
<span data-ttu-id="e0651-155">**Adicionado no ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="e0651-155">**Added in ISE 3.0**</span></span>

<span data-ttu-id="e0651-156">*Trechos de código* são curtas seções de código do Windows PowerShell que pode inserir em scripts que criar no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0651-156">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="e0651-157">ISE do Windows PowerShell vem com um conjunto predefinido de trechos de código.</span><span class="sxs-lookup"><span data-stu-id="e0651-157">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="e0651-158">Pode adicionar trechos de código utilizando o **New-fragmento** cmdlet enquanto trabalha no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0651-158">You can add snippets by using the **New-Snippet** cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="e0651-159">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="e0651-159">**What value does this change add?**</span></span>

<span data-ttu-id="e0651-160">Ao usar trechos de código, pode rapidamente montar e criar scripts para automatizar o seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="e0651-160">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="e0651-161">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="e0651-161">**What works differently?**</span></span>

<span data-ttu-id="e0651-162">Para utilizar em trechos de código no Windows PowerShell 3.0 ou posterior, o **editar** menu, clique em **iniciar trechos de código**, ou prima **Ctrl-J**.</span><span class="sxs-lookup"><span data-stu-id="e0651-162">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press **Ctrl-J**.</span></span>

### <a name="add-on-tools"></a><span data-ttu-id="e0651-163">Ferramentas de suplemento</span><span class="sxs-lookup"><span data-stu-id="e0651-163">Add-on tools</span></span>
<span data-ttu-id="e0651-164">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="e0651-164">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="e0651-165">ISE do Windows PowerShell agora oferece suporte a ferramentas de suplemento, que são controles do Windows Presentation Foundation (WPF) que são adicionados ao utilizar o modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="e0651-165">Windows PowerShell ISE now supports add-on tools, which are Windows Presentation Foundation (WPF) controls that are added by using the object model.</span></span> <span data-ttu-id="e0651-166">Ferramentas de suplemento podem ser apresentadas como um painel vertical ou horizontal na consola do.</span><span class="sxs-lookup"><span data-stu-id="e0651-166">Add-on tools can be displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="e0651-167">Várias ferramentas de suplemento num painel são apresentadas como um controle com guias.</span><span class="sxs-lookup"><span data-stu-id="e0651-167">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="e0651-168">Também pode adicionar ou remover as ferramentas de suplemento que são produzidas por partes não são da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e0651-168">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="e0651-169">Para obter mais informações sobre como importar ou remover as ferramentas de suplemento, consulte [operações de ISE do Windows PowerShell](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="e0651-169">For more information about how to import or remove add-on tools, see [Windows PowerShell ISE Operations](https://technet.microsoft.com/library/cc732148.aspx).</span></span>

<span data-ttu-id="e0651-170">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="e0651-170">**What value does this change add?**</span></span>

<span data-ttu-id="e0651-171">Suplementos permitem-lhe expandir e personalizar o ISE do Windows PowerShell com ferramentas que podem aprimorar sua experiência de criação de scripts ou adicionar funcionalidade ao ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0651-171">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that can enhance your scripting experience or add functionality to Windows PowerShell ISE.</span></span>

<span data-ttu-id="e0651-172">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="e0651-172">**What works differently?**</span></span>

<span data-ttu-id="e0651-173">Windows PowerShell ISE 3.0 e versões posterior são fornecidos com o **comandos** suplemento.</span><span class="sxs-lookup"><span data-stu-id="e0651-173">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="e0651-174">O **comandos** suplemento permite-lhe procurar os cmdlets e aceder à ajuda sobre a cmdlets lado a lado com o **Script** e **consola** painéis.</span><span class="sxs-lookup"><span data-stu-id="e0651-174">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="e0651-175">Suplementos adicionais podem ser encontrados ao utilizar o **Web site de ferramentas de suplemento aberto** comando o **suplementos** menu.</span><span class="sxs-lookup"><span data-stu-id="e0651-175">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

### <a name="restart-manager-and-auto-save"></a><span data-ttu-id="e0651-176">Gerenciador de reinicialização e salvamento automático</span><span class="sxs-lookup"><span data-stu-id="e0651-176">Restart manager and auto-save</span></span>
<span data-ttu-id="e0651-177">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="e0651-177">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="e0651-178">ISE do Windows PowerShell agora guarda automaticamente seus scripts abertos a cada dois minutos, num local separado.</span><span class="sxs-lookup"><span data-stu-id="e0651-178">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span>  <span data-ttu-id="e0651-179">Se o ISE do Windows PowerShell deixa de funcionar ou se o sistema operativo for reiniciado, após o reinício do Windows PowerShell ISE, ele recupera scripts que foram abrir na última sessão, mesmo que os scripts não foram guardados.</span><span class="sxs-lookup"><span data-stu-id="e0651-179">If Windows PowerShell ISE stops working, or if the operating system is restarted, after Windows PowerShell ISE restarts, it recovers scripts that were open in the last session, even if the scripts were not saved.</span></span>

<span data-ttu-id="e0651-180">Para alterar o intervalo de salvamento automático, execute o seguinte comando no painel da consola: **$psise. Options.AutoSaveMinuteInterval**.</span><span class="sxs-lookup"><span data-stu-id="e0651-180">To change the automatic saving interval, run the following command in the Console pane: **$psise.Options.AutoSaveMinuteInterval**.</span></span>

<span data-ttu-id="e0651-181">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="e0651-181">**What value does this change add?**</span></span>

<span data-ttu-id="e0651-182">Agora, pode trabalhar no ISE do Windows PowerShell, sabendo que os seus scripts abertos são guardadas automaticamente em caso de uma reinicialização inesperada.</span><span class="sxs-lookup"><span data-stu-id="e0651-182">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved in the event of an unexpected restart.</span></span>

<span data-ttu-id="e0651-183">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="e0651-183">**What works differently?**</span></span>

<span data-ttu-id="e0651-184">Windows PowerShell ISE 2.0 não guardar os scripts automaticamente em caso de um reinício.</span><span class="sxs-lookup"><span data-stu-id="e0651-184">Windows PowerShell ISE 2.0 does not save the scripts automatically in the event of a restart.</span></span>

### <a name="most-recently-used-list"></a><span data-ttu-id="e0651-185">Mais recentemente utilizado lista</span><span class="sxs-lookup"><span data-stu-id="e0651-185">Most-recently used list</span></span>
<span data-ttu-id="e0651-186">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="e0651-186">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="e0651-187">ISE do Windows PowerShell tem agora uma lista mais recentemente utilizada para ficheiros.</span><span class="sxs-lookup"><span data-stu-id="e0651-187">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="e0651-188">Quando abre um ficheiro no ISE do Windows PowerShell, o arquivo for adicionado à lista mais recentemente utilizada no **ficheiro** menu.</span><span class="sxs-lookup"><span data-stu-id="e0651-188">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="e0651-189">Para alterar o número predefinido de arquivos na lista de mais recentemente utilizado, execute o seguinte comando no painel da consola: **$psise. Options.MruCount**.</span><span class="sxs-lookup"><span data-stu-id="e0651-189">To change the default number of files in the most-recently used list, run the following command in the Console Pane: **$psise.Options.MruCount**.</span></span>

<span data-ttu-id="e0651-190">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="e0651-190">**What value does this change add?**</span></span>

<span data-ttu-id="e0651-191">Agora, pode utilizar a lista mais recentemente utilizada para aceder facilmente aos seus arquivos usados com frequência.</span><span class="sxs-lookup"><span data-stu-id="e0651-191">You can now use the most-recently used list to easily access your frequently-used files.</span></span>

<span data-ttu-id="e0651-192">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="e0651-192">**What works differently?**</span></span>

<span data-ttu-id="e0651-193">Windows PowerShell ISE 2.0 não tem uma lista mais recentemente utilizada.</span><span class="sxs-lookup"><span data-stu-id="e0651-193">Windows PowerShell ISE 2.0 does not have a most-recently used list.</span></span>

### <a name="console-pane"></a><span data-ttu-id="e0651-194">Painel de consola</span><span class="sxs-lookup"><span data-stu-id="e0651-194">Console Pane</span></span>
<span data-ttu-id="e0651-195">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="e0651-195">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="e0651-196">O comando separado e os painéis de saída que estavam disponíveis na primeira versão do Windows PowerShell ISE foram combinados num único painel de consola.</span><span class="sxs-lookup"><span data-stu-id="e0651-196">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="e0651-197">O painel de consola é semelhante em função e a aparência de uma consola típica do Windows PowerShell, mas inclui os seguintes aprimoramentos (a maioria é descrita neste tópico).</span><span class="sxs-lookup"><span data-stu-id="e0651-197">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements (most are described in this topic).</span></span>

- <span data-ttu-id="e0651-198">Cores da sintaxe para texto de entrada (não texto de saída), incluindo sintaxe XML</span><span class="sxs-lookup"><span data-stu-id="e0651-198">Syntax coloring for input text (not output text), including XML syntax</span></span>

- <span data-ttu-id="e0651-199">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="e0651-199">IntelliSense</span></span>

- <span data-ttu-id="e0651-200">Correspondência de chave</span><span class="sxs-lookup"><span data-stu-id="e0651-200">Brace matching</span></span>

- <span data-ttu-id="e0651-201">Indicação do erro</span><span class="sxs-lookup"><span data-stu-id="e0651-201">Error indication</span></span>

- <span data-ttu-id="e0651-202">Suporte completo a Unicode</span><span class="sxs-lookup"><span data-stu-id="e0651-202">Full Unicode support</span></span>

- <span data-ttu-id="e0651-203">**F1** ajuda sensível ao contexto</span><span class="sxs-lookup"><span data-stu-id="e0651-203">**F1** context-sensitive help</span></span>

- <span data-ttu-id="e0651-204">**CTRL + F1** sensível ao contexto de comando de Show</span><span class="sxs-lookup"><span data-stu-id="e0651-204">**Ctrl+F1** context-sensitive Show-Command</span></span>

- <span data-ttu-id="e0651-205">Script complexo e suporte da direita para a esquerda</span><span class="sxs-lookup"><span data-stu-id="e0651-205">Complex script and right-to-left support</span></span>

- <span data-ttu-id="e0651-206">Suporte de tipo de letra</span><span class="sxs-lookup"><span data-stu-id="e0651-206">Font support</span></span>

- <span data-ttu-id="e0651-207">Zoom</span><span class="sxs-lookup"><span data-stu-id="e0651-207">Zoom</span></span>

- <span data-ttu-id="e0651-208">Modos de seleção de linha e selecione de bloco</span><span class="sxs-lookup"><span data-stu-id="e0651-208">Line-select and block-select modes</span></span>

- <span data-ttu-id="e0651-209">Preservação de conteúdo digitado na linha de comandos quando pressiona o **cópia** seta para ver o histórico na consola do</span><span class="sxs-lookup"><span data-stu-id="e0651-209">Preservation of typed content at the command line when you press the **Up** arrow to view history in the console</span></span>

<span data-ttu-id="e0651-210">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="e0651-210">**What value does this change add?**</span></span>

<span data-ttu-id="e0651-211">A adição dessas alterações de painel de consola fornece uma experiência de criação de scripts mais consistente com a interface de console.</span><span class="sxs-lookup"><span data-stu-id="e0651-211">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="e0651-212">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="e0651-212">**What works differently?**</span></span>

<span data-ttu-id="e0651-213">Windows PowerShell ISE 2.0 tem separado de comando e painéis de saída.</span><span class="sxs-lookup"><span data-stu-id="e0651-213">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

### <a name="command-line-switches"></a><span data-ttu-id="e0651-214">Opções da linha de comandos</span><span class="sxs-lookup"><span data-stu-id="e0651-214">Command-line switches</span></span>
<span data-ttu-id="e0651-215">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="e0651-215">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="e0651-216">Se iniciar o ISE do Windows PowerShell a partir da linha de comandos (digitando **powershell_ise.exe**), pode adicionar os seguintes parâmetros de linha de comando novo.</span><span class="sxs-lookup"><span data-stu-id="e0651-216">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="e0651-217">*-NoProfile*: Inicia o ISE do Windows PowerShell sem execução **$profile**</span><span class="sxs-lookup"><span data-stu-id="e0651-217">*-NoProfile*: Starts Windows PowerShell ISE without running **$profile**</span></span>

- <span data-ttu-id="e0651-218">*-Help*: Exibe uma janela de ajuda</span><span class="sxs-lookup"><span data-stu-id="e0651-218">*-Help*: Displays a Help window</span></span>

- <span data-ttu-id="e0651-219">*-mta*: Inicia o ISE do Windows PowerShell no modo multithreaded apartment.</span><span class="sxs-lookup"><span data-stu-id="e0651-219">*-mta*: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="e0651-220">O modo de operação do padrão do Windows PowerShell ISE é o modo de apartamento de thread único, ou *- sta*.</span><span class="sxs-lookup"><span data-stu-id="e0651-220">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or *-sta*.</span></span>

<span data-ttu-id="e0651-221">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="e0651-221">**What value does this change add?**</span></span>

<span data-ttu-id="e0651-222">A adição desses interruptores de linha de comando permite-lhe controlar o ambiente no qual o ISE do Windows PowerShell é executado.</span><span class="sxs-lookup"><span data-stu-id="e0651-222">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="e0651-223">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="e0651-223">**What works differently?**</span></span>

<span data-ttu-id="e0651-224">Windows PowerShell ISE 2.0 não reconhece esses comutadores da linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="e0651-224">Windows PowerShell ISE 2.0 does not recognize these command-line switches.</span></span>

### <a name="new-editor-features"></a><span data-ttu-id="e0651-225">Novos recursos do editor</span><span class="sxs-lookup"><span data-stu-id="e0651-225">New editor features</span></span>
<span data-ttu-id="e0651-226">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="e0651-226">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="e0651-227">Outras funcionalidades de edição do Windows PowerShell ISE incluem:</span><span class="sxs-lookup"><span data-stu-id="e0651-227">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="e0651-228">**Cores de sintaxe XML**ISE do Windows PowerShell agora as cores sintaxe XML da mesma forma como ele cores a sintaxe do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0651-228">**XML syntax coloring**Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>

- <span data-ttu-id="e0651-229">**Correspondência de chaves** ISE do Windows PowerShell inclui a correspondência de chaves e realce e pode ser usado das seguintes formas: (por exemplo, utilizando o **Ir para correspondência** comando ou **Ctrl +]** localiza o a fechar a chave, se tiver uma chave de abertura selecionado).</span><span class="sxs-lookup"><span data-stu-id="e0651-229">**Brace matching** Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or **Ctrl + ]** locates the closing brace, if you have an opening brace selected).</span></span>

- <span data-ttu-id="e0651-230">**Descrever vista** o painel de Script suporta descrevendo, que permite que o recolhimento ou expandir seções do código ao clicar em mais ou menos, que inicia sessão na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="e0651-230">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="e0651-231">Pode utilizar chaves ou o **#region** e **#endregion** etiquetas para marcar o início ou fim de uma seção recolhível.</span><span class="sxs-lookup"><span data-stu-id="e0651-231">You can use braces or the **#region** and **#endregion** tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="e0651-232">Para expandir ou fechar todas as regiões, prima **Ctrl + M**.</span><span class="sxs-lookup"><span data-stu-id="e0651-232">To expand or collapse all regions, press **Ctrl + M**.</span></span>

- <span data-ttu-id="e0651-233">**Arraste e largue a edição de texto**ISE do Windows PowerShell agora suporta arrasta e largar a edição de texto.</span><span class="sxs-lookup"><span data-stu-id="e0651-233">**Drag and drop text editing**Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="e0651-234">Pode selecionar qualquer bloco de texto e arrastar esse texto para outra localização num editor ou a consola para mover o texto.</span><span class="sxs-lookup"><span data-stu-id="e0651-234">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="e0651-235">Se mantenha premida a tecla Ctrl enquanto arrasta o texto selecionado, quando soltar o botão do mouse o texto é copiado para a nova localização.</span><span class="sxs-lookup"><span data-stu-id="e0651-235">If you hold down the Ctrl key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="e0651-236">Esta versão do Windows PowerShell ISE, bem como a versão anterior do Windows PowerShell ISE, quando arrastar e soltar arquivos no ISE do Windows PowerShell, o Windows PowerShell ISE abre o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e0651-236">In this version of Windows PowerShell ISE, as well as the previous version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>

- <span data-ttu-id="e0651-237">**Analisar a exibição de erro** erros de análise são indicados com sublinhados vermelhos.</span><span class="sxs-lookup"><span data-stu-id="e0651-237">**Parse error display** Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="e0651-238">Quando coloque o cursor sobre um erro indicado, o texto de descrição apresenta o problema que foi encontrado no código.</span><span class="sxs-lookup"><span data-stu-id="e0651-238">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>

- <span data-ttu-id="e0651-239">**Zoom** pode ser definida a percentagem de zoom do conteúdo da consola, utilizando o controlo de deslize de zoom (no canto inferior direito da janela do Windows PowerShell ISE), ou introduza o comando **$psise.options.Zoom** no painel da consola.</span><span class="sxs-lookup"><span data-stu-id="e0651-239">**Zoom** The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command **$psise.options.Zoom** in the Console Pane.</span></span>

- <span data-ttu-id="e0651-240">**Rich text copiar e colar** copiar para a área de transferência no ISE do Windows PowerShell preserva o tipo de letra, tamanho e as informações de cor da seleção original.</span><span class="sxs-lookup"><span data-stu-id="e0651-240">**Rich text copy and paste** Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>

- <span data-ttu-id="e0651-241">**Bloquear a seleção** pode selecionar um bloco de texto ao premir a tecla ALT ao selecionar o texto no painel de Script com o rato ou ao premir **Alt + Shift + seta**.</span><span class="sxs-lookup"><span data-stu-id="e0651-241">**Block selection** You can select a block of text by holding down the ALT key while selecting text in the Script Pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

<span data-ttu-id="e0651-242">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="e0651-242">**What value does this change add?**</span></span>

<span data-ttu-id="e0651-243">Os recursos de edição adicionais fornecem um ambiente de edição mais consistente e eficiente.</span><span class="sxs-lookup"><span data-stu-id="e0651-243">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="e0651-244">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="e0651-244">**What works differently?**</span></span>

<span data-ttu-id="e0651-245">Estas melhorias de edição não estavam presentes no Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="e0651-245">These editing enhancements were not present in Windows PowerShell ISE 2.0.</span></span>

### <a name="new-help-viewer-window"></a><span data-ttu-id="e0651-246">Nova janela de Visualizador da ajuda</span><span class="sxs-lookup"><span data-stu-id="e0651-246">New Help viewer window</span></span>
<span data-ttu-id="e0651-247">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="e0651-247">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="e0651-248">Se pressionar **F1** quando o cursor está num cmdlet ou, se tiver parte de um cmdlet realçado, o novo Visualizador da ajuda abre ajuda sensível ao contexto sobre o cmdlet realçado.</span><span class="sxs-lookup"><span data-stu-id="e0651-248">If you press **F1** when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="e0651-249">Para apresentar a ajuda do Windows PowerShell sobre, escreva **operadores** no painel de consola e, em seguida, prima **F1**.</span><span class="sxs-lookup"><span data-stu-id="e0651-249">To display Windows PowerShell About help, type  **operators** in the console pane, and then press **F1**.</span></span>

<span data-ttu-id="e0651-250">Antes de utilizar esta funcionalidade, baixe a versão mais atual dos tópicos de ajuda do Windows PowerShell a partir do site da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e0651-250">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="e0651-251">O método mais simples para baixar os tópicos de ajuda é executar o **Update-Help** cmdlet no painel da consola ao executar o ISE do Windows PowerShell como administrador.</span><span class="sxs-lookup"><span data-stu-id="e0651-251">The simplest method for downloading the Help topics is to run the **Update-Help** cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="e0651-252">É possível alterar a onde o **F1** chave procura de ajuda.</span><span class="sxs-lookup"><span data-stu-id="e0651-252">You can alter where the **F1** key looks for Help.</span></span> <span data-ttu-id="e0651-253">Na **ferramentas**/**opções** menu, no **definições gerais** separador, em **outras definições**, pode definir ou limpar o caixa de verificação **utilizar o conteúdo da ajuda local em vez de conteúdo online**.</span><span class="sxs-lookup"><span data-stu-id="e0651-253">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="e0651-254">Se a opção estiver marcada, o cliente procura o ajuda na ajuda do transferido encontradas na pasta de módulos do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e0651-254">If checked, then the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span>  <span data-ttu-id="e0651-255">Se a caixa de verificação está desmarcada, em seguida, o cliente procura na Biblioteca TechNet para a ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e0651-255">If the checkbox is cleared, then the client looks on the TechNet library for the cmdlet help.</span></span>

<span data-ttu-id="e0651-256">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="e0651-256">**What value does this change add?**</span></span>

<span data-ttu-id="e0651-257">Ajuda sensível ao contexto sem sair do seus atual cmdlet ou script fornece uma experiência de aprendizagem contínua.</span><span class="sxs-lookup"><span data-stu-id="e0651-257">Context-sensitive Help without leaving your current cmdlet or script provides a seamless learning experience.</span></span>

<span data-ttu-id="e0651-258">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="e0651-258">**What works differently?**</span></span>

<span data-ttu-id="e0651-259">Pressionar F1 nas versões anteriores do Windows PowerShell ISE abrir o arquivo de ajuda no computador local.</span><span class="sxs-lookup"><span data-stu-id="e0651-259">Pressing F1 in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="e0651-260">No Windows PowerShell ISE 3.0 e versões posteriores, é aberta uma janela que contém a ajuda do cmdlet que é pesquisável e configuráveis.</span><span class="sxs-lookup"><span data-stu-id="e0651-260">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="e0651-261">Esta experiência de ajuda é nova para o Windows PowerShell ISE 3.0 e ajuda Atualizável é novo para o Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e0651-261">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

### <a name="show-command-cmdlet"></a><span data-ttu-id="e0651-262">Cmdlet de comando show</span><span class="sxs-lookup"><span data-stu-id="e0651-262">Show-Command cmdlet</span></span>
<span data-ttu-id="e0651-263">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="e0651-263">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="e0651-264">O **comando Show** cmdlet permite-lhe compor ou executar um cmdlet ou uma função ao preencher um formulário de gráfico.</span><span class="sxs-lookup"><span data-stu-id="e0651-264">The **Show-Command** cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="e0651-265">O formulário permite aos utilizadores trabalhar com o Windows PowerShell num ambiente gráfico.</span><span class="sxs-lookup"><span data-stu-id="e0651-265">The form lets users work with Windows PowerShell in a graphical environment.</span></span> <span data-ttu-id="e0651-266">**Comando show** também possibilita a autores de script para criar uma rápida GUI de acesso baseado em Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0651-266">**Show-Command** also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="e0651-267">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="e0651-267">**What value does this change add?**</span></span>

<span data-ttu-id="e0651-268">Usando **comando Show** nos seus scripts do Windows PowerShell, pode fornecer aos usuários com o ambiente gráfico com as quais está familiarizados.</span><span class="sxs-lookup"><span data-stu-id="e0651-268">By using **Show-Command** in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they are familiar.</span></span> <span data-ttu-id="e0651-269">**Comando show** também pode ajudar os utilizadores introdutórios aprender o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0651-269">**Show-Command** can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="e0651-270">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="e0651-270">**What works differently?**</span></span>

<span data-ttu-id="e0651-271">Comando show é o novo Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="e0651-271">Show-Command is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0651-272">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0651-272">See also</span></span>
<span data-ttu-id="e0651-273">Para obter mais informações sobre como utilizar o ISE do Windows PowerShell no Windows PowerShell, consulte os links a seguir.</span><span class="sxs-lookup"><span data-stu-id="e0651-273">For more information about using Windows PowerShell ISE in Windows PowerShell, see the following links.</span></span>

- [<span data-ttu-id="e0651-274">Explorar o ambiente de script integrado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0651-274">Exploring the Windows PowerShell Integrated Scripting Environment</span></span>](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [<span data-ttu-id="e0651-275">ISE no TechNet Wiki</span><span class="sxs-lookup"><span data-stu-id="e0651-275">ISE on the TechNet Wiki</span></span>](https://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [<span data-ttu-id="e0651-276">Centro de scripts</span><span class="sxs-lookup"><span data-stu-id="e0651-276">Script Center</span></span>](https://technet.microsoft.com/scriptcenter/default)
