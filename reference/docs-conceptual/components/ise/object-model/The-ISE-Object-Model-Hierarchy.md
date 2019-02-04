---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Hierarquia do Modelo de Objeto ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683773"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="84f42-103">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="84f42-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="84f42-104">Este tópico mostra a hierarquia de objetos que fazem parte do Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="84f42-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
<span data-ttu-id="84f42-105">ISE do Windows PowerShell é incluído no Windows PowerShell 3.0 e no Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="84f42-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span>
<span data-ttu-id="84f42-106">Clique num objeto para levá-lo para a documentação de referência para a classe que define o objeto.</span><span class="sxs-lookup"><span data-stu-id="84f42-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="84f42-107">objeto de $psISE</span><span class="sxs-lookup"><span data-stu-id="84f42-107">$psISE Object</span></span>

<span data-ttu-id="84f42-108">O **$psISE** objeto é a [objeto raiz](The-ObjectModelRoot-Object.md) da hierarquia de objeto ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84f42-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="84f42-109">Localizado no nível superior, disponibiliza os seguintes objetos para processamento de scripts:</span><span class="sxs-lookup"><span data-stu-id="84f42-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="84f42-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="84f42-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="84f42-111">O **$psISE.CurrentFile** objeto é uma instância da [ISEFile](The-ISEFile-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="84f42-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="84f42-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="84f42-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="84f42-113">O **$psISE.CurrentPowerShellTab** objeto é uma instância da [PowerShellTab](The-PowerShellTab-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="84f42-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="84f42-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="84f42-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="84f42-115">O **$psISE.CurrentVisibleHorizontalTool** objeto é uma instância da [ISEAddOnTool](The-ISEAddOnTool-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="84f42-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="84f42-116">Ele representa a ferramenta do suplemento instalado que atualmente é encaixada na borda superior da janela de ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84f42-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="84f42-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="84f42-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="84f42-118">O **$psISE.CurrentVisibleHorizontalTool** objeto é uma instância da [ISEAddOnTool](The-ISEAddOnTool-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="84f42-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="84f42-119">Ele representa a ferramenta do suplemento instalado que atualmente é encaixada na borda direita da janela de ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84f42-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="84f42-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="84f42-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="84f42-121">O **$psISE.Options** objeto é uma instância da [ISEOptions](The-ISEOptions-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="84f42-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="84f42-122">Objeto ISEOptions representa várias definições para o Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="84f42-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="84f42-123">É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="84f42-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="84f42-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="84f42-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="84f42-125">O **$psISE.PowerShellTabs** objeto é uma instância da [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="84f42-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="84f42-126">É uma coleção de todos os atualmente abertas PowerShell guias que representam a ambientes de execução no computador local ou em computadores remotos ligados do Windows PowerShell disponíveis.</span><span class="sxs-lookup"><span data-stu-id="84f42-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span>
<span data-ttu-id="84f42-127">Cada membro da coleção é uma instância do [PowerShellTab](The-PowerShellTab-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="84f42-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="84f42-128">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="84f42-128">See Also</span></span>

- [<span data-ttu-id="84f42-129">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="84f42-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="84f42-130">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="84f42-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)