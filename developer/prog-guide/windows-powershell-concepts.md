---
title: Conceitos do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: c4b13518ad6452a39ca49e897e1d3e353818d332
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850142"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="405ee-102">Windows PowerShell Concepts (Conceitos do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="405ee-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="405ee-103">Esta secção contém informações conceituais que irão ajudar a compreender o Windows PowerShell do ponto de vista de um desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="405ee-103">This section contains conceptual information that will help you understand Windows PowerShell from the viewpoint of a developer.</span></span>

|<span data-ttu-id="405ee-104">Nome do tópico</span><span class="sxs-lookup"><span data-stu-id="405ee-104">Topic Name</span></span>|<span data-ttu-id="405ee-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="405ee-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="405ee-106">Provedores do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="405ee-106">Windows PowerShell Providers</span></span>](http://msdn.microsoft.com/en-us/a65c5c75-1131-4ade-90d3-a613dbe620e9)|<span data-ttu-id="405ee-107">Armazena uma discussão sobre os fornecedores de Windows PowerShell que são utilizados para aceder aos dados.</span><span class="sxs-lookup"><span data-stu-id="405ee-107">A discussion about Windows PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="405ee-108">Snap-ins do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="405ee-108">Windows PowerShell Snap-ins</span></span>](http://msdn.microsoft.com/en-us/20e081a9-522c-48bf-9f21-faaf8cca2e82)|<span data-ttu-id="405ee-109">Um mecanismo para registrar cmdlets e provedores.</span><span class="sxs-lookup"><span data-stu-id="405ee-109">A mechanism for registering cmdlets and providers.</span></span> <span data-ttu-id="405ee-110">(Consulte também [escrever um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).)</span><span class="sxs-lookup"><span data-stu-id="405ee-110">(See also, [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).)</span></span>|
|[<span data-ttu-id="405ee-111">Windows PowerShell Runtime</span><span class="sxs-lookup"><span data-stu-id="405ee-111">Windows PowerShell Runtime</span></span>](http://msdn.microsoft.com/en-us/949f06e8-0224-4cd3-bbad-a0cebbb5dec8)|<span data-ttu-id="405ee-112">A instância atual do espaço de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="405ee-112">The current instance of the Windows PowerShell runspace.</span></span>|
|[<span data-ttu-id="405ee-113">Espaços de execução do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="405ee-113">Windows PowerShell Runspaces</span></span>](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9)|<span data-ttu-id="405ee-114">Os ambientes operacionais em que os comandos são processados.</span><span class="sxs-lookup"><span data-stu-id="405ee-114">The operating environments where commands are processed.</span></span>|
|[<span data-ttu-id="405ee-115">Espaços de nomes do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="405ee-115">Windows PowerShell Namespaces</span></span>](http://msdn.microsoft.com/en-us/04bd2841-e90c-47d2-8a1f-3aeb3df35176)|<span data-ttu-id="405ee-116">Descrição geral dos espaços de nomes de API do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="405ee-116">Overview of Windows PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="405ee-117">Ajuda do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="405ee-117">Windows PowerShell Help</span></span>](http://msdn.microsoft.com/en-us/097b7c1c-a056-4b36-9c86-65b2ee702fc7)|<span data-ttu-id="405ee-118">Uma discussão sobre como escrever ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="405ee-118">A discussion about writing cmdlet Help.</span></span>|
|[<span data-ttu-id="405ee-119">Pedir confirmação</span><span class="sxs-lookup"><span data-stu-id="405ee-119">Requesting Confirmation</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="405ee-120">Uma discussão sobre como cmdlets e provedores solicitar comentários do usuário antes de uma ação está a ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="405ee-120">A discussion about how cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="405ee-121">Conceitos de objeto do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="405ee-121">Windows PowerShell Object Concepts</span></span>](http://msdn.microsoft.com/en-us/a1449178-b6fd-4ca8-a5e1-d747c2c54181)|<span data-ttu-id="405ee-122">Como o Windows PowerShell processa objetos.</span><span class="sxs-lookup"><span data-stu-id="405ee-122">How Windows PowerShell handles objects.</span></span>|
|[<span data-ttu-id="405ee-123">PowerShell do Windows estendido de sistema de tipos (ETS)</span><span class="sxs-lookup"><span data-stu-id="405ee-123">Windows PowerShell Extended Type System (ETS)</span></span>](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353)|<span data-ttu-id="405ee-124">Por meio de programação estender objetos.</span><span class="sxs-lookup"><span data-stu-id="405ee-124">Programmatically extending objects.</span></span>|

## <a name="see-also"></a><span data-ttu-id="405ee-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="405ee-125">See Also</span></span>

[<span data-ttu-id="405ee-126">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="405ee-126">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)