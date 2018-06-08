---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, powershell, cmdlet, psgallery, psget
title: A galeria do PowerShell
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482935"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="b0794-103">A galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0794-103">The PowerShell Gallery</span></span>

<span data-ttu-id="b0794-104">A galeria do PowerShell consiste no repositório central para o conteúdo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0794-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="b0794-105">Aqui, pode encontrar útil módulos do PowerShell que contém os comandos do PowerShell e recursos de configuração de estado pretendido (DSC).</span><span class="sxs-lookup"><span data-stu-id="b0794-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="b0794-106">Também pode encontrar scripts do PowerShell, algumas das quais podem conter fluxos de trabalho do PowerShell e que descrevem um conjunto de tarefas e fornecer a sequenciação para essas tarefas.</span><span class="sxs-lookup"><span data-stu-id="b0794-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="b0794-107">Alguns destes itens são criados pela Microsoft e outros são criados pela Comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0794-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="b0794-108">Descrição geral de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="b0794-108">PowerShellGet Overview</span></span>

<span data-ttu-id="b0794-109">O módulo de PowerShellGet contém cmdlets para detetar, instalar, atualizar e publicar PowerShell artefactos, tais como módulos, recursos de DSC, capacidades de função e Scripts a partir de [galeria do PowerShell](https://www.PowerShellGallery.com) e outra privada repositórios.</span><span class="sxs-lookup"><span data-stu-id="b0794-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="b0794-110">Introdução à Galeria</span><span class="sxs-lookup"><span data-stu-id="b0794-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="b0794-111">Instalar itens da galeria do requer a versão mais recente do módulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="b0794-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="b0794-112">Consulte [instalar PowerShellGet](installing-psget.md) para obter instruções completas.</span><span class="sxs-lookup"><span data-stu-id="b0794-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="b0794-113">Veja o [introdução](getting-started.md) página para obter mais informações sobre como utilizar comandos PowerShellGet com a galeria.</span><span class="sxs-lookup"><span data-stu-id="b0794-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="b0794-114">Também pode executar *Update-Help-PowerShellGet módulo* instalar ajuda local para estes comandos.</span><span class="sxs-lookup"><span data-stu-id="b0794-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="b0794-115">Sistemas operativos suportados</span><span class="sxs-lookup"><span data-stu-id="b0794-115">Supported Operating Systems</span></span>

<span data-ttu-id="b0794-116">O **PowerShellGet** módulo requer **do Windows PowerShell 3.0 ou mais recente**, ou **PowerShell Core 6.0 ou mais recente**.</span><span class="sxs-lookup"><span data-stu-id="b0794-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="b0794-117">Uma versão adequada do **do Windows PowerShell** está disponível para estes sistemas operativos:</span><span class="sxs-lookup"><span data-stu-id="b0794-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="b0794-118">10 do Windows</span><span class="sxs-lookup"><span data-stu-id="b0794-118">Windows 10</span></span>
- <span data-ttu-id="b0794-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="b0794-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="b0794-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="b0794-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="b0794-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="b0794-121">Windows 7 SP1</span></span>
- <span data-ttu-id="b0794-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="b0794-122">Windows Server 2016</span></span>
- <span data-ttu-id="b0794-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="b0794-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="b0794-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="b0794-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="b0794-125">**PowerShellGet** também requer o .NET Framework 4.5 ou superior.</span><span class="sxs-lookup"><span data-stu-id="b0794-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="b0794-126">Pode instalar o .NET Framework 4.5 ou superior do [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="b0794-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="b0794-127">**PowerShell Core** suporta muitos sistemas operativos.</span><span class="sxs-lookup"><span data-stu-id="b0794-127">**PowerShell Core** supports many operating systems.</span></span> <span data-ttu-id="b0794-128">Consulte [neste artigo](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) para uma lista completa.</span><span class="sxs-lookup"><span data-stu-id="b0794-128">See [this article](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) for a full list.</span></span>

<span data-ttu-id="b0794-129">Muitos módulos alojados na Galeria suporta sos diferentes e têm requisitos adicionais.</span><span class="sxs-lookup"><span data-stu-id="b0794-129">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="b0794-130">Consulte a documentação para os módulos para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="b0794-130">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="b0794-131">Recebeu uma pergunta?</span><span class="sxs-lookup"><span data-stu-id="b0794-131">Got a question?</span></span> <span data-ttu-id="b0794-132">Tem comentários?</span><span class="sxs-lookup"><span data-stu-id="b0794-132">Have feedback?</span></span>

<span data-ttu-id="b0794-133">Podem encontrar mais informações sobre a galeria do PowerShell e PowerShellGet no [introdução](getting-started.md) página.</span><span class="sxs-lookup"><span data-stu-id="b0794-133">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="b0794-134">Forneça comentários e comunicar problemas com [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="b0794-134">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
