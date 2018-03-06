---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Obter informações de ajuda detalhada"
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: c786ce089073abccdf186dc1d9e8ee383f83655d
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/31/2017
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="429e7-103">Obter informações de ajuda detalhada</span><span class="sxs-lookup"><span data-stu-id="429e7-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="429e7-104">O Windows PowerShell inclui tópicos de ajuda detalhada que explicam conceitos do Windows PowerShell e o idioma do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="429e7-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="429e7-105">Também existem tópicos de ajuda para cada fornecedor e o cmdlet e tópicos de ajuda para muitas funções e scripts.</span><span class="sxs-lookup"><span data-stu-id="429e7-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="429e7-106">Pode apresentar estes tópicos de ajuda na linha de comandos ou visualizar as versões mais recentemente atualizadas destes tópicos em do Microsoft TechNet Library.</span><span class="sxs-lookup"><span data-stu-id="429e7-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="429e7-107">Muitos programas que alojam o Windows PowerShell, como o Windows PowerShell Integrated Scripting ambiente, fornecem funcionalidades adicionais de ajuda, tais como ajuda sensível ao contexto e compilar o ficheiro de ajuda (.chm).</span><span class="sxs-lookup"><span data-stu-id="429e7-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="429e7-108">Obter ajuda para Cmdlets</span><span class="sxs-lookup"><span data-stu-id="429e7-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="429e7-109">Para obter ajuda sobre cmdlets do Windows PowerShell, utilize o [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="429e7-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="429e7-110">Por exemplo, para obter ajuda para o [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, tipo:</span><span class="sxs-lookup"><span data-stu-id="429e7-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="429e7-111">ou</span><span class="sxs-lookup"><span data-stu-id="429e7-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="429e7-112">Ainda pode obter ajuda sobre o cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="429e7-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="429e7-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="429e7-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="429e7-114">Para obter uma lista de todos os tópicos de ajuda do cmdlet na sua sessão, escreva:</span><span class="sxs-lookup"><span data-stu-id="429e7-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="429e7-115">Para apresentar uma página de cada tópico de ajuda num momento, utilize o **ajudar** função ou o seu alias **man**.</span><span class="sxs-lookup"><span data-stu-id="429e7-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="429e7-116">Por exemplo, para apresentar a ajuda do cmdlet Get-ChildItem, escreva</span><span class="sxs-lookup"><span data-stu-id="429e7-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="429e7-117">ou</span><span class="sxs-lookup"><span data-stu-id="429e7-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="429e7-118">Para ver informações detalhadas sobre um cmdlet, a função ou script, incluindo as descrições dos respetivos parâmetros e exemplos da sua utilização, utilize o *detalhados* parâmetros do cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="429e7-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="429e7-119">Por exemplo, para obter informações detalhadas sobre o cmdlet Get-ChildItem, escreva:</span><span class="sxs-lookup"><span data-stu-id="429e7-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="429e7-120">Para apresentar todo o conteúdo no tópico de ajuda, utilize o *completa* parâmetros do cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="429e7-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="429e7-121">Por exemplo, para apresentar todo o conteúdo no tópico de ajuda do cmdlet Get-ChildItem, escreva:</span><span class="sxs-lookup"><span data-stu-id="429e7-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="429e7-122">Para obter ajuda de detalhado sobre os parâmetros de um cmdlet, utilize o *parâmetro* parâmetros do cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="429e7-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="429e7-123">Por exemplo obter ajuda para todos os parâmetros do cmdlet Get-ChildItem, tipo de detalhado:</span><span class="sxs-lookup"><span data-stu-id="429e7-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="429e7-124">Para apresentar apenas os exemplos de um tópico de ajuda, utilize o *exemplo* parâmetro de Get-Help.</span><span class="sxs-lookup"><span data-stu-id="429e7-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="429e7-125">Por exemplo, para apresentar apenas os exemplos de tópico de ajuda para o cmdlet Get-ChildItem, escreva:</span><span class="sxs-lookup"><span data-stu-id="429e7-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="429e7-126">Para obter informações sobre como escrever tópicos de ajuda para os cmdlets que escreve, consulte [como escrever ajuda do Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) na biblioteca da MSDN.</span><span class="sxs-lookup"><span data-stu-id="429e7-126">For information about how to write Help topics for the cmdlets that you write, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="429e7-127">Obter Ajuda Conceptual</span><span class="sxs-lookup"><span data-stu-id="429e7-127">Getting Conceptual Help</span></span>
<span data-ttu-id="429e7-128">O cmdlet Get-Help também apresenta informações sobre tópicos conceptuais no Windows PowerShell, incluindo tópicos sobre o idioma do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="429e7-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="429e7-129">Tópicos de ajuda conceptuais começar com o prefixo "about_", tais como about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="429e7-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="429e7-130">(O tópico conceptual deve ser introduzido o nome em inglês, mesmo em versões não inglesas do Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="429e7-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="429e7-131">Para apresentar uma lista de tópicos conceptuais, escreva:</span><span class="sxs-lookup"><span data-stu-id="429e7-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="429e7-132">Para apresentar um determinado tópico de ajuda, escreva o nome de tópico, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="429e7-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="429e7-133">Os parâmetros de Get-Help, tais como *detalhados*, *parâmetro*, e *exemplos*, não tem qualquer efeito no ecrã de conceptual tópicos de ajuda.</span><span class="sxs-lookup"><span data-stu-id="429e7-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="429e7-134">Obter ajuda sobre fornecedores</span><span class="sxs-lookup"><span data-stu-id="429e7-134">Getting Help About Providers</span></span>
<span data-ttu-id="429e7-135">O cmdlet Get-Help apresenta informações sobre fornecedores do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="429e7-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="429e7-136">Para obter ajuda para um fornecedor, escreva "Get-Help" seguido do nome do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="429e7-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="429e7-137">Por exemplo, para obter ajuda para o fornecedor de registo, escreva:</span><span class="sxs-lookup"><span data-stu-id="429e7-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="429e7-138">Para obter uma lista de todos os tópicos de ajuda de fornecedor na sua sessão, escreva</span><span class="sxs-lookup"><span data-stu-id="429e7-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="429e7-139">Os parâmetros de Get-Help, tais como *detalhados*, *parâmetro*, e *exemplos*, não tem qualquer efeito no ecrã dos tópicos de ajuda do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="429e7-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="429e7-140">Obter ajuda sobre Scripts e funções</span><span class="sxs-lookup"><span data-stu-id="429e7-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="429e7-141">Tópicos de ajuda de ter muitos scripts e funções no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="429e7-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="429e7-142">Utilize o cmdlet Get-Help para apresentar os tópicos de ajuda para scripts e funções.</span><span class="sxs-lookup"><span data-stu-id="429e7-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="429e7-143">Para apresentar a ajuda para uma função, escreva "get-help" seguido do nome de função.</span><span class="sxs-lookup"><span data-stu-id="429e7-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="429e7-144">Por exemplo, para obter ajuda para a função de Disable-PSRemoting, escreva:</span><span class="sxs-lookup"><span data-stu-id="429e7-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="429e7-145">Para apresentar a ajuda para um script, escreva o caminho completamente qualificado para o ficheiro de script.</span><span class="sxs-lookup"><span data-stu-id="429e7-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="429e7-146">Se o script estiver num caminho listado na variável de ambiente Path, pode omitir o caminho do comando.</span><span class="sxs-lookup"><span data-stu-id="429e7-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="429e7-147">Por exemplo, se tiver um script designado "TestScript.ps1" no seu c\\diretório de teste de PS, para visualizar o tópico de ajuda para o script, tipo:</span><span class="sxs-lookup"><span data-stu-id="429e7-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="429e7-148">Os parâmetros que foram concebidos para apresentar cmdlet ajudam, tais como *detalhados*, *completa*, *exemplos*, e *parâmetro*, funcionam para as funções e scripts ajuda ajudam, demasiado.</span><span class="sxs-lookup"><span data-stu-id="429e7-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="429e7-149">No entanto, quando apresentar todos os ajuda, escrevendo "get-help \*", a ajuda para as funções e scripts não é apresentada.</span><span class="sxs-lookup"><span data-stu-id="429e7-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="429e7-150">Para obter informações sobre como escrever tópicos de ajuda para as suas funções e scripts, consulte [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), e [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span><span class="sxs-lookup"><span data-stu-id="429e7-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="429e7-151">Obter Ajuda Online</span><span class="sxs-lookup"><span data-stu-id="429e7-151">Getting Help Online</span></span>
<span data-ttu-id="429e7-152">Se estiver ligado à Internet, uma das formas melhor para obter ajuda é ver tópicos de ajuda online.</span><span class="sxs-lookup"><span data-stu-id="429e7-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="429e7-153">Porque tópicos online são fáceis de atualização, é provável que forneça o conteúdo mais recente.</span><span class="sxs-lookup"><span data-stu-id="429e7-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="429e7-154">Para obter ajuda online, experimente o *Online* parâmetros do cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="429e7-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="429e7-155">O *Online* parâmetro funciona de cmdlet Get-Help apenas para o cmdlet ajuda, funcionar ajuda e ajuda o script.</span><span class="sxs-lookup"><span data-stu-id="429e7-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="429e7-156">Não é possível utilizar o *Online* parâmetro com conceptual (sobre) ou tópicos de ajuda do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="429e7-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="429e7-157">Além disso, porque esta funcionalidade é opcional, não funciona para cada cmdlet, a função ou o tópico de ajuda de script.</span><span class="sxs-lookup"><span data-stu-id="429e7-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="429e7-158">No entanto, todos os tópicos de ajuda que vêm com o Windows PowerShell, incluindo o fornecedor de ajuda e conceptual (tópicos de ajuda sobre) estão disponíveis online no [do Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) secção do Microsoft TechNet Library.</span><span class="sxs-lookup"><span data-stu-id="429e7-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="429e7-159">Para utilizar o *Online* parâmetros do cmdlet Get-Help, utilize o seguinte formato de comando.</span><span class="sxs-lookup"><span data-stu-id="429e7-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="429e7-160">Por exemplo, para obter a versão online do tópico de ajuda sobre o cmdlet Get-ChildItem, escreva:</span><span class="sxs-lookup"><span data-stu-id="429e7-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="429e7-161">Se estiver disponível uma versão online do tópico de ajuda, será aberto no seu browser predefinido.</span><span class="sxs-lookup"><span data-stu-id="429e7-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="429e7-162">Se a ajuda online é suportada para um tópico de ajuda, também pode ver o endereço de Internet (URL) do tópico de ajuda.</span><span class="sxs-lookup"><span data-stu-id="429e7-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="429e7-163">O endereço Internet é apresentada na secção ligações relacionadas um tópico de ajuda.</span><span class="sxs-lookup"><span data-stu-id="429e7-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="429e7-164">Por exemplo, para ver o URL para a versão online do cmdlet Add-Computer, escreva:</span><span class="sxs-lookup"><span data-stu-id="429e7-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="429e7-165">A primeira linha na secção do tópico ligações relacionadas é mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="429e7-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="429e7-166">Para obter informações sobre como fornecer suporte online para os tópicos de ajuda, consulte [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)e ver [como escrever ajuda do Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) na biblioteca da MSDN.</span><span class="sxs-lookup"><span data-stu-id="429e7-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="429e7-167">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="429e7-167">See Also</span></span>
- <span data-ttu-id="429e7-168">[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)</span><span class="sxs-lookup"><span data-stu-id="429e7-168">[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)</span></span>
- [<span data-ttu-id="429e7-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="429e7-169">about_Scripts</span></span>](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="429e7-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="429e7-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- <span data-ttu-id="429e7-171">[Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span><span class="sxs-lookup"><span data-stu-id="429e7-171">[Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span></span>

