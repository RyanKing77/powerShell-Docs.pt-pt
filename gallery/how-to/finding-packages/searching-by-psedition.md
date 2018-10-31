---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Pacotes com edições do PowerShell compatíveis
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004154"
---
# <a name="packages-with-compatible-powershell-editions"></a><span data-ttu-id="977ba-103">Pacotes com edições do PowerShell compatíveis</span><span class="sxs-lookup"><span data-stu-id="977ba-103">Packages with compatible PowerShell Editions</span></span>

<span data-ttu-id="977ba-104">Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.</span><span class="sxs-lookup"><span data-stu-id="977ba-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="977ba-105">**Edição Desktop:** incorporada no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows, tais como Server Core e o Ambiente de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="977ba-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="977ba-106">**Edição Core:** incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, tais como Servidor Nano e o IoT do Windows.</span><span class="sxs-lookup"><span data-stu-id="977ba-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="977ba-107">Galeria do PowerShell extrai metadados de edições do PowerShell suportados e permite os pacotes de filtros compatível para edições específicas do PowerShell</span><span class="sxs-lookup"><span data-stu-id="977ba-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="977ba-108">Se um pacote tem compatível edições do PowerShell especificados, estes serão apresentados como parte das edições do PowerShell na página de exibição do pacote e também nos resultados de pacotes.</span><span class="sxs-lookup"><span data-stu-id="977ba-108">If a package has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>

![Página de exibição de itens com edições do PowerShell](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="977ba-110">Procurar pacotes na galeria da interface do Usuário que funciona em PowerShellCore</span><span class="sxs-lookup"><span data-stu-id="977ba-110">Search for packages in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="977ba-111">Utilizar etiquetas: "PSEdition_Desktop" e as etiquetas: "PSEdition_Core" aos filtros de pacotes na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="977ba-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="977ba-112">Utilizar etiquetas: "PSEdition_Core" Pesquisar itens compatíveis com o PowerShell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="977ba-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Resultados da pesquisa para itens compatíveis com o Core PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="977ba-114">Utilizar etiquetas: "PSEdition_Desktop" Pesquisar itens compatíveis com a edição de ambiente de trabalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="977ba-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Resultados da pesquisa para itens compatíveis com PSEdition da área de trabalho](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="977ba-116">Obter mais detalhes sobre a criação e encontrar os pacotes com edições do PowerShell compatíveis</span><span class="sxs-lookup"><span data-stu-id="977ba-116">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="977ba-117">Módulos com Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="977ba-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="977ba-118">Scripts com Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="977ba-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
