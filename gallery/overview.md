---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, powershell, cmdlet, psgallery, psget
title: A galeria do PowerShell
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076026"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="eedf7-103">A galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="eedf7-103">The PowerShell Gallery</span></span>

<span data-ttu-id="eedf7-104">A galeria do PowerShell é o repositório central para o conteúdo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eedf7-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="eedf7-105">Nela, pode encontrar útil módulos do PowerShell que contém comandos do PowerShell e de recursos do Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="eedf7-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="eedf7-106">Também pode encontrar scripts do PowerShell, algumas das quais podem conter fluxos de trabalho do PowerShell e que descrevem um conjunto de tarefas e fornecer o sequenciamento para essas tarefas.</span><span class="sxs-lookup"><span data-stu-id="eedf7-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="eedf7-107">Alguns desses pacotes são criados pela Microsoft e outros são criados pela Comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eedf7-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="eedf7-108">Descrição geral do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="eedf7-108">PowerShellGet Overview</span></span>

<span data-ttu-id="eedf7-109">O módulo PowerShellGet contém cmdlets para descobrir, instalar, atualizar e publicação de pacotes do PowerShell que contêm os artefactos, tais como módulos, recursos de DSC, funcionalidades de função e Scripts a partir do [galeria do PowerShell](https://www.PowerShellGallery.com)e outros repositórios privados.</span><span class="sxs-lookup"><span data-stu-id="eedf7-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="eedf7-110">Guia de introdução da Galeria</span><span class="sxs-lookup"><span data-stu-id="eedf7-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="eedf7-111">Instalar pacotes a partir da Galeria requer a versão mais recente do módulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="eedf7-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="eedf7-112">Ver [instalar o PowerShellGet](installing-psget.md) para obter instruções completas.</span><span class="sxs-lookup"><span data-stu-id="eedf7-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="eedf7-113">Veja a [introdução ao](getting-started.md) página para obter mais informações sobre como utilizar comandos do PowerShellGet com a galeria.</span><span class="sxs-lookup"><span data-stu-id="eedf7-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="eedf7-114">Também pode executar *Update-Help-Module PowerShellGet* para instalar ajuda local para estes comandos.</span><span class="sxs-lookup"><span data-stu-id="eedf7-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="eedf7-115">Sistemas operativos suportados</span><span class="sxs-lookup"><span data-stu-id="eedf7-115">Supported Operating Systems</span></span>

<span data-ttu-id="eedf7-116">O **PowerShellGet** requer o módulo **Windows PowerShell 3.0 ou mais recente**, ou **PowerShell Core 6.0 ou mais recente**.</span><span class="sxs-lookup"><span data-stu-id="eedf7-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="eedf7-117">Uma versão adequada do **Windows PowerShell** está disponível para estes sistemas operativos:</span><span class="sxs-lookup"><span data-stu-id="eedf7-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="eedf7-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="eedf7-118">Windows 10</span></span>
- <span data-ttu-id="eedf7-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="eedf7-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="eedf7-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="eedf7-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="eedf7-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="eedf7-121">Windows 7 SP1</span></span>
- <span data-ttu-id="eedf7-122">Windows Server de 2019</span><span class="sxs-lookup"><span data-stu-id="eedf7-122">Windows Server 2019</span></span>
- <span data-ttu-id="eedf7-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="eedf7-123">Windows Server 2016</span></span>
- <span data-ttu-id="eedf7-124">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="eedf7-124">Windows Server 2012 R2</span></span>
- <span data-ttu-id="eedf7-125">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="eedf7-125">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="eedf7-126">**O PowerShellGet** requer o .NET Framework 4.5 ou superior.</span><span class="sxs-lookup"><span data-stu-id="eedf7-126">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="eedf7-127">Pode instalar o .NET Framework 4.5 ou superior partir [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="eedf7-127">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="eedf7-128">Uma vez que **PowerShell Core** é Multiplataforma e o que significa que ele funciona no Windows, Linux e MacOS, que também faz **PowerShellGet** disponíveis nesses sistemas.</span><span class="sxs-lookup"><span data-stu-id="eedf7-128">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="eedf7-129">Para obter uma lista completa de sistemas suportados pelo **PowerShell Core** veja [instalar o PowerShell](/powershell/scripting/setup/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="eedf7-129">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/setup/installing-powershell).</span></span>

<span data-ttu-id="eedf7-130">Muitos módulos hospedados na Galeria irão oferecer suporte a sistemas operacionais diferentes e têm requisitos adicionais.</span><span class="sxs-lookup"><span data-stu-id="eedf7-130">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="eedf7-131">Consulte a documentação para os módulos para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="eedf7-131">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="eedf7-132">Tem uma pergunta?</span><span class="sxs-lookup"><span data-stu-id="eedf7-132">Got a question?</span></span> <span data-ttu-id="eedf7-133">Tem comentários?</span><span class="sxs-lookup"><span data-stu-id="eedf7-133">Have feedback?</span></span>

<span data-ttu-id="eedf7-134">Obter mais informações sobre a galeria do PowerShell e o PowerShellGet podem ser encontradas no [introdução ao](getting-started.md) página.</span><span class="sxs-lookup"><span data-stu-id="eedf7-134">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="eedf7-135">Introduza os comentários e relatório de problemas usando [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="eedf7-135">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
