---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEMenuItemCollection
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030534"
---
# <a name="the-isemenuitemcollection-object"></a>Objeto ISEMenuItemCollection

Uma **ISEMenuItemCollection** objeto é uma coleção de **ISEMenuItem** objetos. É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Um exemplo é o **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** objeto que é usado para personalizar o **suplemento** menu no Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Método

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Adiciona um item de menu à coleção.

**DisplayName** o nome a apresentar do menu a ser adicionado.

**Ação** a **System.Management.Automation.ScriptBlock** objeto que especifica a ação que está associada este item de menu.

**Atalho** o atalho de teclado para a ação.

**Devolve** ISEMenuItem o objeto que acabou de ser adicionado.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Limpar\(\)

Suportado no Windows PowerShell ISE 2.0 e versões posteriores.

Remove todos os submenus do item de menu.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Veja Também

- [Objeto ISEMenuItem](The-ISEMenuItem-Object.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)
