---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 15d9a7474e4c2cf2a9ff8edb88802106489cdba1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="the-powershelltab-object"></a>O objeto de PowerShellTab
  O **PowerShellTab** objeto representa um ambiente de tempo de execução do Windows PowerShell.

## <a name="methods"></a>Métodos

### <a name="invoke-script-"></a>Invocar\( Script\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Executa o script especificado no separador do PowerShell.

> [!NOTE]
> Este método só funciona nos outros separadores de PowerShell, não o separador de PowerShell partir da qual é executado. Não devolver qualquer objeto de valor. Se o código modifica qualquer variável, em seguida, essas alterações sejam mantidas no separador relativamente ao qual o comando foi invocado.

 **Script** -System.Management.Automation.ScriptBlock ou cadeia o bloco de script para executar.

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout\)
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 Executa o script especificado no separador do PowerShell.

> [!NOTE]
> Este método só funciona nos outros separadores de PowerShell, não o separador de PowerShell partir da qual é executado. O bloco de script é executado e qualquer valor que é devolvido a partir do script é devolvido ao ambiente de execução a partir do qual é invocado o comando. Se o comando demora mais tempo a executar que o **millesecondsTimeout** valor Especifica, em seguida, o comando falha com uma exceção: "a operação foi excedido."

 **Script** -System.Management.Automation.ScriptBlock ou cadeia o bloco de script para executar.

 **\[useNewScope\]**  -opcional booleano que assume a predefinição **$true** se definido como **$true**, em seguida, é criado um novo âmbito no qual executar o comando. Não modifica o ambiente de tempo de execução do separador do PowerShell que é especificado pelo comando.

 **\[millisecondsTimeout\]**  -opcional número inteiro que assume a predefinição **500**.
Se o comando não for concluída dentro do período de tempo especificado, em seguida, o comando gera um **TimeoutException** com a mensagem "a operação foi excedido."

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type 'œ$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a>Propriedades

### <a name="addonsmenu"></a>AddOnsMenu
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém o menu de suplementos para o separador do PowerShell.

```
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a>CanInvoke
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade booleana só de leitura que devolva uma **$true** valor se um script pode ser invocado com o [Invoke (Script)](#invoke-script-) método.

```
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab. 
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psise.PowerShellTabs[1] 
$secondTab.CanInvoke 
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke

```

### <a name="consolepane"></a>Consolepane
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.  No Windows PowerShell ISE 2.0 Isto foi atribuído o nome **CommandPane**.

 A propriedade só de leitura que obtém o painel de consola [editor](../ise/The-ISEEditor-Object.md) objeto.

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

### <a name="displayname"></a>NomeaApresentar
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade de leitura e escrita que obtém ou define o texto que é apresentado no separador do PowerShell. Por predefinição, os separadores são denominados "PowerShell #", onde o n. º representa um número.

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="expandedscript"></a>ExpandedScript
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A leitura e escrita propriedade booleana que determina se o painel de Script está expandido ou oculto.

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

### <a name="files"></a>Ficheiros
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém a [recolha de ficheiros de script](../ise/The-ISEFileCollection-Object.md) que estão abertos no separador do PowerShell.

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Saída
  Esta funcionalidade está presente no Windows PowerShell ISE 2.0, mas foi removida ou mudar o nome em versões posteriores do ISE do.  Em versões posteriores do ISE do Windows PowerShell, pode utilizar o **ConsolePane** objetos para os mesmos efeitos.

 A propriedade só de leitura que obtém o painel de resultados de atual [editor](../ise/The-ISEEditor-Object.md).

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Linha de comandos
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém o texto da linha de comandos atual. Nota: o **Prompt** função pode ser substituída pelo utilizador '™ perfil s. Se o resultado é que não seja uma cadeia simple, em seguida, esta propriedade devolve nada.

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 A propriedade de leitura e escrita que indica se o painel de comandos é atualmente apresentado.

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

### <a name="statustext"></a>StatusText
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém a **PowerShellTab** texto de estado.

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 A propriedade só de leitura que indica se o painel de ferramentas de suplementos horizontal está atualmente aberto.

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened
  Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores. 

 A propriedade só de leitura que indica se o painel de ferramentas de suplementos vertical está atualmente aberto.

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Consulte Também
- [O objeto de PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 
- [O ISE do Windows PowerShell modelo de objeto de Scripting](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do Windows PowerShell ISE](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  
