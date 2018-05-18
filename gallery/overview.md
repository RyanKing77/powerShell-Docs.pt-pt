---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, powershell, cmdlet, psgallery, psget
title: A galeria do PowerShell
ms.openlocfilehash: 65e0c427310ac20621109a6620e926a7894cf8f8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="a260e-103">A galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="a260e-103">The PowerShell Gallery</span></span>

<span data-ttu-id="a260e-104">A galeria do PowerShell consiste no repositório central para o conteúdo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a260e-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="a260e-105">Aqui, pode encontrar útil módulos do PowerShell que contém os comandos do PowerShell e recursos de configuração de estado pretendido (DSC).</span><span class="sxs-lookup"><span data-stu-id="a260e-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="a260e-106">Também pode encontrar scripts do PowerShell, algumas das quais podem conter fluxos de trabalho do PowerShell e que descrevem um conjunto de tarefas e fornecer a sequenciação para essas tarefas.</span><span class="sxs-lookup"><span data-stu-id="a260e-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="a260e-107">Alguns destes itens são criados pela Microsoft e outros são criados pela Comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a260e-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="a260e-108">Descrição geral de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a260e-108">PowerShellGet Overview</span></span>

<span data-ttu-id="a260e-109">O módulo de PowerShellGet contém cmdlets para detetar, instalar, atualizar e publicar PowerShell artefactos, tais como módulos, recursos de DSC, capacidades de função e Scripts a partir de [galeria do PowerShell](https://www.PowerShellGallery.com) e outra privada repositórios.</span><span class="sxs-lookup"><span data-stu-id="a260e-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="a260e-110">Introdução à Galeria</span><span class="sxs-lookup"><span data-stu-id="a260e-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="a260e-111">Instalar itens da galeria do requer a versão mais recente do módulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="a260e-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="a260e-112">Consulte [instalar PowerShellGet](installing-psget.md) para obter instruções completas.</span><span class="sxs-lookup"><span data-stu-id="a260e-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="a260e-113">Veja o [introdução](getting-started.md) página para obter mais informações sobre como utilizar comandos PowerShellGet com a galeria.</span><span class="sxs-lookup"><span data-stu-id="a260e-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="a260e-114">Também pode executar *Update-Help-PowerShellGet módulo* instalar ajuda local para estes comandos.</span><span class="sxs-lookup"><span data-stu-id="a260e-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="a260e-115">Sistemas operativos suportados</span><span class="sxs-lookup"><span data-stu-id="a260e-115">Supported Operating Systems</span></span>

<span data-ttu-id="a260e-116">O **PowerShellGet** módulo requer **PowerShell 3.0 ou mais recente**.</span><span class="sxs-lookup"><span data-stu-id="a260e-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="a260e-117">Por conseguinte, **PowerShellGet** necessita de um dos seguintes sistemas operativos:</span><span class="sxs-lookup"><span data-stu-id="a260e-117">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="a260e-118">10 do Windows</span><span class="sxs-lookup"><span data-stu-id="a260e-118">Windows 10</span></span>
- <span data-ttu-id="a260e-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="a260e-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="a260e-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="a260e-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="a260e-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="a260e-121">Windows 7 SP1</span></span>
- <span data-ttu-id="a260e-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="a260e-122">Windows Server 2016</span></span>
- <span data-ttu-id="a260e-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a260e-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="a260e-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="a260e-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="a260e-125">**PowerShellGet** também requer o .NET Framework 4.5 ou superior.</span><span class="sxs-lookup"><span data-stu-id="a260e-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="a260e-126">Pode instalar o .NET Framework 4.5 ou superior do [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="a260e-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="a260e-127">Recebeu uma pergunta?</span><span class="sxs-lookup"><span data-stu-id="a260e-127">Got a question?</span></span> <span data-ttu-id="a260e-128">Tem comentários?</span><span class="sxs-lookup"><span data-stu-id="a260e-128">Have feedback?</span></span>

<span data-ttu-id="a260e-129">Podem encontrar mais informações sobre a galeria do PowerShell e PowerShellGet no [introdução](getting-started.md) página.</span><span class="sxs-lookup"><span data-stu-id="a260e-129">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="a260e-130">Forneça comentários e comunicar problemas com [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="a260e-130">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>