---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Hierarquia do Modelo de Objeto ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950697"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="3d2ac-103">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="3d2ac-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="3d2ac-104">Este tópico mostra a hierarquia de objetos que fazem parte do Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="3d2ac-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
<span data-ttu-id="3d2ac-105">ISE do Windows PowerShell está incluído no Windows PowerShell 3.0 e no Windows PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span>
<span data-ttu-id="3d2ac-106">Clique num objeto para leva-o para a documentação de referência para a classe que define o objeto.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="3d2ac-107">objeto de $psISE</span><span class="sxs-lookup"><span data-stu-id="3d2ac-107">$psISE Object</span></span>

<span data-ttu-id="3d2ac-108">O **$psISE** objeto é o [objecto raiz](The-ObjectModelRoot-Object.md) da hierarquia de objeto de ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="3d2ac-109">Localizada no nível superior, disponibiliza os seguintes objetos para processamento de scripts:</span><span class="sxs-lookup"><span data-stu-id="3d2ac-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="3d2ac-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="3d2ac-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="3d2ac-111">O **$psISE.CurrentFile** objeto é uma instância do [ISEFile](The-ISEFile-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="3d2ac-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="3d2ac-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="3d2ac-113">O **$psISE.CurrentPowerShellTab** objeto é uma instância do [PowerShellTab](The-PowerShellTab-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="3d2ac-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="3d2ac-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="3d2ac-115">O **$psISE.CurrentVisibleHorizontalTool** objeto é uma instância do [ISEAddOnTool](The-ISEAddOnTool-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="3d2ac-116">Representa a ferramenta de suplemento instalado atualmente estiver ancorada para o limite superior da janela ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="3d2ac-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="3d2ac-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="3d2ac-118">O **$psISE.CurrentVisibleHorizontalTool** objeto é uma instância do [ISEAddOnTool](The-ISEAddOnTool-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="3d2ac-119">Representa a ferramenta de suplemento instalado atualmente estiver ancorada para o limite direito da janela ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="3d2ac-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="3d2ac-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="3d2ac-121">O **$psISE.Options** objeto é uma instância do [ISEOptions](The-ISEOptions-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="3d2ac-122">O objeto de ISEOptions representa várias definições de ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="3d2ac-123">É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEOptions.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="3d2ac-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="3d2ac-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="3d2ac-125">O **$psISE.PowerShellTabs** objeto é uma instância do [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="3d2ac-126">É uma coleção de todos os atualmente abertos PowerShell separadores que representam o Windows PowerShell disponíveis execute ambientes no computador local ou em computadores remotos ligados.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span>
<span data-ttu-id="3d2ac-127">Cada membro da coleção é uma instância do [PowerShellTab](The-PowerShellTab-Object.md) classe.</span><span class="sxs-lookup"><span data-stu-id="3d2ac-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d2ac-128">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="3d2ac-128">See Also</span></span>

- [<span data-ttu-id="3d2ac-129">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="3d2ac-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="3d2ac-130">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="3d2ac-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)