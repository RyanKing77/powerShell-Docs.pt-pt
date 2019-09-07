---
ms.date: 09/06/2019
keywords: PowerShell, cmdlet
title: O que há de novo no PowerShell 5,0 ISE
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746230"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="59bb9-103">O que há de novo no ISE do Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="59bb9-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="59bb9-104">Este tópico explica os recursos novos e atualizados que foram introduzidos em versões do Ambiente de Script Integrado do Windows PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="59bb9-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="59bb9-105">Descrição da funcionalidade</span><span class="sxs-lookup"><span data-stu-id="59bb9-105">Feature description</span></span>

<span data-ttu-id="59bb9-106">O ISE do Windows PowerShell é um aplicativo host que permite gravar, executar e testar scripts e módulos em um ambiente gráfico e intuitivo.</span><span class="sxs-lookup"><span data-stu-id="59bb9-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="59bb9-107">Os principais recursos, como cores de sintaxe, preenchimento com Tab, depuração Visual, conformidade com Unicode e ajuda contextual fornecem uma experiência de script avançada.</span><span class="sxs-lookup"><span data-stu-id="59bb9-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="59bb9-108">Para obter mais informações, consulte [apresentando o ISE do Windows PowerShell](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span><span class="sxs-lookup"><span data-stu-id="59bb9-108">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="59bb9-109">A tabela a seguir lista os recursos novos e alterados para esta versão do ISE do Windows PowerShell no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59bb9-109">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="59bb9-110">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="59bb9-110">IntelliSense</span></span>

> <span data-ttu-id="59bb9-111">Adicionado no ISE 3,0</span><span class="sxs-lookup"><span data-stu-id="59bb9-111">Added in ISE 3.0</span></span>

<span data-ttu-id="59bb9-112">O IntelliSense é um recurso de assistência de conclusão automática que faz parte do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59bb9-112">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="59bb9-113">O IntelliSense exibe menus clicáveis de cmdlets, parâmetros, valores de parâmetro, arquivos ou pastas potencialmente correspondentes conforme você digita.</span><span class="sxs-lookup"><span data-stu-id="59bb9-113">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="59bb9-114">**Que valor essa alteração adiciona?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-114">**What value does this change add?**</span></span>

<span data-ttu-id="59bb9-115">Com a adição do IntelliSense, é mais fácil descobrir cmdlets e sintaxe quando você usa ISE do Windows PowerShell para criar scripts.</span><span class="sxs-lookup"><span data-stu-id="59bb9-115">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="59bb9-116">Você também pode usar ISE do Windows PowerShell para aprender o Windows PowerShell enquanto cria novos scripts.</span><span class="sxs-lookup"><span data-stu-id="59bb9-116">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="59bb9-117">**O que funciona de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-117">**What works differently?**</span></span>

<span data-ttu-id="59bb9-118">Quando você digita cmdlets no ISE do Windows PowerShell, um menu rolável e clicável é exibido, permitindo que você procure e selecione os comandos apropriados.</span><span class="sxs-lookup"><span data-stu-id="59bb9-118">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="59bb9-119">Trechos</span><span class="sxs-lookup"><span data-stu-id="59bb9-119">Snippets</span></span>

> <span data-ttu-id="59bb9-120">Adicionado no ISE 3,0</span><span class="sxs-lookup"><span data-stu-id="59bb9-120">Added in ISE 3.0</span></span>

<span data-ttu-id="59bb9-121">Os *trechos* são seções curtas do código do Windows PowerShell que você pode inserir nos scripts criados no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59bb9-121">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="59bb9-122">ISE do Windows PowerShell vem com um conjunto padrão de trechos de código.</span><span class="sxs-lookup"><span data-stu-id="59bb9-122">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="59bb9-123">Você pode adicionar trechos de código usando `New-Snippet` o cmdlet enquanto trabalha no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59bb9-123">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="59bb9-124">**Que valor essa alteração adiciona?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-124">**What value does this change add?**</span></span>

<span data-ttu-id="59bb9-125">Usando trechos de código, você pode montar e criar scripts rapidamente para automatizar seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="59bb9-125">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="59bb9-126">**O que funciona de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-126">**What works differently?**</span></span>

<span data-ttu-id="59bb9-127">Para usar trechos de código no Windows PowerShell 3,0 ou posterior, no menu **Editar** , clique em **Iniciar trechos de código**ou pressione <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="59bb9-127">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="59bb9-128">Ferramentas complementares</span><span class="sxs-lookup"><span data-stu-id="59bb9-128">Add-on tools</span></span>

> <span data-ttu-id="59bb9-129">Adicionado no PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="59bb9-129">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59bb9-130">O ISE do Windows PowerShell agora dá suporte a ferramentas de complemento usando o modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="59bb9-130">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="59bb9-131">Esses Complementos são controles Windows Presentation Foundation (WPF) que são exibidos como um painel vertical ou horizontal no console do.</span><span class="sxs-lookup"><span data-stu-id="59bb9-131">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="59bb9-132">Várias ferramentas complementares em um painel são exibidas como um controle com guias.</span><span class="sxs-lookup"><span data-stu-id="59bb9-132">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="59bb9-133">Você também pode adicionar ou remover ferramentas complementares que são produzidas por partes que não são da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59bb9-133">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="59bb9-134">Para obter mais informações, consulte [a finalidade do modelo de objeto de script de ISE do Windows PowerShell](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span><span class="sxs-lookup"><span data-stu-id="59bb9-134">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="59bb9-135">**Que valor essa alteração adiciona?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-135">**What value does this change add?**</span></span>

<span data-ttu-id="59bb9-136">Os complementos permitem que você estenda e personalize ISE do Windows PowerShell com ferramentas que adicionam funcionalidade e aprimoram sua experiência de script.</span><span class="sxs-lookup"><span data-stu-id="59bb9-136">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="59bb9-137">**O que funciona de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-137">**What works differently?**</span></span>

<span data-ttu-id="59bb9-138">ISE do Windows PowerShell 3,0 e posteriores vêm com o complemento de **comandos** .</span><span class="sxs-lookup"><span data-stu-id="59bb9-138">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="59bb9-139">O complemento **comandos** permite que você procure cmdlets e acesse a ajuda dos cmdlets lado a lado com os painéis de **script** e de **console** .</span><span class="sxs-lookup"><span data-stu-id="59bb9-139">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="59bb9-140">Complementos adicionais podem ser encontrados usando o comando **abrir site de ferramentas complementares** no menu **Complementos** .</span><span class="sxs-lookup"><span data-stu-id="59bb9-140">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="59bb9-141">Gerenciador de reinicialização e salvamento automático</span><span class="sxs-lookup"><span data-stu-id="59bb9-141">Restart manager and auto-save</span></span>

> <span data-ttu-id="59bb9-142">Adicionado no PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="59bb9-142">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59bb9-143">ISE do Windows PowerShell agora salva automaticamente os scripts abertos a cada dois minutos, em um local separado.</span><span class="sxs-lookup"><span data-stu-id="59bb9-143">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="59bb9-144">Quando ISE do Windows PowerShell reinicia após uma falha inesperada ou uma reinicialização, ela recupera os scripts que estavam abertos na última sessão, mesmo que os scripts não tenham sido salvos.</span><span class="sxs-lookup"><span data-stu-id="59bb9-144">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="59bb9-145">Para alterar o intervalo de salvamento automático, execute o seguinte comando no painel de console `$psise.Options.AutoSaveMinuteInterval`:.</span><span class="sxs-lookup"><span data-stu-id="59bb9-145">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="59bb9-146">**Que valor essa alteração adiciona?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-146">**What value does this change add?**</span></span>

<span data-ttu-id="59bb9-147">Agora você pode trabalhar em ISE do Windows PowerShell sabendo que os scripts abertos são salvos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="59bb9-147">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="59bb9-148">**O que funciona de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-148">**What works differently?**</span></span>

<span data-ttu-id="59bb9-149">ISE do Windows PowerShell 2,0 não salva os scripts automaticamente.</span><span class="sxs-lookup"><span data-stu-id="59bb9-149">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="59bb9-150">Lista de usados mais recentemente</span><span class="sxs-lookup"><span data-stu-id="59bb9-150">Most-recently used list</span></span>

> <span data-ttu-id="59bb9-151">Adicionado no PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="59bb9-151">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59bb9-152">ISE do Windows PowerShell agora tem uma lista de arquivos usada mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="59bb9-152">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="59bb9-153">Quando você abre um arquivo em ISE do Windows PowerShell, o arquivo é adicionado à lista de usados mais recentemente no menu **arquivo** .</span><span class="sxs-lookup"><span data-stu-id="59bb9-153">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="59bb9-154">Para alterar o número padrão de arquivos na lista de usados mais recentemente, execute o seguinte comando no painel de console: `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="59bb9-154">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="59bb9-155">**Que valor essa alteração adiciona?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-155">**What value does this change add?**</span></span>

<span data-ttu-id="59bb9-156">Agora você pode usar a lista de usados mais recentemente para acessar facilmente os arquivos usados com frequência.</span><span class="sxs-lookup"><span data-stu-id="59bb9-156">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="59bb9-157">**O que funciona de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-157">**What works differently?**</span></span>

<span data-ttu-id="59bb9-158">ISE do Windows PowerShell 2,0 não tem uma lista de usados mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="59bb9-158">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="59bb9-159">Painel de console</span><span class="sxs-lookup"><span data-stu-id="59bb9-159">Console Pane</span></span>

> <span data-ttu-id="59bb9-160">Adicionado no PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="59bb9-160">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59bb9-161">Os painéis de comando e saída separados que estavam disponíveis na primeira versão do ISE do Windows PowerShell foram combinados em um único painel de console.</span><span class="sxs-lookup"><span data-stu-id="59bb9-161">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="59bb9-162">O painel de console é semelhante em função e aparência a um console típico do Windows PowerShell, mas inclui os seguintes aprimoramentos:</span><span class="sxs-lookup"><span data-stu-id="59bb9-162">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="59bb9-163">Cores de sintaxe para texto de entrada (não texto de saída), incluindo sintaxe XML</span><span class="sxs-lookup"><span data-stu-id="59bb9-163">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="59bb9-164">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="59bb9-164">IntelliSense</span></span>
- <span data-ttu-id="59bb9-165">Correspondência de chaves</span><span class="sxs-lookup"><span data-stu-id="59bb9-165">Brace matching</span></span>
- <span data-ttu-id="59bb9-166">Indicação de erro</span><span class="sxs-lookup"><span data-stu-id="59bb9-166">Error indication</span></span>
- <span data-ttu-id="59bb9-167">Suporte completo a Unicode</span><span class="sxs-lookup"><span data-stu-id="59bb9-167">Full Unicode support</span></span>
- <span data-ttu-id="59bb9-168">Ajuda sensível ao contexto <kbd>F1</kbd></span><span class="sxs-lookup"><span data-stu-id="59bb9-168"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="59bb9-169"><kbd></kbd>Ctrl+<kbd>F1</kbd> show-Command sensível ao contexto</span><span class="sxs-lookup"><span data-stu-id="59bb9-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="59bb9-170">Script complexo e suporte da direita para a esquerda</span><span class="sxs-lookup"><span data-stu-id="59bb9-170">Complex script and right-to-left support</span></span>
- <span data-ttu-id="59bb9-171">Suporte a fontes</span><span class="sxs-lookup"><span data-stu-id="59bb9-171">Font support</span></span>
- <span data-ttu-id="59bb9-172">Zoom</span><span class="sxs-lookup"><span data-stu-id="59bb9-172">Zoom</span></span>
- <span data-ttu-id="59bb9-173">Modos de seleção de linha e seleção de bloco</span><span class="sxs-lookup"><span data-stu-id="59bb9-173">Line-select and block-select modes</span></span>
- <span data-ttu-id="59bb9-174">Preservação do conteúdo digitado na linha de comando quando você pressiona a <kbd>seta</kbd> para exibir o histórico no console</span><span class="sxs-lookup"><span data-stu-id="59bb9-174">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="59bb9-175">**Que valor essa alteração adiciona?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-175">**What value does this change add?**</span></span>

<span data-ttu-id="59bb9-176">A adição dessas alterações do painel de console fornece uma experiência de script que é mais consistente com a interface do console.</span><span class="sxs-lookup"><span data-stu-id="59bb9-176">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="59bb9-177">**O que funciona de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-177">**What works differently?**</span></span>

<span data-ttu-id="59bb9-178">ISE do Windows PowerShell 2,0 tem painéis de comando e de saída separados.</span><span class="sxs-lookup"><span data-stu-id="59bb9-178">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="59bb9-179">Opções de linha de comando</span><span class="sxs-lookup"><span data-stu-id="59bb9-179">Command-line switches</span></span>

> <span data-ttu-id="59bb9-180">Adicionado no PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="59bb9-180">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59bb9-181">Se você iniciar ISE do Windows PowerShell na linha de comando (digitando **Powershell_ise. exe**), poderá adicionar as novas opções de linha de comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="59bb9-181">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="59bb9-182">`-NoProfile`: Inicia ISE do Windows PowerShell sem execução`$profile`</span><span class="sxs-lookup"><span data-stu-id="59bb9-182">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="59bb9-183">`-Help`: Exibe uma janela de ajuda</span><span class="sxs-lookup"><span data-stu-id="59bb9-183">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="59bb9-184">`-mta`: Inicia ISE do Windows PowerShell no modo Apartment multithread.</span><span class="sxs-lookup"><span data-stu-id="59bb9-184">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="59bb9-185">O modo de operação padrão para ISE do Windows PowerShell é o modo Apartment de thread único ou `-sta`.</span><span class="sxs-lookup"><span data-stu-id="59bb9-185">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="59bb9-186">**Que valor essa alteração adiciona?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-186">**What value does this change add?**</span></span>

<span data-ttu-id="59bb9-187">A adição dessas opções de linha de comando permite controlar o ambiente no qual o ISE do Windows PowerShell é executado.</span><span class="sxs-lookup"><span data-stu-id="59bb9-187">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="59bb9-188">**O que funciona de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-188">**What works differently?**</span></span>

<span data-ttu-id="59bb9-189">ISE do Windows PowerShell 2,0 não reconhece essas opções de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="59bb9-189">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="59bb9-190">Novos recursos do editor</span><span class="sxs-lookup"><span data-stu-id="59bb9-190">New editor features</span></span>

> <span data-ttu-id="59bb9-191">Adicionado no PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="59bb9-191">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59bb9-192">Outros recursos de edição de ISE do Windows PowerShell incluem:</span><span class="sxs-lookup"><span data-stu-id="59bb9-192">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="59bb9-193">**Cor de sintaxe XML** -ISE do Windows PowerShell agora tem a sintaxe XML colorida da mesma maneira que a sintaxe de cores de ti do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59bb9-193">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="59bb9-194">**Correspondência de chaves** -ISE do Windows PowerShell inclui correspondência de chaves e realce e pode ser usada das seguintes maneiras: (por exemplo, usar o comando **ir para correspondência** ou <kbd>Ctrl</kbd>+<kbd>]</kbd> localiza a chave de fechamento, se você ter uma chave de abertura selecionada).</span><span class="sxs-lookup"><span data-stu-id="59bb9-194">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="59bb9-195">**Modo de exibição da estrutura do código** O painel de script oferece suporte a estrutura de tópicos, que permite recolher ou expandir seções de código clicando em mais ou menos sinais na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="59bb9-195">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="59bb9-196">Você pode usar chaves ou as marcas `#region` e `#endregion` para marcar o início ou o fim de uma seção recolhível.</span><span class="sxs-lookup"><span data-stu-id="59bb9-196">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="59bb9-197">Para expandir ou recolher todas as regiões, pressione <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span><span class="sxs-lookup"><span data-stu-id="59bb9-197">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="59bb9-198">**Edição de texto arrastar e soltar** -ISE do Windows PowerShell agora dá suporte à edição de texto de arrastar e soltar.</span><span class="sxs-lookup"><span data-stu-id="59bb9-198">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="59bb9-199">Você pode selecionar qualquer bloco de texto e arrastar esse texto para outro local no editor ou no console do para mover o texto.</span><span class="sxs-lookup"><span data-stu-id="59bb9-199">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="59bb9-200">Se você mantiver pressionada a tecla <kbd>Ctrl</kbd> enquanto arrasta o texto selecionado, ao liberar o botão do mouse, o texto será copiado para o novo local.</span><span class="sxs-lookup"><span data-stu-id="59bb9-200">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="59bb9-201">Nesta versão do ISE do Windows PowerShell, quando você arrasta e solta arquivos em ISE do Windows PowerShell, ISE do Windows PowerShell abre o arquivo.</span><span class="sxs-lookup"><span data-stu-id="59bb9-201">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="59bb9-202">**Exibição de erro de análise** -os erros de análise são indicados com sublinhados vermelhos.</span><span class="sxs-lookup"><span data-stu-id="59bb9-202">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="59bb9-203">Quando você passa o mouse sobre um erro indicado, o texto da dica de ferramenta exibe o problema encontrado no código.</span><span class="sxs-lookup"><span data-stu-id="59bb9-203">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="59bb9-204">**Zoom** -o percentual de zoom do conteúdo do console pode ser definido usando o controle deslizante de zoom (no canto inferior direito da janela ISE do Windows PowerShell) ou inserindo o comando `$psise.options.Zoom` no painel de console.</span><span class="sxs-lookup"><span data-stu-id="59bb9-204">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="59bb9-205">**Cópias de Rich Text e** cópia de colagem na área de transferência em ISE do Windows PowerShell preserva a fonte, o tamanho e as informações de cor da seleção original.</span><span class="sxs-lookup"><span data-stu-id="59bb9-205">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="59bb9-206">**Seleção de bloco** – você pode selecionar um bloco de texto mantendo a tecla <kbd>ALT</kbd> pressionada enquanto seleciona o texto no painel de script com o mouse ou pressionando <kbd>ALT</kbd>+<kbd>Shift</kbd>+<kbd>seta</kbd>.</span><span class="sxs-lookup"><span data-stu-id="59bb9-206">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="59bb9-207">**Que valor essa alteração adiciona?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-207">**What value does this change add?**</span></span>

<span data-ttu-id="59bb9-208">Os recursos de edição adicionais fornecem um ambiente de edição mais consistente e eficiente.</span><span class="sxs-lookup"><span data-stu-id="59bb9-208">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="59bb9-209">**O que funciona de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-209">**What works differently?**</span></span>

<span data-ttu-id="59bb9-210">Esses aprimoramentos de edição não estavam presentes no ISE do Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="59bb9-210">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="59bb9-211">Janela do novo Visualizador da ajuda</span><span class="sxs-lookup"><span data-stu-id="59bb9-211">New Help viewer window</span></span>

> <span data-ttu-id="59bb9-212">Adicionado no PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="59bb9-212">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59bb9-213">Se você pressionar <kbd>F1</kbd> quando o cursor estiver em um cmdlet ou se parte de um cmdlet estiver realçada, o novo Visualizador da ajuda abrirá a ajuda contextual sobre o cmdlet realçado.</span><span class="sxs-lookup"><span data-stu-id="59bb9-213">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="59bb9-214">Para exibir **a ajuda do** Windows PowerShell, `operators` digite no painel de console e pressione <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="59bb9-214">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="59bb9-215">Antes de usar esse recurso, baixe a versão mais atual dos tópicos da ajuda do Windows PowerShell no site da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59bb9-215">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="59bb9-216">O método mais simples para baixar os tópicos da ajuda é executar o `Update-Help` cmdlet no painel de console ao executar ISE do Windows PowerShell como administrador.</span><span class="sxs-lookup"><span data-stu-id="59bb9-216">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="59bb9-217">Você pode alterar o local em que a tecla <kbd>F1</kbd> procura ajuda.</span><span class="sxs-lookup"><span data-stu-id="59bb9-217">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="59bb9-218">No menu**Opções** de **ferramentas**/, na guia **configurações gerais** , em **outras configurações**, você pode definir ou desmarcar a caixa de seleção **usar conteúdo de ajuda local em vez de conteúdo online**.</span><span class="sxs-lookup"><span data-stu-id="59bb9-218">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="59bb9-219">Quando marcada, o cliente procura a ajuda do cmdlet na ajuda baixada encontrada na pasta modules.</span><span class="sxs-lookup"><span data-stu-id="59bb9-219">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="59bb9-220">Se a caixa de seleção for desmarcada, o cliente procurará ajuda online.</span><span class="sxs-lookup"><span data-stu-id="59bb9-220">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="59bb9-221">**Que valor essa alteração adiciona?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-221">**What value does this change add?**</span></span>

<span data-ttu-id="59bb9-222">A ajuda contextual sem deixar seu cmdlet ou script atual fornece uma experiência de aprendizado integrada.</span><span class="sxs-lookup"><span data-stu-id="59bb9-222">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="59bb9-223">**O que funciona de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-223">**What works differently?**</span></span>

<span data-ttu-id="59bb9-224">Pressionar <kbd>F1</kbd> em versões anteriores do ISE do Windows PowerShell abriu o arquivo de ajuda no computador local.</span><span class="sxs-lookup"><span data-stu-id="59bb9-224">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="59bb9-225">No ISE do Windows PowerShell 3,0 e posterior, é aberta uma janela que contém a ajuda para o cmdlet que pode ser pesquisado e configurável.</span><span class="sxs-lookup"><span data-stu-id="59bb9-225">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="59bb9-226">Esta experiência de ajuda é nova para o ISE do Windows PowerShell 3,0, e a ajuda atualizável é nova para o Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="59bb9-226">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="59bb9-227">Cmdlet show-Command</span><span class="sxs-lookup"><span data-stu-id="59bb9-227">Show-Command cmdlet</span></span>

> <span data-ttu-id="59bb9-228">Adicionado no PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="59bb9-228">Added in PowerShell 3.0</span></span>

<span data-ttu-id="59bb9-229">O `Show-Command` cmdlet permite compor ou executar um cmdlet ou uma função preenchendo um formulário gráfico.</span><span class="sxs-lookup"><span data-stu-id="59bb9-229">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="59bb9-230">O formulário permite que os usuários trabalhem com o Windows PowerShell em um ambiente gráfico.</span><span class="sxs-lookup"><span data-stu-id="59bb9-230">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="59bb9-231">`Show-Command`também permite que os scripts avançados criem uma GUI rápida baseada no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59bb9-231">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="59bb9-232">**Que valor essa alteração adiciona?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-232">**What value does this change add?**</span></span>

<span data-ttu-id="59bb9-233">Usando `Show-Command` o em seus scripts do Windows PowerShell, você pode fornecer aos usuários o ambiente gráfico com o qual eles estão familiarizados.</span><span class="sxs-lookup"><span data-stu-id="59bb9-233">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="59bb9-234">`Show-Command`também pode ajudar os usuários introdutórios a aprender o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59bb9-234">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="59bb9-235">**O que funciona de maneira diferente?**</span><span class="sxs-lookup"><span data-stu-id="59bb9-235">**What works differently?**</span></span>

<span data-ttu-id="59bb9-236">`Show-Command`é novo ISE do Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="59bb9-236">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="59bb9-237">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59bb9-237">See also</span></span>

<span data-ttu-id="59bb9-238">Para obter mais informações sobre como usar ISE do Windows PowerShell, consulte [explorando o ambiente de script integrado do Windows PowerShell](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span><span class="sxs-lookup"><span data-stu-id="59bb9-238">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span></span>
