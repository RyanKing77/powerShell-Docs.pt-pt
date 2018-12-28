---
ms.date: 08/25/2017
keywords: PowerShell, o cmdlet
title: Objeto ObjectModelRoot
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405587"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="0254f-103">Objeto ObjectModelRoot</span><span class="sxs-lookup"><span data-stu-id="0254f-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="0254f-104">O **$psISE** objeto, o que é o objeto raiz principal no Windows PowerShell® Integrated Scripting Environment (ISE) é uma instância da classe Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="0254f-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="0254f-105">Este tópico descreve as propriedades do **ObjectModelRoot** objeto.</span><span class="sxs-lookup"><span data-stu-id="0254f-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="0254f-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0254f-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="0254f-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="0254f-107">CurrentFile</span></span>

> <span data-ttu-id="0254f-108">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="0254f-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0254f-109">A propriedade só de leitura que obtém o arquivo, que está associado este objeto de host que atualmente possui o foco.</span><span class="sxs-lookup"><span data-stu-id="0254f-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="0254f-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="0254f-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="0254f-111">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="0254f-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0254f-112">A propriedade só de leitura que obtém o separador do PowerShell que possui o foco.</span><span class="sxs-lookup"><span data-stu-id="0254f-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="0254f-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="0254f-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="0254f-114">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="0254f-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0254f-115">A propriedade só de leitura que obtém a ferramenta de suplemento visível no momento do ISE do Windows PowerShell que está localizada no painel de ferramenta horizontal na parte inferior do editor.</span><span class="sxs-lookup"><span data-stu-id="0254f-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="0254f-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="0254f-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="0254f-117">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="0254f-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0254f-118">A propriedade só de leitura que obtém a ferramenta de suplemento visível no momento do ISE do Windows PowerShell que está localizada no painel de ferramenta vertical no lado direito do editor.</span><span class="sxs-lookup"><span data-stu-id="0254f-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="0254f-119">Opções</span><span class="sxs-lookup"><span data-stu-id="0254f-119">Options</span></span>

> <span data-ttu-id="0254f-120">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="0254f-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0254f-121">A propriedade só de leitura que obtém as várias opções que pode alterar as definições no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0254f-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="0254f-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="0254f-122">PowerShellTabs</span></span>

> <span data-ttu-id="0254f-123">Suportado no Windows PowerShell ISE 2.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="0254f-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0254f-124">A propriedade só de leitura que obtém a coleção de guias do PowerShell, que estão abertas no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0254f-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="0254f-125">Por predefinição, este objeto contém um separador do PowerShell. No entanto, pode adicionar mais guias do PowerShell para este objeto utilizando scripts ou utilizando os menus no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0254f-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="0254f-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0254f-126">See Also</span></span>

- [<span data-ttu-id="0254f-127">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="0254f-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="0254f-128">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="0254f-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)