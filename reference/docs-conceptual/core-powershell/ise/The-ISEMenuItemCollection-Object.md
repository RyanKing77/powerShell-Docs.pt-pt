---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954709"
---
# <a name="the-isemenuitemcollection-object"></a>Objeto ISEMenuItemCollection

Um **ISEMenuItemCollection** objeto é uma coleção de **ISEMenuItem** objetos. É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Um exemplo é o **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** objeto que é utilizado para personalizar o **suplemento** menu no Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Método

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Adicionar\(DisplayName, System.Management.Automation.ScriptBlock ação, System.Windows.Input.KeyGesture atalho de cadeia \)

Suportado no Windows PowerShell ISE 2.0 e posterior.

Adiciona um item de menu à coleção.

**DisplayName** o nome a apresentar do menu Adicionar.

**Ação** o **System.Management.Automation.ScriptBlock** objeto que especifica a ação que está associada este item de menu.

**Atalho** o atalho do teclado para a ação.

**Devolve** ISEMenuItem o objeto que acabou de ser adicionado.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Limpar\(\)

Suportado no Windows PowerShell ISE 2.0 e posterior.

Remove todos os submenus o item de menu.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Consulte Também

- [O objeto de ISEMenuItem](The-ISEMenuItem-Object.md)
- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)