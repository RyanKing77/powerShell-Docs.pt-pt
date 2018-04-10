---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, powershell, cmdlet, psgallery, psget
title: A galeria do PowerShell
ms.openlocfilehash: 9519b8bcca9f43419a33db380c3b852e9bb354ac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="bf0c0-103">A galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf0c0-103">The PowerShell Gallery</span></span>

<span data-ttu-id="bf0c0-104">A galeria do PowerShell consiste no repositório central para o conteúdo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf0c0-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="bf0c0-105">Pode encontrar os novos comandos do PowerShell ou de recursos de configuração de estado pretendido (DSC) na galeria.</span><span class="sxs-lookup"><span data-stu-id="bf0c0-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="bf0c0-106">Descrição geral de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bf0c0-106">PowerShellGet Overview</span></span>

<span data-ttu-id="bf0c0-107">O módulo de PowerShellGet contém cmdlets para detetar, instalar, atualizar e publicar PowerShell artefactos, tais como módulos, recursos de DSC, capacidades de função e Scripts a partir de [galeria do PowerShell](https://www.PowerShellGallery.com) e outra privada repositórios.</span><span class="sxs-lookup"><span data-stu-id="bf0c0-107">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="bf0c0-108">Introdução à Galeria</span><span class="sxs-lookup"><span data-stu-id="bf0c0-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="bf0c0-109">Instalar itens da galeria do requer a versão mais recente do módulo PowerShellGet, que está disponível no Windows 10, no Windows Management Framework (WMF) 5.0 ou no instalador do MSI com base em (para PowerShell 3 e 4).</span><span class="sxs-lookup"><span data-stu-id="bf0c0-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="bf0c0-110">[**Obter o Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span><span class="sxs-lookup"><span data-stu-id="bf0c0-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="bf0c0-111">[**Obter o WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), ou</span><span class="sxs-lookup"><span data-stu-id="bf0c0-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="bf0c0-112">**Obter o Instalador MSI**</span><span class="sxs-lookup"><span data-stu-id="bf0c0-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="bf0c0-113">Com a versão mais recente [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) módulo, pode:</span><span class="sxs-lookup"><span data-stu-id="bf0c0-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="bf0c0-114">Pesquisa através de itens na galeria com [encontrar o módulo](https://go.microsoft.com/fwlink/?LinkId=821658) e [localizar Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span><span class="sxs-lookup"><span data-stu-id="bf0c0-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="bf0c0-115">Guardar itens para o sistema da galeria com [guardar-Module](https://go.microsoft.com/fwlink/?LinkId=821669) e [Script guardar](https://go.microsoft.com/fwlink/?LinkId=822334)</span><span class="sxs-lookup"><span data-stu-id="bf0c0-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="bf0c0-116">Instale os itens da galeria com [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) e [Script de instalação](https://go.microsoft.com/fwlink/?LinkId=822327)</span><span class="sxs-lookup"><span data-stu-id="bf0c0-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="bf0c0-117">Carregar itens para a galeria com [publicar-Module](https://go.microsoft.com/fwlink/?LinkId=821666) e [publicar Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span><span class="sxs-lookup"><span data-stu-id="bf0c0-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="bf0c0-118">Adicione o seus próprios repositório personalizado com [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span><span class="sxs-lookup"><span data-stu-id="bf0c0-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="bf0c0-119">Veja o [introdução](psgallery/psgallery_gettingstarted.md) página para obter mais informações sobre como utilizar comandos PowerShellGet com a galeria.</span><span class="sxs-lookup"><span data-stu-id="bf0c0-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="bf0c0-120">Também pode executar *Update-Help-PowerShellGet módulo* instalar ajuda local para estes comandos.</span><span class="sxs-lookup"><span data-stu-id="bf0c0-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="bf0c0-121">Sistemas operativos suportados</span><span class="sxs-lookup"><span data-stu-id="bf0c0-121">Supported Operating Systems</span></span>

<span data-ttu-id="bf0c0-122">O **PowerShellGet** módulo requer **PowerShell 3.0 ou mais recente**.</span><span class="sxs-lookup"><span data-stu-id="bf0c0-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="bf0c0-123">Por conseguinte, **PowerShellGet** necessita de um dos seguintes sistemas operativos:</span><span class="sxs-lookup"><span data-stu-id="bf0c0-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="bf0c0-124">10 do Windows</span><span class="sxs-lookup"><span data-stu-id="bf0c0-124">Windows 10</span></span>
- <span data-ttu-id="bf0c0-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="bf0c0-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="bf0c0-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="bf0c0-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="bf0c0-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="bf0c0-127">Windows 7 SP1</span></span>
- <span data-ttu-id="bf0c0-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="bf0c0-128">Windows Server 2016</span></span>
- <span data-ttu-id="bf0c0-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="bf0c0-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="bf0c0-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="bf0c0-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="bf0c0-131">**PowerShellGet** também requer o .NET Framework 4.5 ou superior.</span><span class="sxs-lookup"><span data-stu-id="bf0c0-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="bf0c0-132">Pode instalar o .NET Framework 4.5 ou superior do [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="bf0c0-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="bf0c0-133">Recebeu uma pergunta?</span><span class="sxs-lookup"><span data-stu-id="bf0c0-133">Got a question?</span></span> <span data-ttu-id="bf0c0-134">Tem comentários?</span><span class="sxs-lookup"><span data-stu-id="bf0c0-134">Have feedback?</span></span>

<span data-ttu-id="bf0c0-135">Podem encontrar mais informações sobre a galeria do PowerShell e PowerShellGet no [introdução](psgallery/psgallery_gettingstarted.md) página.</span><span class="sxs-lookup"><span data-stu-id="bf0c0-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="bf0c0-136">Forneça comentários e comunicar problemas com [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="bf0c0-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>