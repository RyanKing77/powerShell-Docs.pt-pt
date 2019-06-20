---
title: Conceitos do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263855"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="4a743-102">Windows PowerShell Concepts (Conceitos do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="4a743-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="4a743-103">Esta secção contém informações conceituais que irão ajudar a compreender o PowerShell do ponto de vista do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="4a743-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="4a743-104">Nome do tópico</span><span class="sxs-lookup"><span data-stu-id="4a743-104">Topic Name</span></span>|<span data-ttu-id="4a743-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a743-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="4a743-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="4a743-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="4a743-107">Descrição de objetos do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a743-107">Description of PowerShell objects.</span></span> <span data-ttu-id="4a743-108">Para obter mais informações, consulte [sobre a criação do objeto](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="4a743-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="4a743-109">Criação de espaços de execução</span><span class="sxs-lookup"><span data-stu-id="4a743-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="4a743-110">Os ambientes operacionais em que os comandos são processados.</span><span class="sxs-lookup"><span data-stu-id="4a743-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="4a743-111">Para obter mais informações, consulte [classe de espaço de execução](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="4a743-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="4a743-112">Estender objetos de saída</span><span class="sxs-lookup"><span data-stu-id="4a743-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="4a743-113">Como estender objetos do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a743-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="4a743-114">Para obter mais informações, consulte [sobre Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="4a743-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="4a743-115">Cmdlets de registo</span><span class="sxs-lookup"><span data-stu-id="4a743-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="4a743-116">Como tornar os módulos e snap-ins disponíveis no PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a743-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="4a743-117">Para obter mais informações, consulte [módulos e Snap-ins](../cmdlet/modules-and-snap-ins.md).</span><span class="sxs-lookup"><span data-stu-id="4a743-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="4a743-118">A pedir a confirmação de Cmdlets</span><span class="sxs-lookup"><span data-stu-id="4a743-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="4a743-119">Como o cmdlets e provedores solicitar comentários do usuário antes de uma ação está a ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="4a743-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="4a743-120">Classe de RuntimeDefinedParameter</span><span class="sxs-lookup"><span data-stu-id="4a743-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="4a743-121">Declarações de parâmetro de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4a743-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="4a743-122">Espaço de nomes de System.Management.Automation</span><span class="sxs-lookup"><span data-stu-id="4a743-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="4a743-123">Descrição geral dos espaços de nomes de API do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a743-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="4a743-124">Descrição geral de fornecedor do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="4a743-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="4a743-125">Armazena a visão geral sobre provedores de PowerShell que são utilizados para aceder aos dados.</span><span class="sxs-lookup"><span data-stu-id="4a743-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="4a743-126">Escrever ajuda para Cmdlets do PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a743-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="4a743-127">Como escrever ajuda do cmdlet do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a743-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4a743-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a743-128">See also</span></span>

[<span data-ttu-id="4a743-129">Classe do PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a743-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="4a743-130">Referência da API do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="4a743-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="4a743-131">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a743-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4a743-132">Escrever ajuda para módulos do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a743-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="4a743-133">Escrever um fornecedor do Windows Powershell</span><span class="sxs-lookup"><span data-stu-id="4a743-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="4a743-134">Referência da API do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a743-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="4a743-135">Referência do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a743-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)