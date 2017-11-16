---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ba8b4e0e3952226407f00dea8b32785633256089
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="fc6b5-103">O objeto de ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="fc6b5-103">The ISEAddOnToolCollection Object</span></span>
  <span data-ttu-id="fc6b5-104">O **ISEAddOnToolCollection** objeto é uma coleção de **ISEAddOnTool** objetos.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="fc6b5-105">Um exemplo é o **$psISE.CurrentPowerShellTab.VerticalAddOnTools** objeto.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="fc6b5-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="fc6b5-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="fc6b5-107">Adicionar\( nome, ControlType, \[IsVisible\]\)</span><span class="sxs-lookup"><span data-stu-id="fc6b5-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>
  <span data-ttu-id="fc6b5-108">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="fc6b5-109">Adiciona uma nova ferramenta de suplemento à coleção.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="fc6b5-110">Devolve a ferramenta de suplemento adicionados recentemente.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="fc6b5-111">Antes de executar este comando, tem de instalar a ferramenta de suplemento no computador local e carregar a assemblagem.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

 <span data-ttu-id="fc6b5-112">**Nome** -cadeia Especifica o nome a apresentar da ferramenta de suplemento que é adicionado ao ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

 <span data-ttu-id="fc6b5-113">**ControlType** -tipo Especifica o controlo é adicionado.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-113">**ControlType** -Type Specifies the control that is added.</span></span>

 <span data-ttu-id="fc6b5-114">**\[IsVisible\]**  -opcional booleano se definido como **$true**, a ferramenta de suplemento é imediatamente visível no painel de ferramenta associado.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="fc6b5-115">Remover\( Item\)</span><span class="sxs-lookup"><span data-stu-id="fc6b5-115">Remove\( Item \)</span></span>
  <span data-ttu-id="fc6b5-116">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="fc6b5-117">Remove a ferramenta de suplemento especificado da coleção.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-117">Removes the specified add-on tool from the collection.</span></span>

 <span data-ttu-id="fc6b5-118">**Item** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Especifica o objeto a ser removido do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="fc6b5-119">SetSelectedPowerShellTab\( psTab\)</span><span class="sxs-lookup"><span data-stu-id="fc6b5-119">SetSelectedPowerShellTab\( psTab \)</span></span>
  <span data-ttu-id="fc6b5-120">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="fc6b5-121">Seleciona o PowerShell separador que o **psTab** parâmetro especifica.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="fc6b5-122">**psTab** -separador de PowerShell o Microsoft.PowerShell.Host.ISE.PowerShellTab para selecionar.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="remove-pstab-"></a><span data-ttu-id="fc6b5-123">Remover\( psTab\)</span><span class="sxs-lookup"><span data-stu-id="fc6b5-123">Remove\( psTab \)</span></span>
  <span data-ttu-id="fc6b5-124">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="fc6b5-125">Remove o PowerShell separador que o **psTab** parâmetro especifica.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="fc6b5-126">**psTab** -separador de PowerShell Microsoft.PowerShell.Host.ISE.PowerShellTab do remover.</span><span class="sxs-lookup"><span data-stu-id="fc6b5-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="fc6b5-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="fc6b5-127">See Also</span></span>
- [<span data-ttu-id="fc6b5-128">O objeto de PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="fc6b5-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="fc6b5-129">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="fc6b5-129">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="fc6b5-130">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="fc6b5-130">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="fc6b5-131">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="fc6b5-131">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
