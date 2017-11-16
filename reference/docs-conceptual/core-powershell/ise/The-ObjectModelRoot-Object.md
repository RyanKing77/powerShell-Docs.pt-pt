---
ms.date: 2017-08-25
keywords: PowerShell, o cmdlet
title: O objeto de ObjectModelRoot
ms.openlocfilehash: eb3424ff147c35364fa08543d59ebd30f6d2d857
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="34c52-103">O objeto de ObjectModelRoot</span><span class="sxs-lookup"><span data-stu-id="34c52-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="34c52-104">O **$psISE** objeto, que é o objeto principal raiz no Windows PowerShell® Integrated Scripting Environment (ISE) é uma instância da classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="34c52-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="34c52-105">Este tópico descreve as propriedades do **ObjectModelRoot** objeto.</span><span class="sxs-lookup"><span data-stu-id="34c52-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="34c52-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="34c52-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="34c52-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="34c52-107">CurrentFile</span></span>

> <span data-ttu-id="34c52-108">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="34c52-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="34c52-109">A propriedade só de leitura que obtém o ficheiro, que está associado este objeto de anfitrião que tem actualmente o foco.</span><span class="sxs-lookup"><span data-stu-id="34c52-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="34c52-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="34c52-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="34c52-111">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="34c52-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="34c52-112">A propriedade só de leitura que obtém o separador do PowerShell que tem o foco.</span><span class="sxs-lookup"><span data-stu-id="34c52-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="34c52-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="34c52-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="34c52-114">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="34c52-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="34c52-115">A propriedade só de leitura que obtém a ferramenta de suplemento atualmente visível do ISE do Windows PowerShell que está localizada no painel de ferramenta horizontal na parte inferior do editor.</span><span class="sxs-lookup"><span data-stu-id="34c52-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="34c52-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="34c52-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="34c52-117">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="34c52-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="34c52-118">A propriedade só de leitura que obtém a ferramenta de suplemento atualmente visível do ISE do Windows PowerShell que está localizada no painel de ferramenta vertical no lado direito do editor.</span><span class="sxs-lookup"><span data-stu-id="34c52-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="34c52-119">Opções</span><span class="sxs-lookup"><span data-stu-id="34c52-119">Options</span></span>

> <span data-ttu-id="34c52-120">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="34c52-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="34c52-121">A propriedade só de leitura que obtém as várias opções que pode alterar as definições no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34c52-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="34c52-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="34c52-122">PowerShellTabs</span></span>

> <span data-ttu-id="34c52-123">Suportado no Windows PowerShell ISE 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="34c52-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="34c52-124">A propriedade só de leitura que obtém a coleção dos separadores do PowerShell, que estão abertos no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34c52-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="34c52-125">Por predefinição, este objeto contém um separador de PowerShell. No entanto, pode adicionar mais separadores de PowerShell para este objeto utilizando scripts ou utilizando os menus no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34c52-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="34c52-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="34c52-126">See Also</span></span>

- [<span data-ttu-id="34c52-127">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="34c52-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="34c52-128">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="34c52-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="34c52-129">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="34c52-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
