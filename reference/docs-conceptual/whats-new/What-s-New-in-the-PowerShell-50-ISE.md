---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Que s novas no PowerShell 50 ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 35b825cfa6ea720d0af3537c5d1b16c5ececb701
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953587"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a><span data-ttu-id="6901f-103">O que&#39;s no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6901f-103">What&#39;s New in the Windows PowerShell ISE</span></span>
<span data-ttu-id="6901f-104">Este tópico explica as funcionalidades novas e atualizadas que foi introduzidas em versões do Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="6901f-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell  Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="6901f-105">Descrição da funcionalidade</span><span class="sxs-lookup"><span data-stu-id="6901f-105">Feature description</span></span>
<span data-ttu-id="6901f-106">O ISE do Windows PowerShell é uma aplicação de anfitrião que permite-lhe escrever, executar e testar scripts e de módulos num ambiente gráfico e intuitivo.</span><span class="sxs-lookup"><span data-stu-id="6901f-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="6901f-107">As principais funcionalidades, tais como cores da sintaxe separador conclusão, depuração visual, compatibilidade de Unicode e ajuda sensível ao contexto fornecer uma experiência avançada do script.</span><span class="sxs-lookup"><span data-stu-id="6901f-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="6901f-108">Para obter uma descrição geral do ISE do Windows PowerShell, consulte [descrição geral do Windows PowerShell Integrated Scripting ambiente](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span><span class="sxs-lookup"><span data-stu-id="6901f-108">For an overview of Windows PowerShell ISE, see [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span></span>

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a><span data-ttu-id="6901f-109">Funcionalidades novas e alteradas no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6901f-109">New and changed functionality in Windows PowerShell ISE</span></span>
<span data-ttu-id="6901f-110">A tabela seguinte lista as funcionalidades novas e alteradas para esta versão do ISE do Windows PowerShell no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6901f-110">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

|<span data-ttu-id="6901f-111">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="6901f-111">Feature/functionality</span></span>|<span data-ttu-id="6901f-112">Windows PowerShell ISE 4.0</span><span class="sxs-lookup"><span data-stu-id="6901f-112">Windows PowerShell ISE 4.0</span></span>|<span data-ttu-id="6901f-113">ISE do Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="6901f-113">Windows PowerShell ISE 3.0</span></span>|<span data-ttu-id="6901f-114">Windows PowerShell ISE 2.0</span><span class="sxs-lookup"><span data-stu-id="6901f-114">Windows PowerShell ISE 2.0</span></span>|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|<span data-ttu-id="6901f-115">**[IntelliSense](#intellisense)**</span><span class="sxs-lookup"><span data-stu-id="6901f-115">**[IntelliSense](#intellisense)**</span></span>|<span data-ttu-id="6901f-116">X</span><span class="sxs-lookup"><span data-stu-id="6901f-116">X</span></span>|<span data-ttu-id="6901f-117">X</span><span class="sxs-lookup"><span data-stu-id="6901f-117">X</span></span>||
|<span data-ttu-id="6901f-118">**[Snippets](#snippets)**</span><span class="sxs-lookup"><span data-stu-id="6901f-118">**[Snippets](#snippets)**</span></span>|<span data-ttu-id="6901f-119">X</span><span class="sxs-lookup"><span data-stu-id="6901f-119">X</span></span>|<span data-ttu-id="6901f-120">X</span><span class="sxs-lookup"><span data-stu-id="6901f-120">X</span></span>||
|<span data-ttu-id="6901f-121">**[Ferramentas de suplemento](#add-on-tools)**</span><span class="sxs-lookup"><span data-stu-id="6901f-121">**[Add-on Tools](#add-on-tools)**</span></span>|<span data-ttu-id="6901f-122">X</span><span class="sxs-lookup"><span data-stu-id="6901f-122">X</span></span>|<span data-ttu-id="6901f-123">X</span><span class="sxs-lookup"><span data-stu-id="6901f-123">X</span></span>||
|<span data-ttu-id="6901f-124">**[Reinicie o gestor e guardar automática](#restart-manager-and-auto-save)**</span><span class="sxs-lookup"><span data-stu-id="6901f-124">**[Restart Manager and Auto-save](#restart-manager-and-auto-save)**</span></span>|<span data-ttu-id="6901f-125">X</span><span class="sxs-lookup"><span data-stu-id="6901f-125">X</span></span>|<span data-ttu-id="6901f-126">X</span><span class="sxs-lookup"><span data-stu-id="6901f-126">X</span></span>||
|<span data-ttu-id="6901f-127">**[Mais recentemente utilizados lista](#most-recently-used-list)**</span><span class="sxs-lookup"><span data-stu-id="6901f-127">**[Most-recently used list](#most-recently-used-list)**</span></span>|<span data-ttu-id="6901f-128">X</span><span class="sxs-lookup"><span data-stu-id="6901f-128">X</span></span>|<span data-ttu-id="6901f-129">X</span><span class="sxs-lookup"><span data-stu-id="6901f-129">X</span></span>||
|<span data-ttu-id="6901f-130">**[Painel de consola](#console-pane)**</span><span class="sxs-lookup"><span data-stu-id="6901f-130">**[Console Pane](#console-pane)**</span></span>|<span data-ttu-id="6901f-131">X</span><span class="sxs-lookup"><span data-stu-id="6901f-131">X</span></span>|<span data-ttu-id="6901f-132">X</span><span class="sxs-lookup"><span data-stu-id="6901f-132">X</span></span>||
|<span data-ttu-id="6901f-133">**[Parâmetros da linha de comandos](#command-line-switches)**</span><span class="sxs-lookup"><span data-stu-id="6901f-133">**[Command-line switches](#command-line-switches)**</span></span>|<span data-ttu-id="6901f-134">X</span><span class="sxs-lookup"><span data-stu-id="6901f-134">X</span></span>|<span data-ttu-id="6901f-135">X</span><span class="sxs-lookup"><span data-stu-id="6901f-135">X</span></span>||
|<span data-ttu-id="6901f-136">**[Novas funcionalidades de editor](#new-editor-features)**</span><span class="sxs-lookup"><span data-stu-id="6901f-136">**[New editor features](#new-editor-features)**</span></span>|<span data-ttu-id="6901f-137">X</span><span class="sxs-lookup"><span data-stu-id="6901f-137">X</span></span>|<span data-ttu-id="6901f-138">X</span><span class="sxs-lookup"><span data-stu-id="6901f-138">X</span></span>||
|<span data-ttu-id="6901f-139">**[Nova janela de Visualizador da ajuda](#new-help-viewer-window)**</span><span class="sxs-lookup"><span data-stu-id="6901f-139">**[New Help viewer window](#new-help-viewer-window)**</span></span>|<span data-ttu-id="6901f-140">X</span><span class="sxs-lookup"><span data-stu-id="6901f-140">X</span></span>|<span data-ttu-id="6901f-141">X</span><span class="sxs-lookup"><span data-stu-id="6901f-141">X</span></span>||
|<span data-ttu-id="6901f-142">**[Mostrar comando cmdlet](#show-command-cmdlet)**</span><span class="sxs-lookup"><span data-stu-id="6901f-142">**[Show-Command cmdlet](#show-command-cmdlet)**</span></span>|<span data-ttu-id="6901f-143">X</span><span class="sxs-lookup"><span data-stu-id="6901f-143">X</span></span>|<span data-ttu-id="6901f-144">X</span><span class="sxs-lookup"><span data-stu-id="6901f-144">X</span></span>||

### <a name="intellisense"></a><span data-ttu-id="6901f-145">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="6901f-145">IntelliSense</span></span>
<span data-ttu-id="6901f-146">**Adicionado no ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="6901f-146">**Added in ISE 3.0**</span></span>

<span data-ttu-id="6901f-147">O IntelliSense é uma funcionalidade de assistência de conclusão automática que faz parte do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6901f-147">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span> <span data-ttu-id="6901f-148">O IntelliSense mostra clicáveis menus de correspondência potencialmente cmdlets, parâmetros, os valores de parâmetros, os ficheiros ou pastas à medida que escreve.</span><span class="sxs-lookup"><span data-stu-id="6901f-148">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="6901f-149">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="6901f-149">**What value does this change add?**</span></span>

<span data-ttu-id="6901f-150">Com a adição de IntelliSense, é mais fácil detetar os cmdlets e sintaxe quando utilizar o ISE do Windows PowerShell para criar scripts.</span><span class="sxs-lookup"><span data-stu-id="6901f-150">With the addition of IntelliSense, it is easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="6901f-151">Também pode utilizar o ISE do Windows PowerShell para saber o Windows PowerShell enquanto cria os scripts de novo.</span><span class="sxs-lookup"><span data-stu-id="6901f-151">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="6901f-152">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="6901f-152">**What works differently?**</span></span>

<span data-ttu-id="6901f-153">Quando escreve cmdlets no Windows PowerShell ISE 3.0 ou posterior, apresenta um menu deslocável e clicável, permitindo-lhe procurar e selecionar os comandos apropriados.</span><span class="sxs-lookup"><span data-stu-id="6901f-153">When you type cmdlets in the Windows PowerShell ISE 3.0 or later, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

### <a name="snippets"></a><span data-ttu-id="6901f-154">Fragmentos</span><span class="sxs-lookup"><span data-stu-id="6901f-154">Snippets</span></span>
<span data-ttu-id="6901f-155">**Adicionado no ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="6901f-155">**Added in ISE 3.0**</span></span>

<span data-ttu-id="6901f-156">*Fragmentos* são secções abreviadas do código do Windows PowerShell que pode inserir os scripts que criar no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6901f-156">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="6901f-157">ISE do Windows PowerShell inclui um conjunto predefinido de fragmentos.</span><span class="sxs-lookup"><span data-stu-id="6901f-157">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="6901f-158">Pode adicionar fragmentos utilizando o **New-fragmento** cmdlet ao trabalhar no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6901f-158">You can add snippets by using the **New-Snippet** cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="6901f-159">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="6901f-159">**What value does this change add?**</span></span>

<span data-ttu-id="6901f-160">Ao utilizar fragmentos, pode rapidamente Monte e criar scripts para automatizar o seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="6901f-160">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="6901f-161">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="6901f-161">**What works differently?**</span></span>

<span data-ttu-id="6901f-162">Para utilizar fragmentos do Windows PowerShell 3.0 ou posterior, no **editar** menu, clique em **iniciar fragmentos**, ou prima **Ctrl-J**.</span><span class="sxs-lookup"><span data-stu-id="6901f-162">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press **Ctrl-J**.</span></span>

### <a name="add-on-tools"></a><span data-ttu-id="6901f-163">Ferramentas de suplemento</span><span class="sxs-lookup"><span data-stu-id="6901f-163">Add-on tools</span></span>
<span data-ttu-id="6901f-164">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="6901f-164">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="6901f-165">ISE do Windows PowerShell suporta agora ferramentas de suplemento, que são os controlos de Windows Presentation Foundation (WPF) que são adicionados ao utilizar o modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="6901f-165">Windows PowerShell ISE now supports add-on tools, which are Windows Presentation Foundation (WPF) controls that are added by using the object model.</span></span> <span data-ttu-id="6901f-166">Ferramentas de suplemento podem ser apresentadas como um painel vertical ou horizontal na consola.</span><span class="sxs-lookup"><span data-stu-id="6901f-166">Add-on tools can be displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="6901f-167">Várias ferramentas de suplemento num painel são apresentadas como um controlo de separadores.</span><span class="sxs-lookup"><span data-stu-id="6901f-167">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="6901f-168">Também pode adicionar ou remover as ferramentas de suplementares que são produzidas por entidades confiadoras de terceiros.</span><span class="sxs-lookup"><span data-stu-id="6901f-168">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="6901f-169">Para obter mais informações sobre como importar ou remover as ferramentas de suplemento, consulte [operações do Windows PowerShell ISE](http://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="6901f-169">For more information about how to import or remove add-on tools, see [Windows PowerShell ISE Operations](http://technet.microsoft.com/library/cc732148.aspx).</span></span>

<span data-ttu-id="6901f-170">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="6901f-170">**What value does this change add?**</span></span>

<span data-ttu-id="6901f-171">Suplementos permitem-lhe expandir e personalizar o ISE do Windows PowerShell com ferramentas que podem melhorar a sua experiência de script ou adicionar funcionalidades ao ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6901f-171">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that can enhance your scripting experience or add functionality to Windows PowerShell ISE.</span></span>

<span data-ttu-id="6901f-172">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="6901f-172">**What works differently?**</span></span>

<span data-ttu-id="6901f-173">Windows PowerShell ISE 3.0 e posterior vêm com o **comandos** suplemento.</span><span class="sxs-lookup"><span data-stu-id="6901f-173">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="6901f-174">O **comandos** suplemento permite-lhe procurar os cmdlets e aceder à ajuda sobre o cmdlets do lado do lado a lado com o **Script** e **consola** painéis.</span><span class="sxs-lookup"><span data-stu-id="6901f-174">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="6901f-175">Suplementos adicionais podem ser encontrados utilizando o **Open suplemento ferramentas site** comando no **suplementos** menu.</span><span class="sxs-lookup"><span data-stu-id="6901f-175">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

### <a name="restart-manager-and-auto-save"></a><span data-ttu-id="6901f-176">Reinicie o gestor e guardar automática</span><span class="sxs-lookup"><span data-stu-id="6901f-176">Restart manager and auto-save</span></span>
<span data-ttu-id="6901f-177">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="6901f-177">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="6901f-178">ISE do Windows PowerShell agora guarda automaticamente os scripts Abra cada dois minutos num local separado.</span><span class="sxs-lookup"><span data-stu-id="6901f-178">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span>  <span data-ttu-id="6901f-179">Se o ISE do Windows PowerShell deixa de funcionar, ou se o sistema operativo for reiniciado após o reinício do Windows PowerShell ISE, recupera scripts que foram abra na sessão do último, mesmo se os scripts não foram guardados.</span><span class="sxs-lookup"><span data-stu-id="6901f-179">If Windows PowerShell ISE stops working, or if the operating system is restarted, after Windows PowerShell ISE restarts, it recovers scripts that were open in the last session, even if the scripts were not saved.</span></span>

<span data-ttu-id="6901f-180">Para alterar o intervalo de guardar automático, execute o seguinte comando no painel de consola: **$psise. Options.AutoSaveMinuteInterval**.</span><span class="sxs-lookup"><span data-stu-id="6901f-180">To change the automatic saving interval, run the following command in the Console pane: **$psise.Options.AutoSaveMinuteInterval**.</span></span>

<span data-ttu-id="6901f-181">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="6901f-181">**What value does this change add?**</span></span>

<span data-ttu-id="6901f-182">Agora, pode trabalhar no ISE do Windows PowerShell, sabendo que os scripts abra são guardados automaticamente em caso de um reinício inesperado.</span><span class="sxs-lookup"><span data-stu-id="6901f-182">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved in the event of an unexpected restart.</span></span>

<span data-ttu-id="6901f-183">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="6901f-183">**What works differently?**</span></span>

<span data-ttu-id="6901f-184">O Windows PowerShell ISE 2.0 não guarda os scripts automaticamente em caso de um reinício.</span><span class="sxs-lookup"><span data-stu-id="6901f-184">Windows PowerShell ISE 2.0 does not save the scripts automatically in the event of a restart.</span></span>

### <a name="most-recently-used-list"></a><span data-ttu-id="6901f-185">Mais recentemente utilizados lista</span><span class="sxs-lookup"><span data-stu-id="6901f-185">Most-recently used list</span></span>
<span data-ttu-id="6901f-186">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="6901f-186">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="6901f-187">ISE do Windows PowerShell tem agora uma lista de ficheiros utilizada mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="6901f-187">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="6901f-188">Quando abre um ficheiro no ISE do Windows PowerShell, o ficheiro é adicionado à lista de mais recentemente utilizada no **ficheiro** menu.</span><span class="sxs-lookup"><span data-stu-id="6901f-188">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="6901f-189">Para alterar o número predefinido de ficheiros na lista mais recentemente utilizado, execute o seguinte comando no painel de consola: **$psise. Options.MruCount**.</span><span class="sxs-lookup"><span data-stu-id="6901f-189">To change the default number of files in the most-recently used list, run the following command in the Console Pane: **$psise.Options.MruCount**.</span></span>

<span data-ttu-id="6901f-190">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="6901f-190">**What value does this change add?**</span></span>

<span data-ttu-id="6901f-191">Agora, pode utilizar a lista mais recentemente utilizada para aceder facilmente aos seus ficheiros utilizados frequentemente.</span><span class="sxs-lookup"><span data-stu-id="6901f-191">You can now use the most-recently used list to easily access your frequently-used files.</span></span>

<span data-ttu-id="6901f-192">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="6901f-192">**What works differently?**</span></span>

<span data-ttu-id="6901f-193">O Windows PowerShell ISE 2.0 não tem uma lista mais recentemente utilizada.</span><span class="sxs-lookup"><span data-stu-id="6901f-193">Windows PowerShell ISE 2.0 does not have a most-recently used list.</span></span>

### <a name="console-pane"></a><span data-ttu-id="6901f-194">Painel de consola</span><span class="sxs-lookup"><span data-stu-id="6901f-194">Console Pane</span></span>
<span data-ttu-id="6901f-195">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="6901f-195">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="6901f-196">O comando e os painéis de saída que estavam disponíveis na primeira versão do ISE do Windows PowerShell separado foram combinadas para um painel único de consola.</span><span class="sxs-lookup"><span data-stu-id="6901f-196">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="6901f-197">O painel de consola é semelhante na função e do aspeto a uma consola do Windows PowerShell típica, mas inclui as seguintes melhorias (o máximo é descritos neste tópico).</span><span class="sxs-lookup"><span data-stu-id="6901f-197">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements (most are described in this topic).</span></span>

- <span data-ttu-id="6901f-198">Sintaxe coloração para texto de entrada (não texto de saída), incluindo sintaxe XML</span><span class="sxs-lookup"><span data-stu-id="6901f-198">Syntax coloring for input text (not output text), including XML syntax</span></span>

- <span data-ttu-id="6901f-199">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="6901f-199">IntelliSense</span></span>

- <span data-ttu-id="6901f-200">Chaveta correspondente</span><span class="sxs-lookup"><span data-stu-id="6901f-200">Brace matching</span></span>

- <span data-ttu-id="6901f-201">Indicação de erro</span><span class="sxs-lookup"><span data-stu-id="6901f-201">Error indication</span></span>

- <span data-ttu-id="6901f-202">Suporte de Unicode completo</span><span class="sxs-lookup"><span data-stu-id="6901f-202">Full Unicode support</span></span>

- <span data-ttu-id="6901f-203">**F1** ajuda sensível ao contexto</span><span class="sxs-lookup"><span data-stu-id="6901f-203">**F1** context-sensitive help</span></span>

- <span data-ttu-id="6901f-204">**CTRL + F1** Mostrar-Command sensíveis ao contexto</span><span class="sxs-lookup"><span data-stu-id="6901f-204">**Ctrl+F1** context-sensitive Show-Command</span></span>

- <span data-ttu-id="6901f-205">Script complexa e suporte para a esquerda</span><span class="sxs-lookup"><span data-stu-id="6901f-205">Complex script and right-to-left support</span></span>

- <span data-ttu-id="6901f-206">Suporte de tipo de letra</span><span class="sxs-lookup"><span data-stu-id="6901f-206">Font support</span></span>

- <span data-ttu-id="6901f-207">Zoom</span><span class="sxs-lookup"><span data-stu-id="6901f-207">Zoom</span></span>

- <span data-ttu-id="6901f-208">Selecione linha e selecione bloco modos</span><span class="sxs-lookup"><span data-stu-id="6901f-208">Line-select and block-select modes</span></span>

- <span data-ttu-id="6901f-209">Preservação de conteúdo escrito na linha de comandos quando prime o **segurança** seta para ver o histórico na consola do</span><span class="sxs-lookup"><span data-stu-id="6901f-209">Preservation of typed content at the command line when you press the **Up** arrow to view history in the console</span></span>

<span data-ttu-id="6901f-210">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="6901f-210">**What value does this change add?**</span></span>

<span data-ttu-id="6901f-211">A adição destas alterações de painel de consola fornece uma experiência de script que é mais consistente com a interface da consola.</span><span class="sxs-lookup"><span data-stu-id="6901f-211">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="6901f-212">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="6901f-212">**What works differently?**</span></span>

<span data-ttu-id="6901f-213">O Windows PowerShell ISE 2.0 tem separado comando e painéis de saída.</span><span class="sxs-lookup"><span data-stu-id="6901f-213">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

### <a name="command-line-switches"></a><span data-ttu-id="6901f-214">Parâmetros da linha de comandos</span><span class="sxs-lookup"><span data-stu-id="6901f-214">Command-line switches</span></span>
<span data-ttu-id="6901f-215">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="6901f-215">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="6901f-216">Se iniciar o ISE do Windows PowerShell a partir da linha de comandos (escrevendo **powershell_ise.exe**), pode adicionar os seguintes parâmetros da linha de comandos de novo.</span><span class="sxs-lookup"><span data-stu-id="6901f-216">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="6901f-217">*-NoProfile*: inicia o Windows PowerShell ISE sem execução **$profile**</span><span class="sxs-lookup"><span data-stu-id="6901f-217">*-NoProfile*: Starts Windows PowerShell ISE without running **$profile**</span></span>

- <span data-ttu-id="6901f-218">*-Ajudar*: apresenta uma janela de ajuda</span><span class="sxs-lookup"><span data-stu-id="6901f-218">*-Help*: Displays a Help window</span></span>

- <span data-ttu-id="6901f-219">*-mta*: começa ISE do Windows PowerShell no modo apartment multithread.</span><span class="sxs-lookup"><span data-stu-id="6901f-219">*-mta*: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="6901f-220">O modo de operação de predefinido para o ISE do Windows PowerShell é o modo de apartamento de thread único, ou *- sta*.</span><span class="sxs-lookup"><span data-stu-id="6901f-220">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or *-sta*.</span></span>

<span data-ttu-id="6901f-221">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="6901f-221">**What value does this change add?**</span></span>

<span data-ttu-id="6901f-222">A adição destes parâmetros da linha de comandos permite-lhe controlar o ambiente em que executa o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6901f-222">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="6901f-223">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="6901f-223">**What works differently?**</span></span>

<span data-ttu-id="6901f-224">O Windows PowerShell ISE 2.0 não reconhece estes parâmetros da linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="6901f-224">Windows PowerShell ISE 2.0 does not recognize these command-line switches.</span></span>

### <a name="new-editor-features"></a><span data-ttu-id="6901f-225">Novas funcionalidades de editor</span><span class="sxs-lookup"><span data-stu-id="6901f-225">New editor features</span></span>
<span data-ttu-id="6901f-226">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="6901f-226">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="6901f-227">Outras funcionalidades de edição do ISE do Windows PowerShell incluem:</span><span class="sxs-lookup"><span data-stu-id="6901f-227">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="6901f-228">**XML de cores da sintaxe**ISE do Windows PowerShell cores agora sintaxe XML da mesma forma como este cores sintaxe do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6901f-228">**XML syntax coloring**Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>

- <span data-ttu-id="6901f-229">**Correspondência Chaveta** ISE do Windows PowerShell inclui Chaveta correspondentes e de realce e pode ser utilizado das seguintes formas: (por exemplo, utilizando o **aceda a correspondência** comando ou **Ctrl +]** localiza o fechar a chaveta, se tiver uma chaveta de abertura selecionada).</span><span class="sxs-lookup"><span data-stu-id="6901f-229">**Brace matching** Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or **Ctrl + ]** locates the closing brace, if you have an opening brace selected).</span></span>

- <span data-ttu-id="6901f-230">**Descrevem vista** o painel de Script suporta definido que estipule, que lhe permite collapsing ou expandir secções de código, clicando em mais ou menos inicia na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="6901f-230">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="6901f-231">Pode utilizar chavetas ou **#region** e **#endregion** etiquetas para marcar o início ou fim de uma secção expansível.</span><span class="sxs-lookup"><span data-stu-id="6901f-231">You can use braces or the **#region** and **#endregion** tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="6901f-232">Para expandir ou fechar todas as regiões, prima **Ctrl + M**.</span><span class="sxs-lookup"><span data-stu-id="6901f-232">To expand or collapse all regions, press **Ctrl + M**.</span></span>

- <span data-ttu-id="6901f-233">**Arraste e largue a edição de texto**ISE do Windows PowerShell agora suporta arrastar e largar a edição de texto.</span><span class="sxs-lookup"><span data-stu-id="6901f-233">**Drag and drop text editing**Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="6901f-234">Pode selecionar qualquer bloco de texto e arraste esse texto para outra localização no editor ou a consola para mover o texto.</span><span class="sxs-lookup"><span data-stu-id="6901f-234">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="6901f-235">Se, mantenha premida a tecla Ctrl enquanto arraste o texto seleccionado, quando solta o botão do rato o texto é copiado para a nova localização.</span><span class="sxs-lookup"><span data-stu-id="6901f-235">If you hold down the Ctrl key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="6901f-236">Nesta versão do ISE do Windows PowerShell, bem como a versão anterior do ISE do Windows PowerShell, ao arrastar e largar ficheiros no ISE do Windows PowerShell ISE do Windows PowerShell abre-se o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="6901f-236">In this version of Windows PowerShell ISE, as well as the previous version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>

- <span data-ttu-id="6901f-237">**Analisar a apresentação de erro** erros de análise são indicados com indicação vermelha.</span><span class="sxs-lookup"><span data-stu-id="6901f-237">**Parse error display** Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="6901f-238">Quando paira o rato sobre o erro indicado, o texto da descrição apresenta o problema que foi encontrado no código.</span><span class="sxs-lookup"><span data-stu-id="6901f-238">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>

- <span data-ttu-id="6901f-239">**Zoom** a percentagem de zoom da consola '™ conteúdo s pode ser definido utilizando o controlo de deslize de zoom (no canto inferior direito da janela do Windows PowerShell ISE) ou introduzindo o comando **$psise.options.Zoom** no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="6901f-239">**Zoom** The zoom percentage of the console'™s content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command **$psise.options.Zoom** in the Console Pane.</span></span>

- <span data-ttu-id="6901f-240">**Avançada texto copiar e colar** copiar para a área de transferência no ISE do Windows PowerShell preserva o tipo de letra, tamanho e informações de cor da seleção original.</span><span class="sxs-lookup"><span data-stu-id="6901f-240">**Rich text copy and paste** Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>

- <span data-ttu-id="6901f-241">**Bloquear seleção** pode selecionar um bloco de texto ao premir a tecla ALT ao selecionar o texto no painel de Script com o rato ou premindo **Alt + Shift + seta para a**.</span><span class="sxs-lookup"><span data-stu-id="6901f-241">**Block selection** You can select a block of text by holding down the ALT key while selecting text in the Script Pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

<span data-ttu-id="6901f-242">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="6901f-242">**What value does this change add?**</span></span>

<span data-ttu-id="6901f-243">As funcionalidades adicionais de edição fornecem um ambiente de edição mais consistente e eficiente.</span><span class="sxs-lookup"><span data-stu-id="6901f-243">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="6901f-244">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="6901f-244">**What works differently?**</span></span>

<span data-ttu-id="6901f-245">Estas melhorias de edição não estavam presentes no Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="6901f-245">These editing enhancements were not present in Windows PowerShell ISE 2.0.</span></span>

### <a name="new-help-viewer-window"></a><span data-ttu-id="6901f-246">Nova janela de Visualizador da ajuda</span><span class="sxs-lookup"><span data-stu-id="6901f-246">New Help viewer window</span></span>
<span data-ttu-id="6901f-247">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="6901f-247">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="6901f-248">Se premir **F1** quando o cursor é um cmdlet ou tiver parte de um cmdlet realçado, o novo Visualizador da ajuda abre ajuda sensível ao contexto sobre o cmdlet realçado.</span><span class="sxs-lookup"><span data-stu-id="6901f-248">If you press **F1** when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="6901f-249">Para apresentar a ajuda do Windows PowerShell sobre, escreva **operadores** no painel de consola e, em seguida, prima **F1**.</span><span class="sxs-lookup"><span data-stu-id="6901f-249">To display Windows PowerShell About help, type  **operators** in the console pane, and then press **F1**.</span></span>

<span data-ttu-id="6901f-250">Antes de utilizar esta funcionalidade, transfira a versão mais recente dos tópicos de ajuda do Windows PowerShell a partir do Web site da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6901f-250">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="6901f-251">O método mais simples para transferir os tópicos de ajuda está a ser executado o **Update-Help** cmdlet no painel de consola ao utilizar o ISE do Windows PowerShell como administrador.</span><span class="sxs-lookup"><span data-stu-id="6901f-251">The simplest method for downloading the Help topics is to run the **Update-Help** cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="6901f-252">Pode alterar onde o **F1** chave de procura para obter ajuda.</span><span class="sxs-lookup"><span data-stu-id="6901f-252">You can alter where the **F1** key looks for Help.</span></span> <span data-ttu-id="6901f-253">No **ferramentas**/**opções** menu, no **definições gerais** separador em **outras definições**, pode definir ou limpar o caixa de verificação **utilizar conteúdo de ajuda local em vez de conteúdo online**.</span><span class="sxs-lookup"><span data-stu-id="6901f-253">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="6901f-254">Se a opção estiver marcada, o cliente procura para o cmdlet ajuda na ajuda do transferido encontradas na pasta de módulos.</span><span class="sxs-lookup"><span data-stu-id="6901f-254">If checked, then the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span>  <span data-ttu-id="6901f-255">Se a caixa de verificação está desmarcada, o cliente procura na Biblioteca TechNet para a ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6901f-255">If the checkbox is cleared, then the client looks on the TechNet library for the cmdlet help.</span></span>

<span data-ttu-id="6901f-256">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="6901f-256">**What value does this change add?**</span></span>

<span data-ttu-id="6901f-257">Ajuda sensível ao contexto sem sair sua atual cmdlet ou script fornece uma experiência totalmente integrada de aprendizagem.</span><span class="sxs-lookup"><span data-stu-id="6901f-257">Context-sensitive Help without leaving your current cmdlet or script provides a seamless learning experience.</span></span>

<span data-ttu-id="6901f-258">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="6901f-258">**What works differently?**</span></span>

<span data-ttu-id="6901f-259">Premir F1 em versões anteriores do Windows PowerShell ISE abrir o ficheiro de ajuda no computador local.</span><span class="sxs-lookup"><span data-stu-id="6901f-259">Pressing F1 in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="6901f-260">No Windows PowerShell ISE 3.0 e mais tarde, será apresentada uma janela que contém a ajuda do cmdlet que é configurável e pesquisáveis.</span><span class="sxs-lookup"><span data-stu-id="6901f-260">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="6901f-261">Esta experiência de ajuda é nova no Windows PowerShell ISE 3.0 e ajuda Atualizável é nova no Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="6901f-261">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

### <a name="show-command-cmdlet"></a><span data-ttu-id="6901f-262">Mostrar comando cmdlet</span><span class="sxs-lookup"><span data-stu-id="6901f-262">Show-Command cmdlet</span></span>
<span data-ttu-id="6901f-263">**Adicionado no PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="6901f-263">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="6901f-264">O **Mostrar comando** cmdlet permite-lhe compor ou executar um cmdlet ou uma função ao preencher um formulário gráfico.</span><span class="sxs-lookup"><span data-stu-id="6901f-264">The **Show-Command** cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="6901f-265">O formulário permite aos utilizadores trabalhar com o Windows PowerShell num ambiente gráfico.</span><span class="sxs-lookup"><span data-stu-id="6901f-265">The form lets users work with Windows PowerShell in a graphical environment.</span></span> <span data-ttu-id="6901f-266">**Mostrar comando** também permite avançadas scripters para criar uma rápida GUI de acesso baseado no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6901f-266">**Show-Command** also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="6901f-267">**Que valor acrescenta esta alteração?**</span><span class="sxs-lookup"><span data-stu-id="6901f-267">**What value does this change add?**</span></span>

<span data-ttu-id="6901f-268">Ao utilizar **Mostrar comando** nos scripts do Windows PowerShell, pode fornecer os seus utilizadores com o ambiente gráfico com a qual está familiarizados.</span><span class="sxs-lookup"><span data-stu-id="6901f-268">By using **Show-Command** in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they are familiar.</span></span> <span data-ttu-id="6901f-269">**Mostrar comando** também podem ajudar os utilizadores introdutórias saiba do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6901f-269">**Show-Command** can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="6901f-270">**O que funciona de forma diferente?**</span><span class="sxs-lookup"><span data-stu-id="6901f-270">**What works differently?**</span></span>

<span data-ttu-id="6901f-271">Mostrar comando é novo do Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="6901f-271">Show-Command is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="6901f-272">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6901f-272">See also</span></span>
<span data-ttu-id="6901f-273">Para obter mais informações sobre como utilizar o ISE do Windows PowerShell no Windows PowerShell, consulte as hiperligações seguintes.</span><span class="sxs-lookup"><span data-stu-id="6901f-273">For more information about using Windows PowerShell ISE in Windows PowerShell, see the following links.</span></span>

- [<span data-ttu-id="6901f-274">Explorar o ambiente de script integrada do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6901f-274">Exploring the Windows PowerShell Integrated Scripting Environment</span></span>](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [<span data-ttu-id="6901f-275">ISE no TechNet Wiki</span><span class="sxs-lookup"><span data-stu-id="6901f-275">ISE on the TechNet Wiki</span></span>](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [<span data-ttu-id="6901f-276">Centro de scripts</span><span class="sxs-lookup"><span data-stu-id="6901f-276">Script Center</span></span>](http://technet.microsoft.com/scriptcenter/default)