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
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="c40f2-103">Objeto ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="c40f2-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="c40f2-104">Um **ISEMenuItemCollection** objeto é uma coleção de **ISEMenuItem** objetos.</span><span class="sxs-lookup"><span data-stu-id="c40f2-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="c40f2-105">É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="c40f2-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="c40f2-106">Um exemplo é o **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** objeto que é utilizado para personalizar o **suplemento** menu no Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="c40f2-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="c40f2-107">Método</span><span class="sxs-lookup"><span data-stu-id="c40f2-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="c40f2-108">Adicionar\(DisplayName, System.Management.Automation.ScriptBlock ação, System.Windows.Input.KeyGesture atalho de cadeia \)</span><span class="sxs-lookup"><span data-stu-id="c40f2-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="c40f2-109">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c40f2-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c40f2-110">Adiciona um item de menu à coleção.</span><span class="sxs-lookup"><span data-stu-id="c40f2-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="c40f2-111">**DisplayName** o nome a apresentar do menu Adicionar.</span><span class="sxs-lookup"><span data-stu-id="c40f2-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="c40f2-112">**Ação** o **System.Management.Automation.ScriptBlock** objeto que especifica a ação que está associada este item de menu.</span><span class="sxs-lookup"><span data-stu-id="c40f2-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="c40f2-113">**Atalho** o atalho do teclado para a ação.</span><span class="sxs-lookup"><span data-stu-id="c40f2-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="c40f2-114">**Devolve** ISEMenuItem o objeto que acabou de ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="c40f2-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="c40f2-115">Limpar\(\)</span><span class="sxs-lookup"><span data-stu-id="c40f2-115">Clear\(\)</span></span>

<span data-ttu-id="c40f2-116">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c40f2-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c40f2-117">Remove todos os submenus o item de menu.</span><span class="sxs-lookup"><span data-stu-id="c40f2-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="c40f2-118">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c40f2-118">See Also</span></span>

- [<span data-ttu-id="c40f2-119">O objeto de ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="c40f2-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="c40f2-120">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="c40f2-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c40f2-121">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="c40f2-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)