---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEAddOnToolCollection
ms.openlocfilehash: 28ab9747e573b7a76ee655289b341870b1728bc2
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030619"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="f8a83-103">Objeto ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="f8a83-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="f8a83-104">O **ISEAddOnToolCollection** objeto é uma coleção de **ISEAddOnTool** objetos.</span><span class="sxs-lookup"><span data-stu-id="f8a83-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="f8a83-105">Um exemplo é o **$psISE.CurrentPowerShellTab.VerticalAddOnTools** objeto.</span><span class="sxs-lookup"><span data-stu-id="f8a83-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="f8a83-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="f8a83-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="f8a83-107">Add\( Name, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="f8a83-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="f8a83-108">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f8a83-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f8a83-109">Adiciona uma nova ferramenta do suplemento à coleção.</span><span class="sxs-lookup"><span data-stu-id="f8a83-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="f8a83-110">Devolve a ferramenta do suplemento recém-adicionada.</span><span class="sxs-lookup"><span data-stu-id="f8a83-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="f8a83-111">Antes de executar este comando, tem de instalar a ferramenta do suplemento no computador local e carregar a assemblagem.</span><span class="sxs-lookup"><span data-stu-id="f8a83-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="f8a83-112">**Nome** -cadeia de caracteres Especifica o nome a apresentar da ferramenta de suplemento que é adicionado ao ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f8a83-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="f8a83-113">**ControlType** -tipo Especifica o controle que é adicionado.</span><span class="sxs-lookup"><span data-stu-id="f8a83-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="f8a83-114">**\[IsVisible\]**  -opcional booleano se definido como **$true**, a ferramenta do suplemento está imediatamente visível no painel de ferramenta associados.</span><span class="sxs-lookup"><span data-stu-id="f8a83-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="f8a83-115">Remover\( Item \)</span><span class="sxs-lookup"><span data-stu-id="f8a83-115">Remove\( Item \)</span></span>

<span data-ttu-id="f8a83-116">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f8a83-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f8a83-117">Remove a ferramenta do suplemento especificado da coleção.</span><span class="sxs-lookup"><span data-stu-id="f8a83-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="f8a83-118">**Item** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Especifica o objeto seja removido do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f8a83-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="f8a83-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="f8a83-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="f8a83-120">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f8a83-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f8a83-121">Seleciona o PowerShell separador que o **psTab** parâmetro especifica.</span><span class="sxs-lookup"><span data-stu-id="f8a83-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="f8a83-122">**psTab** -separador de PowerShell Microsoft.PowerShell.Host.ISE.PowerShellTab do selecionar.</span><span class="sxs-lookup"><span data-stu-id="f8a83-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="f8a83-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="f8a83-123">Remove\( psTab \)</span></span>

<span data-ttu-id="f8a83-124">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="f8a83-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f8a83-125">Remove o PowerShell separador que o **psTab** parâmetro especifica.</span><span class="sxs-lookup"><span data-stu-id="f8a83-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="f8a83-126">**psTab** -separador de PowerShell Microsoft.PowerShell.Host.ISE.PowerShellTab do remover.</span><span class="sxs-lookup"><span data-stu-id="f8a83-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="f8a83-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="f8a83-127">See Also</span></span>

- [<span data-ttu-id="f8a83-128">Objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="f8a83-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="f8a83-129">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="f8a83-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f8a83-130">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="f8a83-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
