---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953655"
---
# <a name="the-iseoptions-object"></a>Objeto ISEOptions

O **ISEOptions** objeto representa várias definições de ISE do Windows PowerShell. É uma instância do **Microsoft.PowerShell.Host.ISE.ISEOptions** classe.

O **ISEOptions** objeto fornece as seguintes propriedades e métodos.

## <a name="methods"></a>Métodos

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Restaura os valores predefinidos das cores token no painel de consola.

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)

Suportado no Windows PowerShell ISE 2.0 e posterior.

Restaura os valores predefinidos de todas as definições de opções no painel de consola. Também redefine o comportamento de várias mensagens de aviso que fornecem a caixa de verificação standard para impedir que a mensagem a ser mostrada novamente.

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)

Suportado no Windows PowerShell ISE 2.0 e posterior.

Restaura os valores predefinidos das cores token no painel de Script.

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Restaura os valores predefinidos das cores de token para elementos XML que são apresentadas no ISE do Windows PowerShell. Consulte também [XmlTokenColors](#xmltokencolors).

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>Propriedades

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica o número de minutos entre operações de gravação automática dos seus ficheiros ao ISE do Windows PowerShell. O valor predefinido é de 2 minutos. O valor é um número inteiro.

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor

Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.  Para versões posteriores, consulte [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Especifica a cor de fundo para o painel de comandos. É uma instância do **System.Windows.Media.Color** classe.

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a>CommandPaneUp

Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.

Especifica se o painel de comandos está localizado acima do painel de resultados.

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a>ConsolePaneBackgroundColor

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica a cor de fundo para o painel de consola. É uma instância do **System.Windows.Media.Color** classe.

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica a cor de primeiro plano do texto no painel de consola.

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica a cor de fundo do texto no painel de consola.

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a>ConsoleTokenColors

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica as cores dos IntelliSense tokens no painel de consola do ISE do Windows PowerShell. Esta propriedade é um objeto de dicionário que contém os pares nome/valor de tipos de tokens e de cores para o painel de consola. Para alterar as cores dos tokens de IntelliSense, no painel de Script, consulte [TokenColors](#tokencolors). Para repor as cores para os valores predefinidos, consulte [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors). Cores token podem ser definidas para o seguinte: atributo, comando, CommandArgument, CommandParameter, comentário, GroupEnd, GroupStart, palavra-chave, LineContinuation, LoopLabel, membro, uma nova linha, número, operador, posição, StatementSeparator, cadeia, tipo, Desconhecido, a variável.

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica a cor de fundo para a depuração de texto que aparece no painel de consola. É uma instância do **System.Windows.Media.Color** classe.

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica a cor de primeiro plano para a depuração de texto que aparece no painel de consola. É uma instância do **System.Windows.Media.Color** classe.

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a>DefaultOptions

Suportado no Windows PowerShell ISE 2.0 e posterior.

Uma coleção de propriedades que especificam os valores predefinidos para ser utilizado quando são utilizados os métodos de reposição.

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a>ErrorBackgroundColor

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica a cor de fundo de texto de erro que aparece no painel de consola. É uma instância do **System.Windows.Media.Color** classe.

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica a cor de primeiro plano para texto de erro que aparece no painel de consola. É uma instância do **System.Windows.Media.Color** classe.

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a>FontName

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica o nome de tipo de letra atualmente em utilização no painel de Script e o painel de consola.

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a>FontSize

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica o tamanho de tipo de letra como um número inteiro. É utilizado no painel de Script, o painel de comando e o painel de resultados. O intervalo de valores válido é de 8 a 32.

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica o número de segundos que utiliza o IntelliSense para tentar resolver o texto atualmente escrito. Após o número de segundos, o IntelliSense exceder o tempo limite e permite-lhe continuar a escrever. O valor predefinido é 3 segundos. O valor é um número inteiro.

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica o número de ficheiros recentemente abertos que ISE do Windows PowerShell controla e apresenta na parte inferior do **ficheiro aberto** menu. O valor predefinido é 10. O valor é um número inteiro.

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor

Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.  Para versões posteriores, consulte [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

A propriedade de leitura/escrita que obtém ou define a cor de fundo do painel de resultados do próprio. É uma instância do **System.Windows.Media.Color** classe.

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor

Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.  Para versões posteriores, consulte [ConsolePaneForegroundColor](#consolepaneforegroundcolor).

A propriedade de leitura/escrita que altera a cor de primeiro plano do texto no painel de resultados no Windows PowerShell ISE 2.0.

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor

Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.  Para versões posteriores, consulte [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).

A propriedade de leitura/escrita que altera a cor de fundo do texto no painel de resultados.

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor

Suportado no Windows PowerShell ISE 2.0 e posterior.

A propriedade de leitura/escrita que obtém ou define a cor de fundo para os ficheiros. É uma instância do **System.Windows.Media.Color** classe.

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor

Suportado no Windows PowerShell ISE 2.0 e posterior.

A propriedade de leitura/escrita que obtém ou define a cor de primeiro plano para ficheiros de script não no painel de Script.
Para definir a cor de primeiro plano para ficheiros de script, utilize o [TokenColors](#tokencolors).

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState

Suportado no Windows PowerShell ISE 2.0 e posterior.

A propriedade de leitura/escrita que obtém ou define a posição do painel de Script no ecrã do. A cadeia pode ser 'Maximizado', 'Top' ou 'Direita'.

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica se o **CTRL + J** lista de fragmentos inclui o conjunto de arranque que está incluído no Windows PowerShell. Quando definido como **$false**, apenas os fragmentos definido pelo utilizador são apresentados no **CTRL + J** lista. O valor predefinido é **$true**.

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica se o IntelliSense oferece sintaxe, parâmetros e sugestões de valor no painel de consola. O valor predefinido é **$true**.

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica se o IntelliSense oferece sintaxe, parâmetros e sugestões de valor no painel de Script. O valor predefinido é **$true**.

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica se o painel de Script apresenta números de linha na margem esquerda. O valor predefinido é **$true**.

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica se o painel de Script apresenta Retos expansíveis e expansíveis junto de secções de código na margem esquerda. Quando estes são apresentados, pode clicar no sinal de subtração \( - \) ícones junto de um bloco de texto para fechá-lo ou clique no sinal de adição \( + \) ícone para expandir um bloco de texto. O valor predefinido é **$true**.

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica se a barra de ferramentas ISE aparece na parte superior da janela ISE do Windows PowerShell. O valor predefinido é **$true**.

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica se é apresentada uma mensagem de aviso quando um script é guardado automaticamente antes de ser executada. O valor predefinido é **$true**.

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica se é apresentada uma mensagem de aviso quando o mesmo ficheiro é aberto na diferentes separadores do PowerShell. Se definido como **$true**, para abrir o mesmo ficheiro nos vários separadores apresenta esta mensagem: "uma cópia deste ficheiro se encontra aberta noutro separador do Windows PowerShell. As alterações efetuadas a este ficheiro irão afetar copia todos os abrir." O valor predefinido é **$true**.

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a>TokenColors

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica as cores dos IntelliSense tokens no painel de Script do Windows PowerShell ISE. Esta propriedade é um objeto de dicionário que contém os pares nome/valor de tipos de tokens e de cores para o painel de Script. Para alterar as cores dos tokens de IntelliSense, no painel de consola, consulte [ConsoleTokenColors](#consoletokencolors). Para repor as cores para os valores predefinidos, consulte [RestoreDefaultTokenColors](#restoredefaulttokencolors). Cores token podem ser definidas para o seguinte: atributo, comando, CommandArgument, CommandParameter, comentário, GroupEnd, GroupStart, palavra-chave, LineContinuation, LoopLabel, membro, uma nova linha, número, operador, posição, StatementSeparator, cadeia, tipo, Desconhecido, a variável.

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica se pode utilizar a tecla Enter para selecionar um IntelliSense fornecido opção no painel de consola. O valor predefinido é **$true**.

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica se pode utilizar a tecla Enter para selecionar uma opção IntelliSense fornecidos no painel de Script. O valor predefinido é **$true**.

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a>UseLocalHelp

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica se a ajuda instalada localmente ou ajuda Biblioteca TechNet online é apresentada quando prime F1 com o cursor posicionado numa palavra-chave. Se definido como **$true**, em seguida, uma janela de pop-up mostra conteúda de ajuda do instalada localmente. Pode instalar os ficheiros de ajuda, executando o `Update-Help` comando. Se definido como **$false**, em seguida, o browser abre-se a uma página na Biblioteca TechNet.

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica a cor de fundo para verboso texto que aparece no painel de consola. É um **System.Windows.Media.Color** objeto.

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica a cor de primeiro plano para verboso texto que aparece no painel de consola. É um **System.Windows.Media.Color** objeto.

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica a cor de fundo de texto de aviso que aparece no painel de consola. É um **System.Windows.Media.Color** objeto.

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor

Suportado no Windows PowerShell ISE 2.0 e posterior.

Especifica a cor de primeiro plano para texto de aviso que aparece no painel de resultados. É um **System.Windows.Media.Color** objeto.

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica um objeto de dicionário que contém os pares nome/valor de tipos de tokens e de cores para o conteúdo XML que é apresentado no ISE do Windows PowerShell. Cores token podem ser definidas para o seguinte: atributo, comando, CommandArgument, CommandParameter, comentário, GroupEnd, GroupStart, palavra-chave, LineContinuation, LoopLabel, membro, uma nova linha, número, operador, posição, StatementSeparator, cadeia, tipo, Desconhecido, a variável. Consulte também [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a>Zoom

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

Especifica o tamanho relativo de texto em painéis da consola e o Script. O valor predefinido é 100. Os valores mais pequenos fazer com que o texto no ISE do Windows PowerShell apareça mais pequenos enquanto maiores números causam texto apareça maior. O valor é um número inteiro que intervalos de 20 para 400.

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>Consulte Também

- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)