---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="the-isemenuitemcollection-object"></a>O objeto de ISEMenuItemCollection
  Um **ISEMenuItemCollection** objeto é uma coleção de **ISEMenuItem** objetos. É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Um exemplo é o **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** objeto que é utilizado para personalizar o **suplemento** menu no Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Método

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Adicionar\(DisplayName, System.Management.Automation.ScriptBlock ação, System.Windows.Input.KeyGesture atalho de cadeia\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Adiciona um item de menu à coleção.

 **DisplayName** o nome a apresentar do menu Adicionar.

 **Ação** o **System.Management.Automation.ScriptBlock** objeto que especifica a ação que está associada este item de menu.

 **Atalho** o atalho do teclado para a ação.

 **Devolve** ISEMenuItem o objeto que acabou de ser adicionado.

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a>Limpar\(\)
  Suportado no Windows PowerShell ISE 2.0 e posterior. 

 Remove todos os submenus o item de menu.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>Consulte Também
- [O objeto de ISEMenuItem](The-ISEMenuItem-Object.md) 
- [O ISE do Windows PowerShell modelo de objeto de Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto ISE](The-ISE-Object-Model-Hierarchy.md)

  
