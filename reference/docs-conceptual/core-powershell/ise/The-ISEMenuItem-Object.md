---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950714"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="860f8-103">Objeto ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="860f8-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="860f8-104">Um **ISEMenuItem** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="860f8-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="860f8-105">Todos os objetos de menu no **suplementos** menu são instâncias do **Microsoft.PowerShell.Host.ISE.ISEMenuItem** classe.</span><span class="sxs-lookup"><span data-stu-id="860f8-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="860f8-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="860f8-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="860f8-107">NomeaApresentar</span><span class="sxs-lookup"><span data-stu-id="860f8-107">DisplayName</span></span>

<span data-ttu-id="860f8-108">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="860f8-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="860f8-109">A propriedade só de leitura que obtém o nome a apresentar do item de menu.</span><span class="sxs-lookup"><span data-stu-id="860f8-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="860f8-110">Ação</span><span class="sxs-lookup"><span data-stu-id="860f8-110">Action</span></span>

<span data-ttu-id="860f8-111">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="860f8-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="860f8-112">A propriedade só de leitura que obtém o bloco de script.</span><span class="sxs-lookup"><span data-stu-id="860f8-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="860f8-113">Invoca a ação de quando clica com o item de menu.</span><span class="sxs-lookup"><span data-stu-id="860f8-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="860f8-114">Atalho</span><span class="sxs-lookup"><span data-stu-id="860f8-114">Shortcut</span></span>

<span data-ttu-id="860f8-115">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="860f8-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="860f8-116">A propriedade só de leitura que obtém as janelas de entrada do atalho de teclado para o item de menu.</span><span class="sxs-lookup"><span data-stu-id="860f8-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="860f8-117">Submenus</span><span class="sxs-lookup"><span data-stu-id="860f8-117">Submenus</span></span>

<span data-ttu-id="860f8-118">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="860f8-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="860f8-119">A propriedade só de leitura que obtém a [lista dos submenus](The-ISEMenuItemCollection-Object.md) do item de menu.</span><span class="sxs-lookup"><span data-stu-id="860f8-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="860f8-120">Exemplo de script</span><span class="sxs-lookup"><span data-stu-id="860f8-120">Scripting example</span></span>

<span data-ttu-id="860f8-121">Para compreender melhor a utilização do menu de suplementos e as respetivas propriedades passível de ter scripts, leia o seguinte exemplo de script.</span><span class="sxs-lookup"><span data-stu-id="860f8-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="860f8-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="860f8-122">See Also</span></span>

- [<span data-ttu-id="860f8-123">O objeto de ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="860f8-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="860f8-124">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="860f8-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="860f8-125">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="860f8-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)