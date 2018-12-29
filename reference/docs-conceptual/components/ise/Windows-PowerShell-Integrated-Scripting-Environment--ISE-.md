---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Windows PowerShell Integrated Scripting Environment ISE
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: a5fcc8c813349d0b85cc3af29047424fe787d168
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404674"
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="4f0bc-103">Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="4f0bc-103">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="4f0bc-104">O Windows PowerShell Integrated Scripting Environment (ISE) é um dos dois anfitriões para o motor do Windows PowerShell e o idioma.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-104">The Windows PowerShell Integrated Scripting Environment (ISE) is one of two hosts for the Windows PowerShell engine and language.</span></span> <span data-ttu-id="4f0bc-105">Com o mesmo que pode escrever, executar e testar scripts de forma a que não está disponível na consola do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-105">With it you can write, run, and test scripts in ways that are not available in the Windows PowerShell Console.</span></span> <span data-ttu-id="4f0bc-106">O ISE adiciona sintaxe colorida, conclusão de tabulação, IntelliSense, depuração visual e ajuda contextual.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-106">The ISE adds syntax-coloring, tab completion, IntelliSense, visual debugging, and context sensitive Help.</span></span>

<span data-ttu-id="4f0bc-107">O ISE permite-lhe executar comandos num painel de consola, mas também dá suporte a painéis que pode utilizar para a visualização simultânea de código-fonte do seu script e outras ferramentas que podem se conectar o ISE.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-107">The ISE lets you run commands in a console pane, but it also supports panes that you can use to simultaneously view the source code of your script and other tools that can plug into the ISE.</span></span> <span data-ttu-id="4f0bc-108">Pode até mesmo abrir várias janelas de script ao mesmo tempo, o que é especialmente útil quando estiver depurando um script que utiliza funções definidas em outros scripts ou módulos.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-108">You can even open up multiple script windows at the same time, which is especially helpful when you are debugging a script that uses functions defined in other scripts or modules.</span></span>

## <a name="whats-new"></a><span data-ttu-id="4f0bc-109">What’s New (O que há de novo)</span><span class="sxs-lookup"><span data-stu-id="4f0bc-109">What’s New</span></span>

<span data-ttu-id="4f0bc-110">Aqui estão alguns dos recursos que foram adicionados ao ISE nas versões mais recentes do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-110">Here are some of the features that have been added to the ISE in the most recent releases of PowerShell.</span></span>

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a><span data-ttu-id="4f0bc-111">Adicionado no PowerShell 3.0 (Windows Server 2012, Windows 8)</span><span class="sxs-lookup"><span data-stu-id="4f0bc-111">Added in PowerShell 3.0 (Windows Server 2012, Windows 8)</span></span>

<span data-ttu-id="4f0bc-112">**IntelliSense** preenche automaticamente os seus comandos exibindo os menus de correspondente cmdlets, parâmetros, valores de parâmetros, ficheiros ou pastas à medida que escreve.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-112">**IntelliSense** automatically completes your commands by displaying menus of matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="4f0bc-113">**Trechos de código** são curtas seções do código que pode inserir facilmente para os scripts sua escrita.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-113">**Snippets** are short sections of code that you can easily insert into the scripts your write.</span></span> <span data-ttu-id="4f0bc-114">Uma coleção de trechos de código útil está incluída na caixa e, mais pode utilizando o **New-fragmento** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-114">A collection of useful snippets is included in the box and you can more by using the **New-Snippet** cmdlet.</span></span>

