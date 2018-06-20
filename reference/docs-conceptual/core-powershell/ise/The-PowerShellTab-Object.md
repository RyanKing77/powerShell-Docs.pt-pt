---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: c10f9106e31bb05828f1e76554ebe40ddb778340
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952516"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="c7dec-103">Objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="c7dec-103">The PowerShellTab Object</span></span>

<span data-ttu-id="c7dec-104">O **PowerShellTab** objeto representa um ambiente de tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7dec-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="c7dec-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c7dec-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="c7dec-106">Invocar\( Script \)</span><span class="sxs-lookup"><span data-stu-id="c7dec-106">Invoke\( Script \)</span></span>

<span data-ttu-id="c7dec-107">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c7dec-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c7dec-108">Executa o script especificado no separador do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7dec-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="c7dec-109">Este método só funciona nos outros separadores de PowerShell, não o separador de PowerShell partir da qual é executado.</span><span class="sxs-lookup"><span data-stu-id="c7dec-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="c7dec-110">Não devolver qualquer objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="c7dec-110">It does not return any object or value.</span></span> <span data-ttu-id="c7dec-111">Se o código modifica qualquer variável, em seguida, essas alterações sejam mantidas no separador relativamente ao qual o comando foi invocado.</span><span class="sxs-lookup"><span data-stu-id="c7dec-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="c7dec-112">**Script** -System.Management.Automation.ScriptBlock ou cadeia o bloco de script para executar.</span><span class="sxs-lookup"><span data-stu-id="c7dec-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="c7dec-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="c7dec-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="c7dec-114">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="c7dec-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c7dec-115">Executa o script especificado no separador do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7dec-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="c7dec-116">Este método só funciona nos outros separadores de PowerShell, não o separador de PowerShell partir da qual é executado.</span><span class="sxs-lookup"><span data-stu-id="c7dec-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="c7dec-117">O bloco de script é executado e qualquer valor que é devolvido a partir do script é devolvido ao ambiente de execução a partir do qual é invocado o comando.</span><span class="sxs-lookup"><span data-stu-id="c7dec-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="c7dec-118">Se o comando demora mais tempo a executar que o **millesecondsTimeout** valor Especifica, em seguida, o comando falha com uma exceção: "a operação foi excedido."</span><span class="sxs-lookup"><span data-stu-id="c7dec-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="c7dec-119">**Script** -System.Management.Automation.ScriptBlock ou cadeia o bloco de script para executar.</span><span class="sxs-lookup"><span data-stu-id="c7dec-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="c7dec-120">**\[useNewScope\]**  -opcional booleano que assume a predefinição **$true** se definido como **$true**, em seguida, é criado um novo âmbito no qual executar o comando.</span><span class="sxs-lookup"><span data-stu-id="c7dec-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true** If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="c7dec-121">Não modifica o ambiente de tempo de execução do separador do PowerShell que é especificado pelo comando.</span><span class="sxs-lookup"><span data-stu-id="c7dec-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="c7dec-122">**\[millisecondsTimeout\]**  -opcional número inteiro que assume a predefinição **500**.</span><span class="sxs-lookup"><span data-stu-id="c7dec-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="c7dec-123">Se o comando não for concluída dentro do período de tempo especificado, em seguida, o comando gera um **TimeoutException** com a mensagem "a operação foi excedido."</span><span class="sxs-lookup"><span data-stu-id="c7dec-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a><span data-ttu-id="c7dec-124">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c7dec-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="c7dec-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="c7dec-125">AddOnsMenu</span></span>

<span data-ttu-id="c7dec-126">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c7dec-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c7dec-127">A propriedade só de leitura que obtém o menu de suplementos para o separador do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7dec-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a><span data-ttu-id="c7dec-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="c7dec-128">CanInvoke</span></span>

<span data-ttu-id="c7dec-129">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c7dec-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c7dec-130">A propriedade booleana só de leitura que devolva uma **$true** valor se um script pode ser invocado com o [Invoke (Script)](#invoke-script-) método.</span><span class="sxs-lookup"><span data-stu-id="c7dec-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a><span data-ttu-id="c7dec-131">Consolepane</span><span class="sxs-lookup"><span data-stu-id="c7dec-131">Consolepane</span></span>

