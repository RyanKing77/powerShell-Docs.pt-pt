---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 5e04adeebacfb9214bf39d9ec9c5f0e01f5729ee
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="60339-103">O objeto de ISEOptions</span><span class="sxs-lookup"><span data-stu-id="60339-103">The ISEOptions Object</span></span>
  <span data-ttu-id="60339-104">O **ISEOptions** objeto representa várias definições de ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60339-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="60339-105">É uma instância do **Microsoft.PowerShell.Host.ISE.ISEOptions** classe.</span><span class="sxs-lookup"><span data-stu-id="60339-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="60339-106">O **ISEOptions** objeto fornece as seguintes propriedades e métodos.</span><span class="sxs-lookup"><span data-stu-id="60339-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="60339-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="60339-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="60339-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="60339-108">RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="60339-109">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-110">Restaura os valores predefinidos das cores token no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-110">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="60339-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="60339-111">RestoreDefaults\(\)</span></span>
  <span data-ttu-id="60339-112">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-113">Restaura os valores predefinidos de todas as definições de opções no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="60339-114">Também redefine o comportamento de várias mensagens de aviso que fornecem a caixa de verificação standard para impedir que a mensagem a ser mostrada novamente.</span><span class="sxs-lookup"><span data-stu-id="60339-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="60339-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="60339-115">RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="60339-116">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-117">Restaura os valores predefinidos das cores token no painel de Script.</span><span class="sxs-lookup"><span data-stu-id="60339-117">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="60339-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="60339-118">RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="60339-119">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-120">Restaura os valores predefinidos das cores de token para elementos XML que são apresentadas no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60339-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="60339-121">Consulte também [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="60339-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="60339-122">Propriedades</span><span class="sxs-lookup"><span data-stu-id="60339-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="60339-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="60339-123">AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="60339-124">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-125">Especifica o número de minutos entre operações de gravação automática dos seus ficheiros ao ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60339-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="60339-126">O valor predefinido é de 2 minutos.</span><span class="sxs-lookup"><span data-stu-id="60339-126">The default value is 2 minutes.</span></span> <span data-ttu-id="60339-127">O valor é um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="60339-127">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="60339-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-128">CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="60339-129">Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.</span><span class="sxs-lookup"><span data-stu-id="60339-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="60339-130">Para versões posteriores, consulte [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="60339-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

 <span data-ttu-id="60339-131">Especifica a cor de fundo para o painel de comandos.</span><span class="sxs-lookup"><span data-stu-id="60339-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="60339-132">É uma instância do **System.Windows.Media.Color** classe.</span><span class="sxs-lookup"><span data-stu-id="60339-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

### <a name="commandpaneup"></a><span data-ttu-id="60339-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="60339-133">CommandPaneUp</span></span>
  <span data-ttu-id="60339-134">Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.</span><span class="sxs-lookup"><span data-stu-id="60339-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="60339-135">Especifica se o painel de comandos está localizado acima do painel de resultados.</span><span class="sxs-lookup"><span data-stu-id="60339-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="60339-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-136">ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="60339-137">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-138">Especifica a cor de fundo para o painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="60339-139">É uma instância do **System.Windows.Media.Color** classe.</span><span class="sxs-lookup"><span data-stu-id="60339-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="60339-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-140">ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="60339-141">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-142">Especifica a cor de primeiro plano do texto no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-142">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="60339-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-143">ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="60339-144">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-145">Especifica a cor de fundo do texto no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-145">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

### <a name="consoletokencolors"></a><span data-ttu-id="60339-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="60339-146">ConsoleTokenColors</span></span>
  <span data-ttu-id="60339-147">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-148">Especifica as cores dos IntelliSense tokens no painel de consola do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60339-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="60339-149">Esta propriedade é um objeto de dicionário que contém os pares nome/valor de tipos de tokens e de cores para o painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="60339-150">Para alterar as cores dos tokens de IntelliSense, no painel de Script, consulte [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="60339-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="60339-151">Para repor as cores para os valores predefinidos, consulte [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="60339-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="60339-152">Cores token podem ser definidas para o seguinte: atributo, comando, CommandArgument, CommandParameter, comentário, GroupEnd, GroupStart, palavra-chave, LineContinuation, LoopLabel, membro, uma nova linha, número, operador, posição, StatementSeparator, cadeia, tipo, Desconhecido, a variável.</span><span class="sxs-lookup"><span data-stu-id="60339-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="60339-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-153">DebugBackgroundColor</span></span>
  <span data-ttu-id="60339-154">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-155">Especifica a cor de fundo para a depuração de texto que aparece no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="60339-156">É uma instância do **System.Windows.Media.Color** classe.</span><span class="sxs-lookup"><span data-stu-id="60339-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="60339-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-157">DebugForegroundColor</span></span>
  <span data-ttu-id="60339-158">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-159">Especifica a cor de primeiro plano para a depuração de texto que aparece no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="60339-160">É uma instância do **System.Windows.Media.Color** classe.</span><span class="sxs-lookup"><span data-stu-id="60339-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

### <a name="defaultoptions"></a><span data-ttu-id="60339-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="60339-161">DefaultOptions</span></span>
  <span data-ttu-id="60339-162">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-163">Uma coleção de propriedades que especificam os valores predefinidos para ser utilizado quando são utilizados os métodos de reposição.</span><span class="sxs-lookup"><span data-stu-id="60339-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```
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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="60339-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-164">ErrorBackgroundColor</span></span>
  <span data-ttu-id="60339-165">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-166">Especifica a cor de fundo de texto de erro que aparece no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="60339-167">É uma instância do **System.Windows.Media.Color** classe.</span><span class="sxs-lookup"><span data-stu-id="60339-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="60339-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-168">ErrorForegroundColor</span></span>
  <span data-ttu-id="60339-169">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-170">Especifica a cor de primeiro plano para texto de erro que aparece no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="60339-171">É uma instância do **System.Windows.Media.Color** classe.</span><span class="sxs-lookup"><span data-stu-id="60339-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

### <a name="fontname"></a><span data-ttu-id="60339-172">FontName</span><span class="sxs-lookup"><span data-stu-id="60339-172">FontName</span></span>
  <span data-ttu-id="60339-173">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-174">Especifica o nome de tipo de letra atualmente em utilização no painel de Script e o painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

### <a name="fontsize"></a><span data-ttu-id="60339-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="60339-175">FontSize</span></span>
  <span data-ttu-id="60339-176">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-177">Especifica o tamanho de tipo de letra como um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="60339-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="60339-178">É utilizado no painel de Script, o painel de comando e o painel de resultados.</span><span class="sxs-lookup"><span data-stu-id="60339-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="60339-179">O intervalo de valores válido é de 8 a 32.</span><span class="sxs-lookup"><span data-stu-id="60339-179">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="60339-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="60339-180">IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="60339-181">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-182">Especifica o número de segundos que utiliza o IntelliSense para tentar resolver o texto atualmente escrito.</span><span class="sxs-lookup"><span data-stu-id="60339-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="60339-183">Após o número de segundos, o IntelliSense exceder o tempo limite e permite-lhe continuar a escrever.</span><span class="sxs-lookup"><span data-stu-id="60339-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="60339-184">O valor predefinido é 3 segundos.</span><span class="sxs-lookup"><span data-stu-id="60339-184">The default value is 3 seconds.</span></span> <span data-ttu-id="60339-185">O valor é um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="60339-185">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="60339-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="60339-186">MruCount</span></span>
  <span data-ttu-id="60339-187">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-188">Especifica o número de ficheiros recentemente abertos que ISE do Windows PowerShell controla e apresenta na parte inferior do **ficheiro aberto** menu.</span><span class="sxs-lookup"><span data-stu-id="60339-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="60339-189">O valor predefinido é 10.</span><span class="sxs-lookup"><span data-stu-id="60339-189">The default value is 10.</span></span> <span data-ttu-id="60339-190">O valor é um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="60339-190">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="60339-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-191">OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="60339-192">Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.</span><span class="sxs-lookup"><span data-stu-id="60339-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="60339-193">Para versões posteriores, consulte [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="60339-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

 <span data-ttu-id="60339-194">A propriedade de leitura/escrita que obtém ou define a cor de fundo do painel de resultados do próprio.</span><span class="sxs-lookup"><span data-stu-id="60339-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="60339-195">É uma instância do **System.Windows.Media.Color** classe.</span><span class="sxs-lookup"><span data-stu-id="60339-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="60339-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-196">OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="60339-197">Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.</span><span class="sxs-lookup"><span data-stu-id="60339-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="60339-198">Para versões posteriores, consulte [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="60339-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

 <span data-ttu-id="60339-199">A propriedade de leitura/escrita que altera a cor de primeiro plano do texto no painel de resultados no Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="60339-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="60339-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-200">OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="60339-201">Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.</span><span class="sxs-lookup"><span data-stu-id="60339-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="60339-202">Para versões posteriores, consulte [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="60339-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

 <span data-ttu-id="60339-203">A propriedade de leitura/escrita que altera a cor de fundo do texto no painel de resultados.</span><span class="sxs-lookup"><span data-stu-id="60339-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="60339-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-204">ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="60339-205">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-206">A propriedade de leitura/escrita que obtém ou define a cor de fundo para os ficheiros.</span><span class="sxs-lookup"><span data-stu-id="60339-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="60339-207">É uma instância do **System.Windows.Media.Color** classe.</span><span class="sxs-lookup"><span data-stu-id="60339-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'

```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="60339-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-208">ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="60339-209">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-210">A propriedade de leitura/escrita que obtém ou define a cor de primeiro plano para ficheiros de script não no painel de Script.</span><span class="sxs-lookup"><span data-stu-id="60339-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="60339-211">Para definir a cor de primeiro plano para ficheiros de script, utilize o [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="60339-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="60339-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="60339-212">SelectedScriptPaneState</span></span>
  <span data-ttu-id="60339-213">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-214">A propriedade de leitura/escrita que obtém ou define a posição do painel de Script no ecrã do.</span><span class="sxs-lookup"><span data-stu-id="60339-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="60339-215">A cadeia pode ser "Maximizado", "Top" ou "Direito".</span><span class="sxs-lookup"><span data-stu-id="60339-215">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

### <a name="showdefaultsnippets"></a><span data-ttu-id="60339-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="60339-216">ShowDefaultSnippets</span></span>
  <span data-ttu-id="60339-217">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-218">Especifica se o **CTRL + J** lista de fragmentos inclui o conjunto de arranque que está incluído no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60339-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="60339-219">Quando definido como **$false**, apenas os fragmentos definido pelo utilizador são apresentados no **CTRL + J** lista.</span><span class="sxs-lookup"><span data-stu-id="60339-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="60339-220">O valor predefinido é **$true**.</span><span class="sxs-lookup"><span data-stu-id="60339-220">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="60339-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="60339-221">ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="60339-222">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-223">Especifica se o IntelliSense oferece sintaxe, parâmetros e sugestões de valor no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="60339-224">O valor predefinido é **$true**.</span><span class="sxs-lookup"><span data-stu-id="60339-224">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="60339-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="60339-225">ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="60339-226">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-227">Especifica se o IntelliSense oferece sintaxe, parâmetros e sugestões de valor no painel de Script.</span><span class="sxs-lookup"><span data-stu-id="60339-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="60339-228">O valor predefinido é **$true**.</span><span class="sxs-lookup"><span data-stu-id="60339-228">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="60339-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="60339-229">ShowLineNumbers</span></span>
  <span data-ttu-id="60339-230">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-231">Especifica se o painel de Script apresenta números de linha na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="60339-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="60339-232">O valor predefinido é **$true**.</span><span class="sxs-lookup"><span data-stu-id="60339-232">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="60339-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="60339-233">ShowOutlining</span></span>
  <span data-ttu-id="60339-234">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-235">Especifica se o painel de Script apresenta Retos expansíveis e expansíveis junto de secções de código na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="60339-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="60339-236">Quando estes são apresentados, pode clicar no sinal de subtração \( - \) ícones junto de um bloco de texto para fechá-lo ou clique no sinal de adição \( + \) ícone para expandir um bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="60339-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="60339-237">O valor predefinido é **$true**.</span><span class="sxs-lookup"><span data-stu-id="60339-237">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="60339-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="60339-238">ShowToolBar</span></span>
  <span data-ttu-id="60339-239">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-240">Especifica se a barra de ferramentas ISE aparece na parte superior da janela ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60339-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="60339-241">O valor predefinido é **$true**.</span><span class="sxs-lookup"><span data-stu-id="60339-241">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="60339-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="60339-242">ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="60339-243">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-244">Especifica se é apresentada uma mensagem de aviso quando um script é guardado automaticamente antes de ser executada.</span><span class="sxs-lookup"><span data-stu-id="60339-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="60339-245">O valor predefinido é **$true**.</span><span class="sxs-lookup"><span data-stu-id="60339-245">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="60339-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="60339-246">ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="60339-247">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-248">Especifica se é apresentada uma mensagem de aviso quando o mesmo ficheiro é aberto na diferentes separadores do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60339-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="60339-249">Se definido como **$true**, para abrir o mesmo ficheiro nos vários separadores apresenta esta mensagem: "uma cópia deste ficheiro se encontra aberta noutro separador do Windows PowerShell. As alterações efetuadas a este ficheiro irão afetar copia todos os abrir."</span><span class="sxs-lookup"><span data-stu-id="60339-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="60339-250">O valor predefinido é **$true**.</span><span class="sxs-lookup"><span data-stu-id="60339-250">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

### <a name="tokencolors"></a><span data-ttu-id="60339-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="60339-251">TokenColors</span></span>
  <span data-ttu-id="60339-252">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-253">Especifica as cores dos IntelliSense tokens no painel de Script do Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="60339-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="60339-254">Esta propriedade é um objeto de dicionário que contém os pares nome/valor de tipos de tokens e de cores para o painel de Script.</span><span class="sxs-lookup"><span data-stu-id="60339-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="60339-255">Para alterar as cores dos tokens de IntelliSense, no painel de consola, consulte [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="60339-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="60339-256">Para repor as cores para os valores predefinidos, consulte [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="60339-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="60339-257">Cores token podem ser definidas para o seguinte: atributo, comando, CommandArgument, CommandParameter, comentário, GroupEnd, GroupStart, palavra-chave, LineContinuation, LoopLabel, membro, uma nova linha, número, operador, posição, StatementSeparator, cadeia, tipo, Desconhecido, a variável.</span><span class="sxs-lookup"><span data-stu-id="60339-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="60339-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="60339-258">UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="60339-259">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-260">Especifica se pode utilizar a tecla Enter para selecionar um IntelliSense fornecido opção no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="60339-261">O valor predefinido é **$true**.</span><span class="sxs-lookup"><span data-stu-id="60339-261">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="60339-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="60339-262">UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="60339-263">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-264">Especifica se pode utilizar a tecla Enter para selecionar uma opção IntelliSense fornecidos no painel de Script.</span><span class="sxs-lookup"><span data-stu-id="60339-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="60339-265">O valor predefinido é **$true**.</span><span class="sxs-lookup"><span data-stu-id="60339-265">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

### <a name="uselocalhelp"></a><span data-ttu-id="60339-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="60339-266">UseLocalHelp</span></span>
  <span data-ttu-id="60339-267">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-268">Especifica se a ajuda instalada localmente ou ajuda Biblioteca TechNet online é apresentada quando prime F1 com o cursor posicionado numa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="60339-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="60339-269">Se definido como **$true**, em seguida, uma janela de pop-up mostra conteúda de ajuda do instalada localmente.</span><span class="sxs-lookup"><span data-stu-id="60339-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="60339-270">Pode instalar os ficheiros de ajuda, executando o `Update-Help` comando.</span><span class="sxs-lookup"><span data-stu-id="60339-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="60339-271">Se definido como **$false**, em seguida, o browser abre-se a uma página na Biblioteca TechNet.</span><span class="sxs-lookup"><span data-stu-id="60339-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="60339-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-272">VerboseBackgroundColor</span></span>
  <span data-ttu-id="60339-273">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-274">Especifica a cor de fundo para verboso texto que aparece no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="60339-275">É um **System.Windows.Media.Color** objeto.</span><span class="sxs-lookup"><span data-stu-id="60339-275">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="60339-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-276">VerboseForegroundColor</span></span>
  <span data-ttu-id="60339-277">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-278">Especifica a cor de primeiro plano para verboso texto que aparece no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="60339-279">É um **System.Windows.Media.Color** objeto.</span><span class="sxs-lookup"><span data-stu-id="60339-279">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor ='yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="60339-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-280">WarningBackgroundColor</span></span>
  <span data-ttu-id="60339-281">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-282">Especifica a cor de fundo de texto de aviso que aparece no painel de consola.</span><span class="sxs-lookup"><span data-stu-id="60339-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="60339-283">É um **System.Windows.Media.Color** objeto.</span><span class="sxs-lookup"><span data-stu-id="60339-283">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="60339-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="60339-284">WarningForegroundColor</span></span>
  <span data-ttu-id="60339-285">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="60339-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="60339-286">Especifica a cor de primeiro plano para texto de aviso que aparece no painel de resultados.</span><span class="sxs-lookup"><span data-stu-id="60339-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="60339-287">É um **System.Windows.Media.Color** objeto.</span><span class="sxs-lookup"><span data-stu-id="60339-287">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor ='yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="60339-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="60339-288">XmlTokenColors</span></span>
  <span data-ttu-id="60339-289">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-290">Especifica um objeto de dicionário que contém os pares nome/valor de tipos de tokens e de cores para o conteúdo XML que é apresentado no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60339-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="60339-291">Cores token podem ser definidas para o seguinte: atributo, comando, CommandArgument, CommandParameter, comentário, GroupEnd, GroupStart, palavra-chave, LineContinuation, LoopLabel, membro, uma nova linha, número, operador, posição, StatementSeparator, cadeia, tipo, Desconhecido, a variável.</span><span class="sxs-lookup"><span data-stu-id="60339-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="60339-292">Consulte também [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="60339-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

### <a name="zoom"></a><span data-ttu-id="60339-293">Zoom</span><span class="sxs-lookup"><span data-stu-id="60339-293">Zoom</span></span>
  <span data-ttu-id="60339-294">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="60339-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="60339-295">Especifica o tamanho relativo de texto em painéis da consola e o Script.</span><span class="sxs-lookup"><span data-stu-id="60339-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="60339-296">O valor predefinido é 100.</span><span class="sxs-lookup"><span data-stu-id="60339-296">The default value is 100.</span></span> <span data-ttu-id="60339-297">Os valores mais pequenos fazer com que o texto no ISE do Windows PowerShell apareça mais pequenos enquanto maiores números causam texto apareça maior.</span><span class="sxs-lookup"><span data-stu-id="60339-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="60339-298">O valor é um número inteiro que intervalos de 20 para 400.</span><span class="sxs-lookup"><span data-stu-id="60339-298">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="60339-299">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="60339-299">See Also</span></span>
- [<span data-ttu-id="60339-300">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="60339-300">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="60339-301">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="60339-301">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

