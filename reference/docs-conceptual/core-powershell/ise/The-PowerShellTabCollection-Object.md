---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="bb56c-103">Objeto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="bb56c-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="bb56c-104">O **PowerShellTab** objeto da coleção é uma coleção de **PowerShellTab** objetos.</span><span class="sxs-lookup"><span data-stu-id="bb56c-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="bb56c-105">Cada **PowerShellTab** objeto funciona como um ambiente de tempo de execução separado.</span><span class="sxs-lookup"><span data-stu-id="bb56c-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="bb56c-106">É uma instância da classe de Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="bb56c-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="bb56c-107">Um exemplo é o **$psISE.PowerShellTabs** objeto.</span><span class="sxs-lookup"><span data-stu-id="bb56c-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="bb56c-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="bb56c-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="bb56c-109">Adicionar\(\)</span><span class="sxs-lookup"><span data-stu-id="bb56c-109">Add\(\)</span></span>

<span data-ttu-id="bb56c-110">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="bb56c-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bb56c-111">Adiciona um novo separador do PowerShell para a coleção.</span><span class="sxs-lookup"><span data-stu-id="bb56c-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="bb56c-112">Devolve o separador adicionado recentemente.</span><span class="sxs-lookup"><span data-stu-id="bb56c-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="bb56c-113">Remover\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="bb56c-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="bb56c-114">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="bb56c-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bb56c-115">Remove o separador que é especificado pelo **psTab** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bb56c-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="bb56c-116">**psTab** separador o PowerShell para remover.</span><span class="sxs-lookup"><span data-stu-id="bb56c-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="bb56c-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="bb56c-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="bb56c-118">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="bb56c-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bb56c-119">Seleciona o separador do PowerShell que é especificado pelo **psTab** parâmetro para torná-lo no separador de PowerShell atualmente ativo.</span><span class="sxs-lookup"><span data-stu-id="bb56c-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="bb56c-120">**psTab** PowerShell o separador para selecionar.</span><span class="sxs-lookup"><span data-stu-id="bb56c-120">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="bb56c-121">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="bb56c-121">See Also</span></span>

- [<span data-ttu-id="bb56c-122">O objeto de PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="bb56c-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="bb56c-123">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="bb56c-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="bb56c-124">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="bb56c-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)