<span data-ttu-id="c7dec-132">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="c7dec-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="c7dec-133">No Windows PowerShell ISE 2.0 Isto foi atribuído o nome **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="c7dec-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="c7dec-134">A propriedade só de leitura que obtém o painel de consola [editor](../ise/The-ISEEditor-Object.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="c7dec-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="c7dec-135">NomeaApresentar</span><span class="sxs-lookup"><span data-stu-id="c7dec-135">DisplayName</span></span>

<span data-ttu-id="c7dec-136">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c7dec-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c7dec-137">A propriedade de leitura e escrita que obtém ou define o texto que é apresentado no separador do PowerShell. Por predefinição, os separadores são denominados "PowerShell #", onde o n. º representa um número.</span><span class="sxs-lookup"><span data-stu-id="c7dec-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="c7dec-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="c7dec-138">ExpandedScript</span></span>

<span data-ttu-id="c7dec-139">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c7dec-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c7dec-140">A leitura e escrita propriedade booleana que determina se o painel de Script está expandido ou oculto.</span><span class="sxs-lookup"><span data-stu-id="c7dec-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="c7dec-141">Ficheiros</span><span class="sxs-lookup"><span data-stu-id="c7dec-141">Files</span></span>

<span data-ttu-id="c7dec-142">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c7dec-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c7dec-143">A propriedade só de leitura que obtém a [recolha de ficheiros de script](../ise/The-ISEFileCollection-Object.md) que estão abertos no separador do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7dec-143">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="c7dec-144">Saída</span><span class="sxs-lookup"><span data-stu-id="c7dec-144">Output</span></span>

<span data-ttu-id="c7dec-145">Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.</span><span class="sxs-lookup"><span data-stu-id="c7dec-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="c7dec-146">Em versões posteriores do ISE do Windows PowerShell, pode utilizar o **ConsolePane** objetos para os mesmos efeitos.</span><span class="sxs-lookup"><span data-stu-id="c7dec-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="c7dec-147">A propriedade só de leitura que obtém o painel de resultados de atual [editor](../ise/The-ISEEditor-Object.md).</span><span class="sxs-lookup"><span data-stu-id="c7dec-147">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="c7dec-148">Linha de comandos</span><span class="sxs-lookup"><span data-stu-id="c7dec-148">Prompt</span></span>

<span data-ttu-id="c7dec-149">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c7dec-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c7dec-150">A propriedade só de leitura que obtém o texto da linha de comandos atual.</span><span class="sxs-lookup"><span data-stu-id="c7dec-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="c7dec-151">Nota: o **Prompt** função pode ser substituída pelo utilizador '™ perfil s.</span><span class="sxs-lookup"><span data-stu-id="c7dec-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="c7dec-152">Se o resultado é que não seja uma cadeia simple, em seguida, esta propriedade devolve nada.</span><span class="sxs-lookup"><span data-stu-id="c7dec-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="c7dec-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="c7dec-153">ShowCommands</span></span>

<span data-ttu-id="c7dec-154">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="c7dec-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c7dec-155">A propriedade de leitura e escrita que indica se o painel de comandos é atualmente apresentado.</span><span class="sxs-lookup"><span data-stu-id="c7dec-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="c7dec-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="c7dec-156">StatusText</span></span>

<span data-ttu-id="c7dec-157">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c7dec-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c7dec-158">A propriedade só de leitura que obtém a **PowerShellTab** texto de estado.</span><span class="sxs-lookup"><span data-stu-id="c7dec-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="c7dec-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="c7dec-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="c7dec-160">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="c7dec-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c7dec-161">A propriedade só de leitura que indica se o painel de ferramentas de suplementos horizontal está atualmente aberto.</span><span class="sxs-lookup"><span data-stu-id="c7dec-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="c7dec-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="c7dec-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="c7dec-163">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="c7dec-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c7dec-164">A propriedade só de leitura que indica se o painel de ferramentas de suplementos vertical está atualmente aberto.</span><span class="sxs-lookup"><span data-stu-id="c7dec-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="c7dec-165">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c7dec-165">See Also</span></span>

- [<span data-ttu-id="c7dec-166">O objeto de PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="c7dec-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="c7dec-167">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="c7dec-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c7dec-168">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="c7dec-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)