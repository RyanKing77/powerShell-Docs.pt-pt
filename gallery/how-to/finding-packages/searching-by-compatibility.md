---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Pacotes com o sistema operativo ou edições do PowerShell compatíveis
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057183"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="5e59b-103">Pacotes com sistemas operativos ou edições do PowerShell compatíveis</span><span class="sxs-lookup"><span data-stu-id="5e59b-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="5e59b-104">A partir da versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos diferentes de recursos e às compatibilidades de plataforma.</span><span class="sxs-lookup"><span data-stu-id="5e59b-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="5e59b-105">Pesquisar por edição do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e59b-105">Searching by PowerShell Edition</span></span>

<span data-ttu-id="5e59b-106">As duas edições do PowerShell são:</span><span class="sxs-lookup"><span data-stu-id="5e59b-106">The two editions of PowerShell are:</span></span>
- <span data-ttu-id="5e59b-107">**Edição Desktop:** Criado no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows como núcleo de servidor e Desktop do Windows.</span><span class="sxs-lookup"><span data-stu-id="5e59b-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="5e59b-108">**Edição Core:** Incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, como o servidor Nano e o Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="5e59b-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="5e59b-109">Galeria do PowerShell permite-lhe filtrar pacotes compatíveis para as edições específicas do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e59b-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="5e59b-110">Se um pacote tem compatível edições do PowerShell especificado, são listados como parte das edições do PowerShell na página de exibição do pacote e também nos resultados de pacotes.</span><span class="sxs-lookup"><span data-stu-id="5e59b-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="5e59b-111">Também pode procurar pacotes compatíveis com o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e59b-111">You can also search for compatible packages using PowerShell.</span></span>

![Página de exibição de itens com edições do PowerShell](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="5e59b-113">Procurar pacotes na galeria da interface do Usuário que funcionam no PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5e59b-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="5e59b-114">Utilizar etiquetas: "PSEdition_Desktop" e as etiquetas: "PSEdition_Core" aos filtros de pacotes na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e59b-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="5e59b-115">Utilizar etiquetas: "PSEdition_Core" Pesquisar itens compatíveis com o PowerShell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="5e59b-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Resultados da pesquisa para itens compatíveis com o Core PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="5e59b-117">Utilizar etiquetas: "PSEdition_Desktop" Pesquisar itens compatíveis com a edição de ambiente de trabalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e59b-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Resultados da pesquisa para itens compatíveis com PSEdition da área de trabalho](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="5e59b-119">Procurar pacotes encontrar as edições compatíveis com o PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e59b-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="5e59b-120">Pode especificar etiquetas para filtrar para a edição do PowerShell e o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="5e59b-120">You can specify tags to filter for the PowerShell edition and OS.</span></span>
<span data-ttu-id="5e59b-121">Utilizar o `Find-Package` cmdlet especificando o `-Tag` parâmetro para especificar a edição (e o sistema operacional) estiver a filtrar.</span><span class="sxs-lookup"><span data-stu-id="5e59b-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="5e59b-122">Como este:</span><span class="sxs-lookup"><span data-stu-id="5e59b-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="5e59b-123">Pesquisar por sistema operativo</span><span class="sxs-lookup"><span data-stu-id="5e59b-123">Searching by Operating System</span></span>

<span data-ttu-id="5e59b-124">Uma vez que o PowerShell Core está disponível para Windows, Linux e MacOS, pacotes na galeria podem ser criados para qualquer combinação destes sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="5e59b-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="5e59b-125">Na galeria da interface do Usuário utilize as seguintes etiquetas searchs para encontrar pacotes marcados pelo sistema operativo:</span><span class="sxs-lookup"><span data-stu-id="5e59b-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="5e59b-126">Tags: "Windows"</span><span class="sxs-lookup"><span data-stu-id="5e59b-126">Tags: "Windows"</span></span>
- <span data-ttu-id="5e59b-127">Tags: "Linux"</span><span class="sxs-lookup"><span data-stu-id="5e59b-127">Tags: "Linux"</span></span>
- <span data-ttu-id="5e59b-128">Tags: "MacOS"</span><span class="sxs-lookup"><span data-stu-id="5e59b-128">Tags: "MacOS"</span></span>

<span data-ttu-id="5e59b-129">Pode especificar essas marcas na `Find-Module` (e outros cmdlets no módulo PowerShellGet), assim:</span><span class="sxs-lookup"><span data-stu-id="5e59b-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="5e59b-130">A procurar às compatibilidades vários</span><span class="sxs-lookup"><span data-stu-id="5e59b-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="5e59b-131">Pode procurar por um pacote que tenha às compatibilidades vários utilizando a sintaxe:</span><span class="sxs-lookup"><span data-stu-id="5e59b-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span>

<span data-ttu-id="5e59b-132">Tags: "Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="5e59b-132">Tags: "Compatibility1" "Compatibility2"</span></span>

<span data-ttu-id="5e59b-133">Por exemplo, se estiver procurando por um pacote com o PowerShell Core compatibilidade, que é executado em meus computadores Windows e Linux, utilize as etiquetas de pesquisa:</span><span class="sxs-lookup"><span data-stu-id="5e59b-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="5e59b-134">Tags: "PSEdition_Core" "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="5e59b-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span>

<span data-ttu-id="5e59b-135">Para procurar com o PowerShell, pode usar o `Find-Module` (e os outros cmdlets no módulo PowerShellGet), assim:</span><span class="sxs-lookup"><span data-stu-id="5e59b-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="5e59b-136">Obter mais detalhes sobre a criação e encontrar os pacotes com edições do PowerShell compatíveis</span><span class="sxs-lookup"><span data-stu-id="5e59b-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="5e59b-137">Módulos com Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e59b-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="5e59b-138">Scripts com Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e59b-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
