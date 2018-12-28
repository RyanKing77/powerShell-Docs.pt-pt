---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405530"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="f2397-103">Objeto ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="f2397-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="f2397-104">Uma **ISEMenuItem** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="f2397-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="f2397-105">Todos os objetos de menu no **suplementos** menu são instâncias da **Microsoft.PowerShell.Host.ISE.ISEMenuItem** classe.</span><span class="sxs-lookup"><span data-stu-id="f2397-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="f2397-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f2397-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="f2397-107">NomeaApresentar</span><span class="sxs-lookup"><span data-stu-id="f2397-107">DisplayName</span></span>

<span data-ttu-id="f2397-108">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="f2397-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f2397-109">A propriedade só de leitura que obtém o nome a apresentar do item de menu.</span><span class="sxs-lookup"><span data-stu-id="f2397-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="f2397-110">Ação</span><span class="sxs-lookup"><span data-stu-id="f2397-110">Action</span></span>

<span data-ttu-id="f2397-111">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="f2397-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f2397-112">A propriedade só de leitura que obtém o bloco de script.</span><span class="sxs-lookup"><span data-stu-id="f2397-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="f2397-113">Invoca a ação quando clica o item de menu.</span><span class="sxs-lookup"><span data-stu-id="f2397-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="f2397-114">Atalho</span><span class="sxs-lookup"><span data-stu-id="f2397-114">Shortcut</span></span>

<span data-ttu-id="f2397-115">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="f2397-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f2397-116">A propriedade só de leitura que obtém o Windows o atalho de teclado para o item de menu de entrada.</span><span class="sxs-lookup"><span data-stu-id="f2397-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="f2397-117">Submenus</span><span class="sxs-lookup"><span data-stu-id="f2397-117">Submenus</span></span>

<span data-ttu-id="f2397-118">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="f2397-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f2397-119">A propriedade só de leitura que obtém a [lista de submenus](The-ISEMenuItemCollection-Object.md) do item de menu.</span><span class="sxs-lookup"><span data-stu-id="f2397-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="f2397-120">Exemplo de script</span><span class="sxs-lookup"><span data-stu-id="f2397-120">Scripting example</span></span>

<span data-ttu-id="f2397-121">Para compreender melhor o uso de menu de suplementos e as respetivas propriedades programável por script, leia o seguinte exemplo de script.</span><span class="sxs-lookup"><span data-stu-id="f2397-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="f2397-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f2397-122">See Also</span></span>

- [<span data-ttu-id="f2397-123">Objeto ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="f2397-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="f2397-124">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="f2397-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f2397-125">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="f2397-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)