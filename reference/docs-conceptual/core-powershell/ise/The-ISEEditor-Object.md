---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de ISEEditor
ms.openlocfilehash: c593eeebf0b9a94769841efd2aa78f84a3829ca5
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2017
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="76108-103">O objeto de ISEEditor</span><span class="sxs-lookup"><span data-stu-id="76108-103">The ISEEditor Object</span></span>
  <span data-ttu-id="76108-104">Um **ISEEditor** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="76108-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="76108-105">O painel de consola é um **ISEEditor** objeto.</span><span class="sxs-lookup"><span data-stu-id="76108-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="76108-106">Cada [ISEFile](The-ISEFile-Object.md) objeto tem um associados **ISEEditor** objeto.</span><span class="sxs-lookup"><span data-stu-id="76108-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="76108-107">As secções seguintes listam os métodos e propriedades de um **ISEEditor** objeto.</span><span class="sxs-lookup"><span data-stu-id="76108-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="76108-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="76108-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="76108-109">Limpar\(\)</span><span class="sxs-lookup"><span data-stu-id="76108-109">Clear\(\)</span></span>
  <span data-ttu-id="76108-110">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-111">Limpa o texto no editor.</span><span class="sxs-lookup"><span data-stu-id="76108-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="76108-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="76108-112">EnsureVisible\(int lineNumber\)</span></span>
  <span data-ttu-id="76108-113">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-114">Desloca o editor de modo a que a linha que corresponde a especificado **lineNumber** valor do parâmetro fica visível.</span><span class="sxs-lookup"><span data-stu-id="76108-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="76108-115">-Emite uma exceção se o número de linhas especificado está fora do intervalo de 1, último número de linha, que define os números de linha válido.</span><span class="sxs-lookup"><span data-stu-id="76108-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

 <span data-ttu-id="76108-116">**lineNumber** o número de linha que está a ser tornado visível.</span><span class="sxs-lookup"><span data-stu-id="76108-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="76108-117">Foco\(\)</span><span class="sxs-lookup"><span data-stu-id="76108-117">Focus\(\)</span></span>
  <span data-ttu-id="76108-118">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-119">Define o foco para o editor.</span><span class="sxs-lookup"><span data-stu-id="76108-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="76108-120">GetLineLength\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="76108-120">GetLineLength\(int lineNumber \)</span></span>
  <span data-ttu-id="76108-121">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-122">Obtém o comprimento de linha como um valor inteiro para a linha que é especificada o número de linha.</span><span class="sxs-lookup"><span data-stu-id="76108-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

 <span data-ttu-id="76108-123">**lineNumber** o número de linha da qual pode obter o comprimento.</span><span class="sxs-lookup"><span data-stu-id="76108-123">**lineNumber** The number of the line of which to get the length.</span></span>

 <span data-ttu-id="76108-124">**Devolve** o comprimento de linha para a linha no número de linhas especificado.</span><span class="sxs-lookup"><span data-stu-id="76108-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="76108-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="76108-125">GoToMatch\(\)</span></span>
  <span data-ttu-id="76108-126">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="76108-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="76108-127">Move o acento circunflexo ao caráter correspondente, se o **CanGoToMatch** é propriedade do objeto do editor **$true**, que ocorre quando o acento circunflexo imediatamente antes de um parêntese, parêntese ou Chaveta - \(,\[, {- ou imediatamente após um parêntese, parêntese ou Chaveta - \),\],}.</span><span class="sxs-lookup"><span data-stu-id="76108-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="76108-128">O acento circunflexo é colocado antes de um caráter de abertura ou após um caráter de fecho.</span><span class="sxs-lookup"><span data-stu-id="76108-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="76108-129">Se o **CanGoToMatch** propriedade é **$false**, em seguida, este método não produz qualquer efeito.</span><span class="sxs-lookup"><span data-stu-id="76108-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a><span data-ttu-id="76108-130">InsertText\( texto\)</span><span class="sxs-lookup"><span data-stu-id="76108-130">InsertText\( text \)</span></span>
  <span data-ttu-id="76108-131">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-132">Substitui a seleção com texto ou introduza o texto da posição de acento circunflexo atual.</span><span class="sxs-lookup"><span data-stu-id="76108-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

 <span data-ttu-id="76108-133">**texto** -o texto a inserção da cadeia.</span><span class="sxs-lookup"><span data-stu-id="76108-133">**text** - String The text to insert.</span></span>

 <span data-ttu-id="76108-134">Consulte o [Scripting exemplo](#scripting-example) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="76108-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="76108-135">Selecione\( startLine, startColumn, endLine, endColumn\)</span><span class="sxs-lookup"><span data-stu-id="76108-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>
  <span data-ttu-id="76108-136">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-137">Seleciona o texto do **startLine**, **startColumn**, **endLine**, e **endColumn** parâmetros.</span><span class="sxs-lookup"><span data-stu-id="76108-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

 <span data-ttu-id="76108-138">**startLine** -número inteiro a linha em que a seleção é iniciada.</span><span class="sxs-lookup"><span data-stu-id="76108-138">**startLine** - Integer The line where the selection starts.</span></span>

 <span data-ttu-id="76108-139">**startColumn** -número inteiro a coluna dentro da linha de início em que a seleção é iniciada.</span><span class="sxs-lookup"><span data-stu-id="76108-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

 <span data-ttu-id="76108-140">**endLine** -número inteiro a linha em que a seleção termina.</span><span class="sxs-lookup"><span data-stu-id="76108-140">**endLine** - Integer The line where the selection ends.</span></span>

 <span data-ttu-id="76108-141">**endColumn** -número inteiro a coluna dentro da linha de fim onde termina a seleção.</span><span class="sxs-lookup"><span data-stu-id="76108-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

 <span data-ttu-id="76108-142">Consulte o [Scripting exemplo](#scripting-example) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="76108-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="76108-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="76108-143">SelectCaretLine\(\)</span></span>
  <span data-ttu-id="76108-144">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-145">Seleciona a toda a linha de texto que contém o acento circunflexo atualmente.</span><span class="sxs-lookup"><span data-stu-id="76108-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="76108-146">SetCaretPosition\( lineNumber, columnNumber\)</span><span class="sxs-lookup"><span data-stu-id="76108-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>
  <span data-ttu-id="76108-147">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-148">Define a posição de acento circunflexo o número de linha e o número de coluna.</span><span class="sxs-lookup"><span data-stu-id="76108-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="76108-149">-Emite uma exceção se o número de linha de acento circunflexo ou o número de coluna de acento circunflexo está fora do respetivos respetivos intervalos válidos.</span><span class="sxs-lookup"><span data-stu-id="76108-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

 <span data-ttu-id="76108-150">**lineNumber** -número inteiro o número de linha de acento circunflexo.</span><span class="sxs-lookup"><span data-stu-id="76108-150">**lineNumber** - Integer The caret line number.</span></span>

 <span data-ttu-id="76108-151">**columnNumber** -número inteiro o número de coluna de acento circunflexo.</span><span class="sxs-lookup"><span data-stu-id="76108-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="76108-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="76108-152">ToggleOutliningExpansion\(\)</span></span>
  <span data-ttu-id="76108-153">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="76108-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="76108-154">Faz com que todas as secções de contorno expandir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="76108-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="76108-155">Propriedades</span><span class="sxs-lookup"><span data-stu-id="76108-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="76108-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="76108-156">CanGoToMatch</span></span>
  <span data-ttu-id="76108-157">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="76108-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="76108-158">A propriedade booleana só de leitura para indicar se o acento circunflexo foi junto a um parêntesis, parêntese ou Chaveta - \( \), \[ \], {}.</span><span class="sxs-lookup"><span data-stu-id="76108-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="76108-159">Se o acento circunflexo é imediatamente antes do caráter de abertura ou imediatamente após o caráter de fecho de um par de, em seguida, este valor de propriedade é **$true**.</span><span class="sxs-lookup"><span data-stu-id="76108-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="76108-160">Caso contrário, é **$false**.</span><span class="sxs-lookup"><span data-stu-id="76108-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="76108-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="76108-161">CaretColumn</span></span>
  <span data-ttu-id="76108-162">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-163">A propriedade só de leitura que obtém o número de colunas que corresponde a posição do acento circunflexo.</span><span class="sxs-lookup"><span data-stu-id="76108-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="76108-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="76108-164">CaretLine</span></span>
  <span data-ttu-id="76108-165">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-166">A propriedade só de leitura que obtém o número da linha que contém o acento circunflexo.</span><span class="sxs-lookup"><span data-stu-id="76108-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="76108-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="76108-167">CaretLineText</span></span>
  <span data-ttu-id="76108-168">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-169">A propriedade só de leitura que obtém a linha de texto que contém o acento circunflexo concluída.</span><span class="sxs-lookup"><span data-stu-id="76108-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="76108-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="76108-170">LineCount</span></span>
  <span data-ttu-id="76108-171">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-172">A propriedade só de leitura que obtém a contagem de linha do editor.</span><span class="sxs-lookup"><span data-stu-id="76108-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="76108-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="76108-173">SelectedText</span></span>
  <span data-ttu-id="76108-174">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-175">A propriedade só de leitura que obtém o texto seleccionado a partir do editor.</span><span class="sxs-lookup"><span data-stu-id="76108-175">The read-only property that gets the selected text from the editor.</span></span>

 <span data-ttu-id="76108-176">Consulte o [Scripting exemplo](#scripting-example) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="76108-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="76108-177">Texto</span><span class="sxs-lookup"><span data-stu-id="76108-177">Text</span></span>
  <span data-ttu-id="76108-178">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="76108-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="76108-179">A propriedade de leitura/escrita que obtém ou define o texto no editor.</span><span class="sxs-lookup"><span data-stu-id="76108-179">The read/write property that gets or sets the text in the editor.</span></span>

 <span data-ttu-id="76108-180">Consulte o [Scripting exemplo](#scripting-example) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="76108-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="76108-181">Exemplo de script</span><span class="sxs-lookup"><span data-stu-id="76108-181">Scripting Example</span></span>

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
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="76108-182">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="76108-182">See Also</span></span>
- [<span data-ttu-id="76108-183">O objeto de ISEFile</span><span class="sxs-lookup"><span data-stu-id="76108-183">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="76108-184">O objeto de PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="76108-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="76108-185">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="76108-185">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="76108-186">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="76108-186">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="76108-187">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="76108-187">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
