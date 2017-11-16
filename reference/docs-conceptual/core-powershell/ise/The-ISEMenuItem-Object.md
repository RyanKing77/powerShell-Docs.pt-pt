---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 5561955040e56110a6af0619c286548f5812fb47
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="the-isemenuitem-object"></a>O objeto de ISEMenuItem
  Um **ISEMenuItem** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItem. Todos os objetos de menu no **suplementos** menu são instâncias do **Microsoft.PowerShell.Host.ISE.ISEMenuItem** classe.

## <a name="properties"></a>Propriedades

### <a name="displayname"></a>NomeaApresentar
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém o nome a apresentar do item de menu.

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

### <a name="action"></a>Ação
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém o bloco de script. Invoca a ação de quando clica com o item de menu.

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Atalho
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém as janelas de entrada do atalho de teclado para o item de menu.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Submenus
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 A propriedade só de leitura que obtém a [lista dos submenus](The-ISEMenuItemCollection-Object.md) do item de menu.

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Exemplo de script
 Para compreender melhor a utilização do menu de suplementos e as respetivas propriedades passível de ter scripts, leia o seguinte exemplo de script.

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a>Consulte Também
- [O objeto de ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) 
- [O ISE do Windows PowerShell modelo de objeto de Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [A hierarquia de modelo de objeto ISE](The-ISE-Object-Model-Hierarchy.md)
