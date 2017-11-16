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
# <a name="the-isemenuitem-object"></a><span data-ttu-id="75610-103">O objeto de ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="75610-103">The ISEMenuItem Object</span></span>
  <span data-ttu-id="75610-104">Um **ISEMenuItem** objeto é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="75610-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="75610-105">Todos os objetos de menu no **suplementos** menu são instâncias do **Microsoft.PowerShell.Host.ISE.ISEMenuItem** classe.</span><span class="sxs-lookup"><span data-stu-id="75610-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="75610-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="75610-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="75610-107">NomeaApresentar</span><span class="sxs-lookup"><span data-stu-id="75610-107">DisplayName</span></span>
  <span data-ttu-id="75610-108">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="75610-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="75610-109">A propriedade só de leitura que obtém o nome a apresentar do item de menu.</span><span class="sxs-lookup"><span data-stu-id="75610-109">The read-only property that gets the display name of the menu item.</span></span>

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

### <a name="action"></a><span data-ttu-id="75610-110">Ação</span><span class="sxs-lookup"><span data-stu-id="75610-110">Action</span></span>
  <span data-ttu-id="75610-111">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="75610-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="75610-112">A propriedade só de leitura que obtém o bloco de script.</span><span class="sxs-lookup"><span data-stu-id="75610-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="75610-113">Invoca a ação de quando clica com o item de menu.</span><span class="sxs-lookup"><span data-stu-id="75610-113">It invokes the action when you click the menu item.</span></span>

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="75610-114">Atalho</span><span class="sxs-lookup"><span data-stu-id="75610-114">Shortcut</span></span>
  <span data-ttu-id="75610-115">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="75610-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="75610-116">A propriedade só de leitura que obtém as janelas de entrada do atalho de teclado para o item de menu.</span><span class="sxs-lookup"><span data-stu-id="75610-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="75610-117">Submenus</span><span class="sxs-lookup"><span data-stu-id="75610-117">Submenus</span></span>
  <span data-ttu-id="75610-118">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="75610-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="75610-119">A propriedade só de leitura que obtém a [lista dos submenus](The-ISEMenuItemCollection-Object.md) do item de menu.</span><span class="sxs-lookup"><span data-stu-id="75610-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="75610-120">Exemplo de script</span><span class="sxs-lookup"><span data-stu-id="75610-120">Scripting example</span></span>
 <span data-ttu-id="75610-121">Para compreender melhor a utilização do menu de suplementos e as respetivas propriedades passível de ter scripts, leia o seguinte exemplo de script.</span><span class="sxs-lookup"><span data-stu-id="75610-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="75610-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="75610-122">See Also</span></span>
- [<span data-ttu-id="75610-123">O objeto de ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="75610-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md) 
- [<span data-ttu-id="75610-124">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="75610-124">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="75610-125">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="75610-125">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="75610-126">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="75610-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
