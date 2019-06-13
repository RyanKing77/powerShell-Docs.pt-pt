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
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="26b06-103">Objeto ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="26b06-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="26b06-104">Uma **ISEMenuItemCollection** objeto é uma coleção de **ISEMenuItem** objetos.</span><span class="sxs-lookup"><span data-stu-id="26b06-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="26b06-105">É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="26b06-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="26b06-106">Um exemplo é o **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** objeto que é usado para personalizar o **suplemento** menu no Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="26b06-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="26b06-107">Método</span><span class="sxs-lookup"><span data-stu-id="26b06-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="26b06-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="26b06-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="26b06-109">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="26b06-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="26b06-110">Adiciona um item de menu à coleção.</span><span class="sxs-lookup"><span data-stu-id="26b06-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="26b06-111">**DisplayName** o nome a apresentar do menu a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="26b06-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="26b06-112">**Ação** a **System.Management.Automation.ScriptBlock** objeto que especifica a ação que está associada este item de menu.</span><span class="sxs-lookup"><span data-stu-id="26b06-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="26b06-113">**Atalho** o atalho de teclado para a ação.</span><span class="sxs-lookup"><span data-stu-id="26b06-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="26b06-114">**Devolve** ISEMenuItem o objeto que acabou de ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="26b06-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="26b06-115">Limpar\(\)</span><span class="sxs-lookup"><span data-stu-id="26b06-115">Clear\(\)</span></span>

<span data-ttu-id="26b06-116">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="26b06-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="26b06-117">Remove todos os submenus do item de menu.</span><span class="sxs-lookup"><span data-stu-id="26b06-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="26b06-118">Veja Também</span><span class="sxs-lookup"><span data-stu-id="26b06-118">See Also</span></span>

- [<span data-ttu-id="26b06-119">Objeto ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="26b06-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="26b06-120">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="26b06-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="26b06-121">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="26b06-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