<span data-ttu-id="4f0bc-115">**Ferramentas de suplemento** que adiciona funcionalidades ao ISE do podem ser criadas ao escrever código que interage com [o Windows PowerShell ISE scripts modelo de objeto](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="4f0bc-115">**Add-on tools** that add features to the ISE can be created by writing code that interacts with [The Windows PowerShell ISE Scripting Object Model](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).</span></span>

<span data-ttu-id="4f0bc-116">Essas ferramentas podem exibir controles num painel com guias ou invisivelmente de trabalho em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-116">These tools can display controls in a tabbed pane or work invisibly in the background.</span></span> <span data-ttu-id="4f0bc-117">O **comandos** suplemento é um bom exemplo e está incluído na versão 3.0 e posterior que apresenta uma lista de comandos disponíveis e sua ajuda.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-117">The **Commands** add-on is a good example and is included with version 3.0 and later that displays a list of the available commands and their Help.</span></span>

<span data-ttu-id="4f0bc-118">**Gerenciador de reinicialização e salvamento automático** automaticamente salvar seus scripts a cada dois minutos para ajudar a evitar a perda do seu trabalho em caso de uma pane ou um reinício inesperado.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-118">**Restart Manager and Auto-save** automatically save your scripts every two minutes to help you avoid the loss of your work in the event of a crash or unexpected restart.</span></span>

<span data-ttu-id="4f0bc-119">**A maioria dos lista utilizados recentemente** faz agora parte do arquivo abrir menu para tornar mais fácil para os ficheiros que utiliza mais frequentemente.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-119">**Most Recently Used list** is now part of the File Open menu to make it easier to get to the files you use most often.</span></span>

<span data-ttu-id="4f0bc-120">**Painel de consola intercalado**.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-120">**Merged Console pane**.</span></span> <span data-ttu-id="4f0bc-121">Nas versões anteriores do ISE, havia painéis de comando e de saída separados.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-121">In previous versions of the ISE there were separate Command and Output panes.</span></span> <span data-ttu-id="4f0bc-122">Eles são agora combinados num único painel que mais diretamente imita o que vê na consola do Windows Powershell.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-122">They are now combined into a single pane that more directly mimics what you see in the Windows Powershell Console.</span></span>

<span data-ttu-id="4f0bc-123">**Opções da linha de comandos**.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-123">**Command-line switches**.</span></span> <span data-ttu-id="4f0bc-124">Vários comutadores da linha de comandos nova dão-lhe mais controlo sobre a forma como funciona o ISE.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-124">Several new command-line switches give you more control over the way the ISE works.</span></span> <span data-ttu-id="4f0bc-125">-NoProfile inicia o ISE sem executar um script de perfil.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-125">-NoProfile starts the ISE without running a profile script.</span></span> <span data-ttu-id="4f0bc-126">-Help abre uma janela de ajuda com o ISE.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-126">-Help opens up a help window with the ISE.</span></span> <span data-ttu-id="4f0bc-127">-mta inicia o ISE no "modo de multi-threaded apartment".</span><span class="sxs-lookup"><span data-stu-id="4f0bc-127">-mta starts the ISE in “multi-threaded apartment mode”.</span></span> <span data-ttu-id="4f0bc-128">A predefinição é o único thread.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-128">The default is single-threaded.</span></span>

<span data-ttu-id="4f0bc-129">**Novos recursos do editor** que seja mais fácil criar e ler o seu código:</span><span class="sxs-lookup"><span data-stu-id="4f0bc-129">**New editor features** make it easier to create and read your code:</span></span>

- <span data-ttu-id="4f0bc-130">**Cores de sintaxe XML**.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-130">**XML syntax coloring**.</span></span> <span data-ttu-id="4f0bc-131">O editor do ISE cores agora sintaxe XML da mesma forma como ele cores sintaxe de código do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-131">The ISE editor now colors XML syntax in the same way as it colors Windows PowerShell code syntax.</span></span>

- <span data-ttu-id="4f0bc-132">**Correspondência de chaves**.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-132">**Brace matching**.</span></span> <span data-ttu-id="4f0bc-133">O ISE do PowerShell ISEWindows destaca as chavetas correspondentes para o ajudar a garantir que tem o número certo de fechar as chavetas de acordo com sua abertura aqueles.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-133">The ISEWindows PowerShell ISE highlights matching braces to help you ensure you have the right number of closing braces to match your opening ones.</span></span> <span data-ttu-id="4f0bc-134">Use CTRL -\[ para localizar a chave de fechamento que corresponda a chave de abertura que se encontra o cursor.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-134">Use CTRL-\[ to locate the closing brace that matches the opening brace that the cursor is on.</span></span>

- <span data-ttu-id="4f0bc-135">**Descrever vista**.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-135">**Outline view**.</span></span> <span data-ttu-id="4f0bc-136">Pode fechar ou expandir as secções do seu código, ao clicar no sinal de adição e subtração sinais na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-136">You can collapse or expand sections of your code by clicking the plus and minus signs in the left margin.</span></span> <span data-ttu-id="4f0bc-137">Isto torna mais fácil encontrar o código que está procurando num script longo.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-137">This makes it easier to find the code you’re looking for in a long script.</span></span>

- <span data-ttu-id="4f0bc-138">**Arraste e largue a edição de texto**.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-138">**Drag and drop text editing**.</span></span> <span data-ttu-id="4f0bc-139">Pode selecionar um bloco de texto e arrastá-lo para outra localização para movê-la.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-139">You can select a block of text and drag it to another location to move it.</span></span> <span data-ttu-id="4f0bc-140">Se mantenha premida a tecla Ctrl enquanto arrasta o texto selecionado, que copiar, em vez de mover.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-140">If you hold down the Ctrl key while you drag the selected text you copy instead of move.</span></span>

- <span data-ttu-id="4f0bc-141">**Analisar a exibição de erro**.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-141">**Parse error display**.</span></span> <span data-ttu-id="4f0bc-142">Windows PowerShell examina o script, à medida que escreve.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-142">Windows PowerShell examines your script as you type.</span></span> <span data-ttu-id="4f0bc-143">Se detetar um erro, mostra um squiggle vermelho sob o código incorreto.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-143">If it detects an error, it shows a red squiggle under the offending code.</span></span> <span data-ttu-id="4f0bc-144">Quando focaliza o erro indicado, uma dica de ferramenta mostra-lhe o problema que foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-144">When you hover over the indicated error, a tooltip shows you the problem that was found.</span></span>

- <span data-ttu-id="4f0bc-145">**Zoom**.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-145">**Zoom**.</span></span> <span data-ttu-id="4f0bc-146">Pode ampliar seu texto para torná-lo mais fácil de ler ou aplicar o zoom para ver o quadro, utilizando o controlo de deslize no canto inferior direito da janela de ISE.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-146">You can zoom in on your text to make it easier to read or zoom out to see the bigger picture by using the slider in the bottom-right corner of the ISE window.</span></span>

- <span data-ttu-id="4f0bc-147">**Rich text copiar e colar**.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-147">**Rich text copy and paste**.</span></span> <span data-ttu-id="4f0bc-148">Quando copia do ISE para a área de transferência, o tipo de letra, tamanho e as informações de cor do texto selecionado está incluído.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-148">When you copy from the ISE to the clipboard, the font, size, and color information of the selected text is included.</span></span>

- <span data-ttu-id="4f0bc-149">**Bloquear a seleção**.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-149">**Block selection**.</span></span> <span data-ttu-id="4f0bc-150">Pode selecionar um segmento em forma de bloco de texto ao premir a tecla ALT ao selecionar o texto no painel de script com o rato ou ao premir **Alt + Shift + seta**.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-150">You can select a block-shaped chunk of text by holding down the ALT key while selecting text in the script pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a><span data-ttu-id="4f0bc-151">Adicionado no PowerShell 2.0 (Windows Server 2008 R2, Windows 7)</span><span class="sxs-lookup"><span data-stu-id="4f0bc-151">Added in PowerShell 2.0 (Windows Server 2008 R2, Windows 7)</span></span>

<span data-ttu-id="4f0bc-152">O ISE foi introduzido com o PowerShell v2.0.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-152">The ISE was introduced with PowerShell v2.0.</span></span>

## <a name="requirements-for-running-the-windows-powershell-ise"></a><span data-ttu-id="4f0bc-153">Requisitos para executar o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f0bc-153">Requirements for running the Windows PowerShell ISE</span></span>

<span data-ttu-id="4f0bc-154">O ISE encontra-se disponíveis em qualquer computador Windows que pode executar a versão do Windows PowerShell 2.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-154">The ISE is available on any Windows computer that can run Windows PowerShell v2.0 or later.</span></span> <span data-ttu-id="4f0bc-155">Cada versão do Windows e Windows Server inclui uma versão do Windows PowerShell e o ISE, mas pode atualizar para o mais recente disponível ao instalar o Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="4f0bc-155">Each version of Windows and Windows Server includes a version of Windows PowerShell and the ISE, but you can upgrade to the latest available by installing the Windows Management Framework (WMF).</span></span> <span data-ttu-id="4f0bc-156">Consulte a [WMF](/powershell/wmf) documentação para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-156">See the [WMF](/powershell/wmf) documentation for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="4f0bc-157">Como o ISE do Windows PowerShell exige uma interface gráfica do usuário, não é possível executá-lo a opção Server Core do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="4f0bc-157">Because Windows PowerShell ISE requires a graphical user interface, you can’t run it on the Server Core option of Windows Server.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f0bc-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f0bc-158">See also</span></span>

[<span data-ttu-id="4f0bc-159">Objetivo do windows power shell do ise do modelo de objeto de script</span><span class="sxs-lookup"><span data-stu-id="4f0bc-159">Purpose of the windows power shell ise scripting object model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)