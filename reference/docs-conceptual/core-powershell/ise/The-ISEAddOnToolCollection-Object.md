---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="f0262-103">Objeto ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="f0262-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="f0262-104">O **ISEAddOnToolCollection** objeto é uma coleção de **ISEAddOnTool** objetos.</span><span class="sxs-lookup"><span data-stu-id="f0262-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="f0262-105">Um exemplo é o **$psISE.CurrentPowerShellTab.VerticalAddOnTools** objeto.</span><span class="sxs-lookup"><span data-stu-id="f0262-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="f0262-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="f0262-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="f0262-107">Adicionar\( nome, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="f0262-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="f0262-108">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f0262-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f0262-109">Adiciona uma nova ferramenta de suplemento à coleção.</span><span class="sxs-lookup"><span data-stu-id="f0262-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="f0262-110">Devolve a ferramenta de suplemento adicionados recentemente.</span><span class="sxs-lookup"><span data-stu-id="f0262-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="f0262-111">Antes de executar este comando, tem de instalar a ferramenta de suplemento no computador local e carregar a assemblagem.</span><span class="sxs-lookup"><span data-stu-id="f0262-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="f0262-112">**Nome** -cadeia Especifica o nome a apresentar da ferramenta de suplemento que é adicionado ao ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0262-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="f0262-113">**ControlType** -tipo Especifica o controlo é adicionado.</span><span class="sxs-lookup"><span data-stu-id="f0262-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="f0262-114">**\[IsVisible\]**  -opcional booleano se definido como **$true**, a ferramenta de suplemento é imediatamente visível no painel de ferramenta associado.</span><span class="sxs-lookup"><span data-stu-id="f0262-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="f0262-115">Remover\( Item \)</span><span class="sxs-lookup"><span data-stu-id="f0262-115">Remove\( Item \)</span></span>

<span data-ttu-id="f0262-116">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f0262-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f0262-117">Remove a ferramenta de suplemento especificado da coleção.</span><span class="sxs-lookup"><span data-stu-id="f0262-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="f0262-118">**Item** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Especifica o objeto a ser removido do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0262-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="f0262-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="f0262-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="f0262-120">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f0262-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f0262-121">Seleciona o PowerShell separador que o **psTab** parâmetro especifica.</span><span class="sxs-lookup"><span data-stu-id="f0262-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="f0262-122">**psTab** -separador de PowerShell o Microsoft.PowerShell.Host.ISE.PowerShellTab para selecionar.</span><span class="sxs-lookup"><span data-stu-id="f0262-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="f0262-123">Remover\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="f0262-123">Remove\( psTab \)</span></span>

<span data-ttu-id="f0262-124">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f0262-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f0262-125">Remove o PowerShell separador que o **psTab** parâmetro especifica.</span><span class="sxs-lookup"><span data-stu-id="f0262-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="f0262-126">**psTab** -separador de PowerShell Microsoft.PowerShell.Host.ISE.PowerShellTab do remover.</span><span class="sxs-lookup"><span data-stu-id="f0262-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="f0262-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f0262-127">See Also</span></span>

- [<span data-ttu-id="f0262-128">O objeto de PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="f0262-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="f0262-129">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="f0262-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f0262-130">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="f0262-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)