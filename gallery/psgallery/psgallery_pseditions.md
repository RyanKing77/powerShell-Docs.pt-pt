---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgallery_pseditions
ms.openlocfilehash: 0b30c1da53832a6b74be7aa14ed9331b1e9fe643
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="items-with-compatible-powershell-editions"></a><span data-ttu-id="08a0a-103">Itens com edições de PowerShell compatível</span><span class="sxs-lookup"><span data-stu-id="08a0a-103">Items with compatible PowerShell Editions</span></span>
<span data-ttu-id="08a0a-104">Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.</span><span class="sxs-lookup"><span data-stu-id="08a0a-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="08a0a-105">**Edição Desktop:** incorporada no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows, tais como Server Core e o Ambiente de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="08a0a-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="08a0a-106">**Edição Core:** incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, tais como Servidor Nano e o IoT do Windows.</span><span class="sxs-lookup"><span data-stu-id="08a0a-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a><span data-ttu-id="08a0a-107">Galeria do PowerShell extrai metadados de PSEditions suportados e permite-lhe os itens de filtros compatível para edições específicas do PowerShell</span><span class="sxs-lookup"><span data-stu-id="08a0a-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the items compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="08a0a-108">Se um item tem compatível PSEditions especificados, estes serão apresentados como parte do 'PowerShell edições' na página de visualização do item e também nos resultados de itens.</span><span class="sxs-lookup"><span data-stu-id="08a0a-108">If an item has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the item display page and also in items results.</span></span>
<span data-ttu-id="08a0a-109">![Página de visualização do item com PSEditions](Images/ItemDisplayPageWithPSEditions.PNG)</span><span class="sxs-lookup"><span data-stu-id="08a0a-109">![Item display page with PSEditions](Images/ItemDisplayPageWithPSEditions.PNG)</span></span>

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="08a0a-110">Pesquisa de itens de Galeria de IU que funciona em PowerShellCore</span><span class="sxs-lookup"><span data-stu-id="08a0a-110">Search for items in the gallery UI which works on PowerShellCore</span></span>
<span data-ttu-id="08a0a-111">Utilize etiquetas: etiquetas e "PSEdition_Desktop": "PSEdition_Core" filtros os itens de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08a0a-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the items on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="08a0a-112">Utilize etiquetas: "PSEdition_Core" para procurar itens compatíveis com o PowerShell Core edição.</span><span class="sxs-lookup"><span data-stu-id="08a0a-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>
![Resultados da pesquisa para itens compatíveis com PSEdition de núcleo](Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="08a0a-114">Utilize etiquetas: "PSEdition_Desktop" para procurar itens compatíveis com a edição de ambiente de trabalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08a0a-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>
![Resultados da pesquisa de itens compatíveis com o ambiente de trabalho PSEdition](Images/SearchResultsWithPSEdition_Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a><span data-ttu-id="08a0a-116">Obter mais detalhes sobre a criação e localizar os itens com edições de PowerShell compatível</span><span class="sxs-lookup"><span data-stu-id="08a0a-116">More details on authoring and finding the items with compatible PowerShell Editions</span></span>
### <a name="modules-with-pseditionspsgetmodulemodulewithpseditionsupportmd"></a>[<span data-ttu-id="08a0a-117">Módulos com Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="08a0a-117">Modules with PSEditions</span></span>](../psget/module/modulewithpseditionsupport.md)
### <a name="scripts-with-pseditionspsgetscriptscriptwithpseditionsupportmd"></a>[<span data-ttu-id="08a0a-118">Scripts com Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="08a0a-118">Scripts with PSEditions</span></span>](../psget/script/scriptwithpseditionsupport.md)