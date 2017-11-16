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
# <a name="the-iseeditor-object"></a>O objeto de ISEEditor
  Um **ISEEditor** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEEditor. O painel de consola é um **ISEEditor** objeto. Cada [ISEFile](The-ISEFile-Object.md) objeto tem um associados **ISEEditor** objeto. As secções seguintes listam os métodos e propriedades de um **ISEEditor** objeto.

## <a name="methods"></a>Métodos

### <a name="clear"></a>Limpar\(\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Limpa o texto no editor.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Desloca o editor de modo a que a linha que corresponde a especificado **lineNumber** valor do parâmetro fica visível. -Emite uma exceção se o número de linhas especificado está fora do intervalo de 1, último número de linha, que define os números de linha válido.

 **lineNumber** o número de linha que está a ser tornado visível.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Foco\(\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Define o foco para o editor.

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Obtém o comprimento de linha como um valor inteiro para a linha que é especificada o número de linha.

 **lineNumber** o número de linha da qual pode obter o comprimento.

 **Devolve** o comprimento de linha para a linha no número de linhas especificado.

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 Move o acento circunflexo ao caráter correspondente, se o **CanGoToMatch** é propriedade do objeto do editor **$true**, que ocorre quando o acento circunflexo imediatamente antes de um parêntese, parêntese ou Chaveta - \(,\[, {- ou imediatamente após um parêntese, parêntese ou Chaveta - \),\],}.  O acento circunflexo é colocado antes de um caráter de abertura ou após um caráter de fecho. Se o **CanGoToMatch** propriedade é **$false**, em seguida, este método não produz qualquer efeito.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a>InsertText\( texto\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Substitui a seleção com texto ou introduza o texto da posição de acento circunflexo atual.

 **texto** -o texto a inserção da cadeia.

 Consulte o [Scripting exemplo](#scripting-example) mais adiante neste tópico.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Selecione\( startLine, startColumn, endLine, endColumn\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Seleciona o texto do **startLine**, **startColumn**, **endLine**, e **endColumn** parâmetros.

 **startLine** -número inteiro a linha em que a seleção é iniciada.

 **startColumn** -número inteiro a coluna dentro da linha de início em que a seleção é iniciada.

 **endLine** -número inteiro a linha em que a seleção termina.

 **endColumn** -número inteiro a coluna dentro da linha de fim onde termina a seleção.

 Consulte o [Scripting exemplo](#scripting-example) mais adiante neste tópico.

### <a name="selectcaretline"></a>SelectCaretLine\(\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Seleciona a toda a linha de texto que contém o acento circunflexo atualmente.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Define a posição de acento circunflexo o número de linha e o número de coluna. -Emite uma exceção se o número de linha de acento circunflexo ou o número de coluna de acento circunflexo está fora do respetivos respetivos intervalos válidos.

 **lineNumber** -número inteiro o número de linha de acento circunflexo.

 **columnNumber** -número inteiro o número de coluna de acento circunflexo.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 Faz com que todas as secções de contorno expandir ou fechar.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Propriedades

### <a name="cangotomatch"></a>CanGoToMatch
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 A propriedade booleana só de leitura para indicar se o acento circunflexo foi junto a um parêntesis, parêntese ou Chaveta - \( \), \[ \], {}. Se o acento circunflexo é imediatamente antes do caráter de abertura ou imediatamente após o caráter de fecho de um par de, em seguida, este valor de propriedade é **$true**. Caso contrário, é **$false**.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém o número de colunas que corresponde a posição do acento circunflexo.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém o número da linha que contém o acento circunflexo.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém a linha de texto que contém o acento circunflexo concluída.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém a contagem de linha do editor.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém o texto seleccionado a partir do editor.

 Consulte o [Scripting exemplo](#scripting-example) mais adiante neste tópico.

### <a name="text"></a>Texto
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade de leitura/escrita que obtém ou define o texto no editor.

 Consulte o [Scripting exemplo](#scripting-example) mais adiante neste tópico.

## <a name="scripting-example"></a>Exemplo de script

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

## <a name="see-also"></a>Consulte Também
- [O objeto de ISEFile](The-ISEFile-Object.md) 
- [O objeto de PowerShellTab](The-PowerShellTab-Object.md) 
- [O ISE do Windows PowerShell modelo de objeto de Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto ISE](The-ISE-Object-Model-Hierarchy.md)

  
