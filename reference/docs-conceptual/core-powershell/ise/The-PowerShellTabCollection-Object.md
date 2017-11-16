---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="6e9cd-103">O objeto de PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="6e9cd-103">The PowerShellTabCollection Object</span></span>
  <span data-ttu-id="6e9cd-104">O **PowerShellTab** objeto da coleção é uma coleção de **PowerShellTab** objetos.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="6e9cd-105">Cada **PowerShellTab** objeto funciona como um ambiente de tempo de execução separado.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="6e9cd-106">É uma instância da classe de Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="6e9cd-107">Um exemplo é o **$psISE.PowerShellTabs** objeto.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="6e9cd-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="6e9cd-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="6e9cd-109">Adicionar\(\)</span><span class="sxs-lookup"><span data-stu-id="6e9cd-109">Add\(\)</span></span>
  <span data-ttu-id="6e9cd-110">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="6e9cd-111">Adiciona um novo separador do PowerShell para a coleção.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="6e9cd-112">Devolve o separador adicionado recentemente.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-112">It returns the newly added tab.</span></span>

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="6e9cd-113">Remover\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="6e9cd-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="6e9cd-114">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="6e9cd-115">Remove o separador que é especificado pelo **psTab** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

 <span data-ttu-id="6e9cd-116">**psTab** separador o PowerShell para remover.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-116">**psTab** The PowerShell tab to remove.</span></span>

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="6e9cd-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="6e9cd-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="6e9cd-118">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="6e9cd-119">Seleciona o separador do PowerShell que é especificado pelo **psTab** parâmetro para torná-lo no separador de PowerShell atualmente ativo.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

 <span data-ttu-id="6e9cd-120">**psTab** PowerShell o separador para selecionar.</span><span class="sxs-lookup"><span data-stu-id="6e9cd-120">**psTab** The PowerShell tab to select.</span></span>

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a><span data-ttu-id="6e9cd-121">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="6e9cd-121">See Also</span></span>
- [<span data-ttu-id="6e9cd-122">O objeto de PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="6e9cd-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="6e9cd-123">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="6e9cd-123">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="6e9cd-124">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="6e9cd-124">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="6e9cd-125">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="6e9cd-125">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
