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
# <a name="the-iseeditor-object"></a>Objeto ISEEditor

Uma **ISEEditor** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEEditor. O painel de consola é um **ISEEditor** objeto. Cada [ISEFile](The-ISEFile-Object.md) -se associado ao objeto **ISEEditor** objeto. As secções seguintes listam os métodos e propriedades de um **ISEEditor** objeto.

## <a name="methods"></a>Métodos

### <a name="clear"></a>Limpar\(\)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Limpa o texto no editor.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Se desloca o editor, para que a linha que corresponde a especificado **lineNumber** valor do parâmetro fica visível. Ele lançará uma exceção se o número de linha especificado está fora do intervalo de 1, último número de linha, que define os números de linha válido.

**lineNumber** o número da linha que está a ficar visível.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Foco\(\)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Define o foco para o editor.

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber \)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Obtém o comprimento de linha como um número inteiro para a linha especificada pelo número de linha.

**lineNumber** o número de linha do qual pretende obter o comprimento.

**Devolve** o comprimento de linha para a linha em que o número de linha especificado.

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

Move o sinal de interpolação para o caráter correspondente, se o **CanGoToMatch** é de propriedade do objeto editor **$true**, que ocorre quando o sinal de interpolação é imediatamente antes de um parêntese de abertura, colchete ou chave - \(,\[, {- ou imediatamente após o parêntesis de fecho, colchete ou chave - \),\],}.  O sinal de interpolação é colocado antes de um caráter de abertura ou após um caractere de fechamento. Se o **CanGoToMatch** propriedade é **$false**, em seguida, esse método não faz nada.

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>InsertText\( text \)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Substitui a seleção com texto ou insere texto na posição atual do sinal de interpolação.

**texto** -o texto para inserir a cadeia de caracteres.

Consulte a [exemplo de script](#scripting-example) mais adiante neste tópico.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Select\( startLine, startColumn, endLine, endColumn \)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Seleciona o texto a partir da **startLine**, **startColumn**, **endLine**, e **endColumn** parâmetros.

**startLine** -número inteiro a linha em que a seleção é iniciada.

**startColumn** -número inteiro a coluna dentro da linha de início em que a seleção é iniciada.

**endLine** -número inteiro a linha onde termina a seleção.

**endColumn** -número inteiro a coluna na fim de linha onde termina a seleção.

Consulte a [exemplo de script](#scripting-example) mais adiante neste tópico.

### <a name="selectcaretline"></a>SelectCaretLine\(\)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Seleciona toda a linha de texto que atualmente contém o sinal de interpolação.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber \)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Define a posição do sinal de interpolação o número de linha e o número da coluna. Ele lançará uma exceção se o número de linha de sinal de intercalação ou o número da coluna de sinal de interpolação está fora de seus respectivos intervalos válidos.

**lineNumber** -número inteiro o número de linha de sinal de interpolação.

**columnNumber** -número inteiro o número da coluna de sinal de interpolação.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

Faz com que todas as seções de contorno expandir ou fechar.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Propriedades

### <a name="cangotomatch"></a>CanGoToMatch

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

A propriedade só de leitura booleana para indicar se o sinal de interpolação é junto a um parêntese, um colchete ou uma chave - \( \), \[ \], {}. Se o sinal de interpolação é imediatamente antes do caráter de abertura ou imediatamente após o caractere de fechamento de um par, então este valor de propriedade é **$true**. Caso contrário, será **$false**.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém o número da coluna que corresponde à posição do sinal de interpolação de.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém o número de linha que contém o sinal de interpolação.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém a completa de linha de texto que contém o sinal de interpolação.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém a contagem de linha do editor.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém o texto selecionado do editor.

Consulte a [exemplo de script](#scripting-example) mais adiante neste tópico.

### <a name="text"></a>Texto

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade de leitura/gravação que obtém ou define o texto no editor.

Consulte a [exemplo de script](#scripting-example) mais adiante neste tópico.

## <a name="scripting-example"></a>Scripts de exemplo

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

## <a name="see-also"></a>Veja Também

- [Objeto ISEFile](The-ISEFile-Object.md)
- [Objeto PowerShellTab](The-PowerShellTab-Object.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)