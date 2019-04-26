---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEEditor
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086770"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="7ecee-103">Objeto ISEEditor</span><span class="sxs-lookup"><span data-stu-id="7ecee-103">The ISEEditor Object</span></span>

<span data-ttu-id="7ecee-104">Uma **ISEEditor** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="7ecee-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="7ecee-105">O painel de consola é um **ISEEditor** objeto.</span><span class="sxs-lookup"><span data-stu-id="7ecee-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="7ecee-106">Cada [ISEFile](The-ISEFile-Object.md) -se associado ao objeto **ISEEditor** objeto.</span><span class="sxs-lookup"><span data-stu-id="7ecee-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="7ecee-107">As secções seguintes listam os métodos e propriedades de um **ISEEditor** objeto.</span><span class="sxs-lookup"><span data-stu-id="7ecee-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="7ecee-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="7ecee-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="7ecee-109">Limpar\(\)</span><span class="sxs-lookup"><span data-stu-id="7ecee-109">Clear\(\)</span></span>

<span data-ttu-id="7ecee-110">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-111">Limpa o texto no editor.</span><span class="sxs-lookup"><span data-stu-id="7ecee-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="7ecee-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="7ecee-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="7ecee-113">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-114">Se desloca o editor, para que a linha que corresponde a especificado **lineNumber** valor do parâmetro fica visível.</span><span class="sxs-lookup"><span data-stu-id="7ecee-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="7ecee-115">Ele lançará uma exceção se o número de linha especificado está fora do intervalo de 1, último número de linha, que define os números de linha válido.</span><span class="sxs-lookup"><span data-stu-id="7ecee-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="7ecee-116">**lineNumber** o número da linha que está a ficar visível.</span><span class="sxs-lookup"><span data-stu-id="7ecee-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="7ecee-117">Foco\(\)</span><span class="sxs-lookup"><span data-stu-id="7ecee-117">Focus\(\)</span></span>

<span data-ttu-id="7ecee-118">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-119">Define o foco para o editor.</span><span class="sxs-lookup"><span data-stu-id="7ecee-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="7ecee-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="7ecee-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="7ecee-121">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-122">Obtém o comprimento de linha como um número inteiro para a linha especificada pelo número de linha.</span><span class="sxs-lookup"><span data-stu-id="7ecee-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="7ecee-123">**lineNumber** o número de linha do qual pretende obter o comprimento.</span><span class="sxs-lookup"><span data-stu-id="7ecee-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="7ecee-124">**Devolve** o comprimento de linha para a linha em que o número de linha especificado.</span><span class="sxs-lookup"><span data-stu-id="7ecee-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="7ecee-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="7ecee-125">GoToMatch\(\)</span></span>

<span data-ttu-id="7ecee-126">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="7ecee-127">Move o sinal de interpolação para o caráter correspondente, se o **CanGoToMatch** é de propriedade do objeto editor **$true**, que ocorre quando o sinal de interpolação é imediatamente antes de um parêntese de abertura, colchete ou chave - \(,\[, {- ou imediatamente após o parêntesis de fecho, colchete ou chave - \),\],}.</span><span class="sxs-lookup"><span data-stu-id="7ecee-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="7ecee-128">O sinal de interpolação é colocado antes de um caráter de abertura ou após um caractere de fechamento.</span><span class="sxs-lookup"><span data-stu-id="7ecee-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="7ecee-129">Se o **CanGoToMatch** propriedade é **$false**, em seguida, esse método não faz nada.</span><span class="sxs-lookup"><span data-stu-id="7ecee-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="7ecee-130">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="7ecee-130">InsertText\( text \)</span></span>

