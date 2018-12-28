---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405406"
---
# <a name="the-isemenuitemcollection-object"></a>Objeto ISEMenuItemCollection

Uma **ISEMenuItemCollection** objeto é uma coleção de **ISEMenuItem** objetos. É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Um exemplo é o **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** objeto que é usado para personalizar o **suplemento** menu no Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Método

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Adicionar\(DisplayName, ação System.Management.Automation.ScriptBlock, System.Windows.Input.KeyGesture atalho de cadeias de caracteres \)

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

## <a name="see-also"></a>Consulte Também

- [Objeto ISEMenuItem](The-ISEMenuItem-Object.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)