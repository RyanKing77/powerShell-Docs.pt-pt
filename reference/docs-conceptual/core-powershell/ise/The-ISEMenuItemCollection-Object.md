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
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="40ef5-103">O objeto de ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="40ef5-103">The ISEMenuItemCollection Object</span></span>
  <span data-ttu-id="40ef5-104">Um **ISEMenuItemCollection** objeto é uma coleção de **ISEMenuItem** objetos.</span><span class="sxs-lookup"><span data-stu-id="40ef5-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="40ef5-105">É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="40ef5-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="40ef5-106">Um exemplo é o **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** objeto que é utilizado para personalizar o **suplemento** menu no Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="40ef5-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="40ef5-107">Método</span><span class="sxs-lookup"><span data-stu-id="40ef5-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="40ef5-108">Adicionar\(DisplayName, System.Management.Automation.ScriptBlock ação, System.Windows.Input.KeyGesture atalho de cadeia\)</span><span class="sxs-lookup"><span data-stu-id="40ef5-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>
  <span data-ttu-id="40ef5-109">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="40ef5-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="40ef5-110">Adiciona um item de menu à coleção.</span><span class="sxs-lookup"><span data-stu-id="40ef5-110">Adds a menu item to the collection.</span></span>

 <span data-ttu-id="40ef5-111">**DisplayName** o nome a apresentar do menu Adicionar.</span><span class="sxs-lookup"><span data-stu-id="40ef5-111">**DisplayName** The display name of the menu to be added.</span></span>

 <span data-ttu-id="40ef5-112">**Ação** o **System.Management.Automation.ScriptBlock** objeto que especifica a ação que está associada este item de menu.</span><span class="sxs-lookup"><span data-stu-id="40ef5-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

 <span data-ttu-id="40ef5-113">**Atalho** o atalho do teclado para a ação.</span><span class="sxs-lookup"><span data-stu-id="40ef5-113">**Shortcut** The keyboard shortcut for the action.</span></span>

 <span data-ttu-id="40ef5-114">**Devolve** ISEMenuItem o objeto que acabou de ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="40ef5-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a><span data-ttu-id="40ef5-115">Limpar\(\)</span><span class="sxs-lookup"><span data-stu-id="40ef5-115">Clear\(\)</span></span>
  <span data-ttu-id="40ef5-116">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="40ef5-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="40ef5-117">Remove todos os submenus o item de menu.</span><span class="sxs-lookup"><span data-stu-id="40ef5-117">Removes all submenus from the menu item.</span></span>

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a><span data-ttu-id="40ef5-118">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="40ef5-118">See Also</span></span>
- [<span data-ttu-id="40ef5-119">O objeto de ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="40ef5-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md) 
- [<span data-ttu-id="40ef5-120">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="40ef5-120">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="40ef5-121">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="40ef5-121">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="40ef5-122">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="40ef5-122">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
