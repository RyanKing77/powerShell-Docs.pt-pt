---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405397"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="4ab58-103">Objeto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="4ab58-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="4ab58-104">O **PowerShellTab** objeto da coleção é uma coleção de **PowerShellTab** objetos.</span><span class="sxs-lookup"><span data-stu-id="4ab58-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="4ab58-105">Cada **PowerShellTab** objeto funciona como um ambiente de tempo de execução separado.</span><span class="sxs-lookup"><span data-stu-id="4ab58-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="4ab58-106">É uma instância da classe Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="4ab58-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="4ab58-107">Um exemplo é o **$psISE.PowerShellTabs** objeto.</span><span class="sxs-lookup"><span data-stu-id="4ab58-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="4ab58-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="4ab58-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="4ab58-109">Adicionar\(\)</span><span class="sxs-lookup"><span data-stu-id="4ab58-109">Add\(\)</span></span>

<span data-ttu-id="4ab58-110">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ab58-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4ab58-111">Adiciona um novo separador do PowerShell para a coleção.</span><span class="sxs-lookup"><span data-stu-id="4ab58-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="4ab58-112">Ele retorna a guia recém-adicionada.</span><span class="sxs-lookup"><span data-stu-id="4ab58-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="4ab58-113">Remover\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="4ab58-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="4ab58-114">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ab58-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4ab58-115">Remove a guia especificada pelos **psTab** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4ab58-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="4ab58-116">**psTab** separador do PowerShell a remover.</span><span class="sxs-lookup"><span data-stu-id="4ab58-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="4ab58-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="4ab58-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="4ab58-118">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ab58-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4ab58-119">Seleciona o separador do PowerShell que é especificado pela **psTab** parâmetro para tornar o separador do PowerShell atualmente ativo.</span><span class="sxs-lookup"><span data-stu-id="4ab58-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="4ab58-120">**psTab** separador do PowerShell a selecionar.</span><span class="sxs-lookup"><span data-stu-id="4ab58-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4ab58-121">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="4ab58-121">See Also</span></span>

- [<span data-ttu-id="4ab58-122">Objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="4ab58-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="4ab58-123">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="4ab58-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="4ab58-124">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="4ab58-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)