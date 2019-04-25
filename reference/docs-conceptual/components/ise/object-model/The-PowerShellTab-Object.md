---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 577e2aaaddf3071801816d9ae91dbf0006dd5072
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057677"
---
# <a name="the-powershelltab-object"></a>Objeto PowerShellTab

O **PowerShellTab** objeto representa um ambiente de tempo de execução do Windows PowerShell.

## <a name="methods"></a>Métodos

### <a name="invoke-script-"></a>Invoke\( Script \)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Executa o script fornecido no separador do PowerShell.

> [!NOTE]
> Este método só funciona nos outros separadores de PowerShell, não o separador do PowerShell do qual é executado. Não devolve qualquer objeto de valor. Se o código modifica qualquer variável, essas alterações sejam mantidas na guia em relação ao qual o comando foi chamado.

**Script** -System.Management.Automation.ScriptBlock ou cadeia de caracteres o bloco de script para executar.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

Executa o script fornecido no separador do PowerShell.

> [!NOTE]
> Este método só funciona nos outros separadores de PowerShell, não o separador do PowerShell do qual é executado. O bloco de script é executado e qualquer valor que é devolvido do script é retornado para o ambiente de execução do qual invocou o comando. Se o comando demora mais tempo a execute mais do que o **millesecondsTimeout** valor Especifica, em seguida, o comando falha com uma exceção: "A operação foi excedido."

**Script** -System.Management.Automation.ScriptBlock ou cadeia de caracteres o bloco de script para executar.

**\[useNewScope\]**  -opcional booleano que, por padrão **$true** se definido como **$true**, em seguida, um novo âmbito é criado dentro do qual pretende executar o comando. Não modifica o ambiente de tempo de execução do separador do PowerShell especificado pelo comando.

**\[millisecondsTimeout\]**  -inteiro opcional que, por padrão **500**.
Se o comando não for concluída dentro do tempo especificado, o comando gera um **TimeoutException** com a mensagem "a operação foi excedido."

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

## <a name="properties"></a>Propriedades

### <a name="addonsmenu"></a>AddOnsMenu

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém o menu de complementos para o separador do PowerShell.

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

### <a name="caninvoke"></a>CanInvoke

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade booleana só de leitura que retorna um **$true** valor se um script pode ser invocado com o [Invoke (Script)](#invoke-script-) método.

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

### <a name="consolepane"></a>Consolepane

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.  No Windows PowerShell ISE 2.0 isso era chamado **CommandPane**.

A propriedade só de leitura que obtém o painel de consola [editor](The-ISEEditor-Object.md) objeto.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>DisplayName

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade de leitura / escrita que obtém ou define o texto que é apresentado no separador do PowerShell. Por predefinição, os separadores são denominados "PowerShell #", onde o n. º representa um número.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

O leitura e escrita propriedade booleana que determina se o painel de scripts é expandido ou oculto.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Ficheiros

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém a [coleção de arquivos de script](The-ISEFileCollection-Object.md) que estão abertas no separador do PowerShell.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Saída

Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudada em versões posteriores do ISE.  Nas versões posteriores do ISE do Windows PowerShell, pode utilizar o **ConsolePane** objeto destinada à mesma.

A propriedade só de leitura que obtém o painel de resultados de atual [editor](The-ISEEditor-Object.md).

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Linha de comandos

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém o texto de linha de comandos atual. Nota: os **Prompt** função pode ser substituída pelo utilizador '™ perfil s. Se o resultado é que não seja uma cadeia de caracteres simples, em seguida, essa propriedade retorna nada.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

A propriedade de leitura / escrita que indica se o painel de comandos é atualmente apresentado.

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>StatusText

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

A propriedade só de leitura que obtém a **PowerShellTab** texto do Estado.

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

A propriedade só de leitura que indica se o painel de ferramentas de suplementos horizontal é atualmente aberto.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

A propriedade só de leitura que indica se o painel de ferramentas de suplementos vertical é atualmente aberto.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Veja Também

- [Objeto PowerShellTabCollection](The-PowerShellTabCollection-Object.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)