---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Obter Informações de Ajuda Detalhadas
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: e58814f512aa2c5914f92f942cf2a4a76956ee20
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794574"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="4f479-103">Obter informações de ajuda detalhadas</span><span class="sxs-lookup"><span data-stu-id="4f479-103">Getting detailed help information</span></span>

<span data-ttu-id="4f479-104">PowerShell inclui artigos de ajuda detalhados que explicam conceitos do PowerShell e a linguagem do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f479-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="4f479-105">Também existem artigos de ajuda para cada cmdlet e o fornecedor e para muitas funções e scripts.</span><span class="sxs-lookup"><span data-stu-id="4f479-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="4f479-106">Pode exibir esses artigos de ajuda no prompt de comando ou vista atualizada mais recentemente versões dos seguintes artigos no [PowerShell](/powershell/scripting/overview) documentação online.</span><span class="sxs-lookup"><span data-stu-id="4f479-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="4f479-107">Obter ajuda para cmdlets</span><span class="sxs-lookup"><span data-stu-id="4f479-107">Getting help for cmdlets</span></span>

<span data-ttu-id="4f479-108">Para obter ajuda sobre cmdlets do PowerShell, utilize o [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f479-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="4f479-109">Por exemplo, para obter ajuda para o `Get-ChildItem` cmdlet, tipo:</span><span class="sxs-lookup"><span data-stu-id="4f479-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="4f479-110">ou</span><span class="sxs-lookup"><span data-stu-id="4f479-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="4f479-111">Pode até mesmo obter ajuda sobre o cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="4f479-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="4f479-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4f479-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="4f479-113">Para obter uma lista de todos os o cmdlet artigos de ajuda na sua sessão, escreva:</span><span class="sxs-lookup"><span data-stu-id="4f479-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="4f479-114">Para apresentar uma página de cada artigo de ajuda ao mesmo tempo, utilize o `help` função ou o respetivo alias `man`.</span><span class="sxs-lookup"><span data-stu-id="4f479-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="4f479-115">Por exemplo, para apresentar a ajuda para o `Get-ChildItem` cmdlet, tipo</span><span class="sxs-lookup"><span data-stu-id="4f479-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="4f479-116">ou</span><span class="sxs-lookup"><span data-stu-id="4f479-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="4f479-117">Para visualizar informações detalhadas, utilizar o **Detailed** parâmetro do `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f479-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="4f479-118">Por exemplo, para obter informações detalhadas o `Get-ChildItem` cmdlet, tipo:</span><span class="sxs-lookup"><span data-stu-id="4f479-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="4f479-119">Para exibir todo o conteúdo do artigo de ajuda, utilize o **completo** parâmetro do `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f479-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="4f479-120">Por exemplo, para exibir todo o conteúdo do artigo de ajuda para o `Get-ChildItem` cmdlet, tipo:</span><span class="sxs-lookup"><span data-stu-id="4f479-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="4f479-121">Para obter detalhadas ajuda sobre os parâmetros de um cmdlet, utilize o **parâmetro** parâmetro do `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f479-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="4f479-122">Por exemplo obter detalhadas ajuda para todos os parâmetros do `Get-ChildItem` cmdlet, tipo:</span><span class="sxs-lookup"><span data-stu-id="4f479-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="4f479-123">Para apresentar apenas os exemplos num artigo de ajuda, utilize o **exemplos** parâmetro do `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="4f479-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="4f479-124">Por exemplo, para apresentar apenas os exemplos neste artigo de ajuda para o `Get-ChildItem` cmdlet, tipo:</span><span class="sxs-lookup"><span data-stu-id="4f479-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="4f479-125">Para obter informações sobre como escrever artigos de ajuda para os cmdlets que escreva, consulte [como escrever ajuda do Cmdlet](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="4f479-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="4f479-126">Obter ajuda conceitual</span><span class="sxs-lookup"><span data-stu-id="4f479-126">Getting conceptual help</span></span>

<span data-ttu-id="4f479-127">O `Get-Help` cmdlet também apresenta informações sobre artigos conceptuais no PowerShell, inclusive artigos sobre a linguagem do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f479-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="4f479-128">Ajuda conceitual artigos começam com o prefixo "about_", como about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="4f479-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="4f479-129">(O nome do artigo conceitual deve ser inserido em inglês mesmo em versões não inglesas do PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="4f479-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="4f479-130">Para apresentar uma lista de artigos conceptuais, escreva:</span><span class="sxs-lookup"><span data-stu-id="4f479-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="4f479-131">Para apresentar um determinado artigo de ajuda, escreva o nome de artigo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4f479-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="4f479-132">Os parâmetros da `Get-Help`, tal como **Detailed**, **parâmetro**, e **exemplos**, não têm efeito na exibição de artigos de ajuda conceituais.</span><span class="sxs-lookup"><span data-stu-id="4f479-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="4f479-133">Obter ajuda sobre os fornecedores</span><span class="sxs-lookup"><span data-stu-id="4f479-133">Getting help about providers</span></span>

<span data-ttu-id="4f479-134">O `Get-Help` cmdlet apresenta informações sobre fornecedores do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f479-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="4f479-135">Para obter ajuda para um fornecedor, escreva `Get-Help` seguido pelo nome do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="4f479-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="4f479-136">Por exemplo, para obter ajuda para o fornecedor de registo, escreva:</span><span class="sxs-lookup"><span data-stu-id="4f479-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="4f479-137">Para obter uma lista de todos os fornecedor de artigos de ajuda na sua sessão, escreva</span><span class="sxs-lookup"><span data-stu-id="4f479-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="4f479-138">Os parâmetros da `Get-Help`, tal como **Detailed**, **parâmetro**, e **exemplos**, não têm efeito na exibição de artigos de ajuda do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="4f479-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="4f479-139">Obter ajuda sobre scripts e funções</span><span class="sxs-lookup"><span data-stu-id="4f479-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="4f479-140">Muitos scripts e funções do PowerShell têm artigos de ajuda.</span><span class="sxs-lookup"><span data-stu-id="4f479-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="4f479-141">Utilize o `Get-Help` cmdlet para ver os artigos de ajuda para scripts e funções.</span><span class="sxs-lookup"><span data-stu-id="4f479-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="4f479-142">Para apresentar a ajuda para uma função, escreva `Get-Help` seguido do nome de função.</span><span class="sxs-lookup"><span data-stu-id="4f479-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="4f479-143">Por exemplo, para obter ajuda para o `Disable-PSRemoting` de função, escreva:</span><span class="sxs-lookup"><span data-stu-id="4f479-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="4f479-144">Para apresentar a ajuda para obter um script, escreva o caminho para o ficheiro de script.</span><span class="sxs-lookup"><span data-stu-id="4f479-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="4f479-145">Se o script não estiver num caminho listado na variável de ambiente Path, tem de utilizar o caminho totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="4f479-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="4f479-146">Por exemplo, se tiver um script chamado "TestScript.ps1" na sua unidade c:\\directory PS e teste, para exibir o artigo de ajuda para o script, tipo:</span><span class="sxs-lookup"><span data-stu-id="4f479-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="4f479-147">Os parâmetros que foram concebidos para exibir o trabalho de ajuda do cmdlet para o script e a função, também ajudam.</span><span class="sxs-lookup"><span data-stu-id="4f479-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="4f479-148">No entanto, a ajuda para funções e scripts não é apresentada quando executa `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="4f479-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="4f479-149">Para obter informações sobre como escrever artigos de ajuda para seus scripts e funções, consulte os artigos seguintes:</span><span class="sxs-lookup"><span data-stu-id="4f479-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="4f479-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="4f479-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="4f479-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="4f479-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="4f479-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="4f479-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="4f479-153">Obter ajuda online</span><span class="sxs-lookup"><span data-stu-id="4f479-153">Getting help online</span></span>

<span data-ttu-id="4f479-154">Visualizar os artigos de ajuda online é uma das melhores formas de obter ajuda.</span><span class="sxs-lookup"><span data-stu-id="4f479-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="4f479-155">Artigos online são mais fáceis de atualizar e fornecer o conteúdo mais recente.</span><span class="sxs-lookup"><span data-stu-id="4f479-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="4f479-156">Para obter ajuda online, utilize o **Online** parâmetro do `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f479-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="4f479-157">Todos os artigos de ajuda que vêm com o PowerShell, incluindo o fornecedor de ajuda e conceitual (sobre), artigos de ajuda, estão disponíveis online na [PowerShell](/powershell/scripting/powershell-scripting) documentação.</span><span class="sxs-lookup"><span data-stu-id="4f479-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="4f479-158">Não é possível utilizar o **Online** parâmetro com conceitual (about_\*) ou artigos de ajuda do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="4f479-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="4f479-159">Ajuda online é opcional, para que ele não funciona para cada cmdlet, função ou script.</span><span class="sxs-lookup"><span data-stu-id="4f479-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="4f479-160">Por exemplo, para obter a versão online do artigo de ajuda o `Get-ChildItem` cmdlet, tipo:</span><span class="sxs-lookup"><span data-stu-id="4f479-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="4f479-161">PowerShell abre o artigo no seu browser predefinido.</span><span class="sxs-lookup"><span data-stu-id="4f479-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="4f479-162">Se a ajuda online é suportada para um artigo de ajuda, também pode ver o URL do artigo de ajuda.</span><span class="sxs-lookup"><span data-stu-id="4f479-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="4f479-163">O URL é apresentado na seção Links relacionados de um artigo de ajuda.</span><span class="sxs-lookup"><span data-stu-id="4f479-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="4f479-164">Por exemplo, para ver o URL para a versão online do cmdlet Add-Computer, escreva:</span><span class="sxs-lookup"><span data-stu-id="4f479-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="4f479-165">A primeira linha na seção Links relacionados do artigo é mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="4f479-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="4f479-166">Para obter informações sobre como fornecer suporte online para seus artigos de ajuda, consulte [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="4f479-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="4f479-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f479-167">See also</span></span>

- [<span data-ttu-id="4f479-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="4f479-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="4f479-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="4f479-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="4f479-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="4f479-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="4f479-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="4f479-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