<span data-ttu-id="7ecee-131">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-132">Substitui a seleção com texto ou insere texto na posição atual do sinal de interpolação.</span><span class="sxs-lookup"><span data-stu-id="7ecee-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="7ecee-133">**texto** -o texto para inserir a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7ecee-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="7ecee-134">Consulte a [exemplo de script](#scripting-example) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="7ecee-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="7ecee-135">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="7ecee-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="7ecee-136">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-137">Seleciona o texto a partir da **startLine**, **startColumn**, **endLine**, e **endColumn** parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7ecee-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="7ecee-138">**startLine** -número inteiro a linha em que a seleção é iniciada.</span><span class="sxs-lookup"><span data-stu-id="7ecee-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="7ecee-139">**startColumn** -número inteiro a coluna dentro da linha de início em que a seleção é iniciada.</span><span class="sxs-lookup"><span data-stu-id="7ecee-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="7ecee-140">**endLine** -número inteiro a linha onde termina a seleção.</span><span class="sxs-lookup"><span data-stu-id="7ecee-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="7ecee-141">**endColumn** -número inteiro a coluna na fim de linha onde termina a seleção.</span><span class="sxs-lookup"><span data-stu-id="7ecee-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="7ecee-142">Consulte a [exemplo de script](#scripting-example) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="7ecee-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="7ecee-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="7ecee-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="7ecee-144">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-145">Seleciona toda a linha de texto que atualmente contém o sinal de interpolação.</span><span class="sxs-lookup"><span data-stu-id="7ecee-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="7ecee-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="7ecee-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="7ecee-147">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-148">Define a posição do sinal de interpolação o número de linha e o número da coluna.</span><span class="sxs-lookup"><span data-stu-id="7ecee-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="7ecee-149">Ele lançará uma exceção se o número de linha de sinal de intercalação ou o número da coluna de sinal de interpolação está fora de seus respectivos intervalos válidos.</span><span class="sxs-lookup"><span data-stu-id="7ecee-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

<span data-ttu-id="7ecee-150">**lineNumber** -número inteiro o número de linha de sinal de interpolação.</span><span class="sxs-lookup"><span data-stu-id="7ecee-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="7ecee-151">**columnNumber** -número inteiro o número da coluna de sinal de interpolação.</span><span class="sxs-lookup"><span data-stu-id="7ecee-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="7ecee-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="7ecee-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="7ecee-153">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="7ecee-154">Faz com que todas as seções de contorno expandir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="7ecee-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="7ecee-155">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7ecee-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="7ecee-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="7ecee-156">CanGoToMatch</span></span>

<span data-ttu-id="7ecee-157">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="7ecee-158">A propriedade só de leitura booleana para indicar se o sinal de interpolação é junto a um parêntese, um colchete ou uma chave - \( \), \[ \], {}.</span><span class="sxs-lookup"><span data-stu-id="7ecee-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="7ecee-159">Se o sinal de interpolação é imediatamente antes do caráter de abertura ou imediatamente após o caractere de fechamento de um par, então este valor de propriedade é **$true**.</span><span class="sxs-lookup"><span data-stu-id="7ecee-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="7ecee-160">Caso contrário, será **$false**.</span><span class="sxs-lookup"><span data-stu-id="7ecee-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="7ecee-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="7ecee-161">CaretColumn</span></span>

<span data-ttu-id="7ecee-162">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-163">A propriedade só de leitura que obtém o número da coluna que corresponde à posição do sinal de interpolação de.</span><span class="sxs-lookup"><span data-stu-id="7ecee-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="7ecee-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="7ecee-164">CaretLine</span></span>

<span data-ttu-id="7ecee-165">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-166">A propriedade só de leitura que obtém o número de linha que contém o sinal de interpolação.</span><span class="sxs-lookup"><span data-stu-id="7ecee-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="7ecee-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="7ecee-167">CaretLineText</span></span>

<span data-ttu-id="7ecee-168">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-169">A propriedade só de leitura que obtém a completa de linha de texto que contém o sinal de interpolação.</span><span class="sxs-lookup"><span data-stu-id="7ecee-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="7ecee-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="7ecee-170">LineCount</span></span>

<span data-ttu-id="7ecee-171">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-172">A propriedade só de leitura que obtém a contagem de linha do editor.</span><span class="sxs-lookup"><span data-stu-id="7ecee-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="7ecee-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="7ecee-173">SelectedText</span></span>

<span data-ttu-id="7ecee-174">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-175">A propriedade só de leitura que obtém o texto selecionado do editor.</span><span class="sxs-lookup"><span data-stu-id="7ecee-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="7ecee-176">Consulte a [exemplo de script](#scripting-example) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="7ecee-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="7ecee-177">Texto</span><span class="sxs-lookup"><span data-stu-id="7ecee-177">Text</span></span>

<span data-ttu-id="7ecee-178">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7ecee-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7ecee-179">A propriedade de leitura/gravação que obtém ou define o texto no editor.</span><span class="sxs-lookup"><span data-stu-id="7ecee-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="7ecee-180">Consulte a [exemplo de script](#scripting-example) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="7ecee-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="7ecee-181">Scripts de exemplo</span><span class="sxs-lookup"><span data-stu-id="7ecee-181">Scripting Example</span></span>

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase.
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line.
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="7ecee-182">Veja Também</span><span class="sxs-lookup"><span data-stu-id="7ecee-182">See Also</span></span>

- [<span data-ttu-id="7ecee-183">Objeto ISEFile</span><span class="sxs-lookup"><span data-stu-id="7ecee-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="7ecee-184">Objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="7ecee-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="7ecee-185">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="7ecee-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="7ecee-186">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="7ecee-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)