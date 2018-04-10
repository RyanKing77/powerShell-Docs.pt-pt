---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgallery_unlist_items
ms.openlocfilehash: af48f2ca889dcc101d466e40f2ecbe0cdf62c066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="unlisting-items"></a><span data-ttu-id="758a5-103">Remover itens da lista</span><span class="sxs-lookup"><span data-stu-id="758a5-103">Unlisting items</span></span>

<span data-ttu-id="758a5-104">**Razão pela qual está a remover um item da galeria do PowerShell não exposta como uma opção?**</span><span class="sxs-lookup"><span data-stu-id="758a5-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="758a5-105">A galeria do PowerShell não suporta utilizadores eliminados permanentemente os itens.</span><span class="sxs-lookup"><span data-stu-id="758a5-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="758a5-106">Isto permite que os outros possam desempenhar as dependências dos itens sem se preocupar quebras possíveis no futuro.</span><span class="sxs-lookup"><span data-stu-id="758a5-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="758a5-107">Por exemplo, se o módulo de Pester depende do módulo do Azure e o módulo do Azure é removido do galeria, em seguida, o utilizador pode já não utiliza o módulo de Pester.</span><span class="sxs-lookup"><span data-stu-id="758a5-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="758a5-108">Em vez de um item a remover, no entanto, é pode unlist-lo em vez disso.</span><span class="sxs-lookup"><span data-stu-id="758a5-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="758a5-109">**O que faz unlisting um item na galeria do PowerShell fazer?**</span><span class="sxs-lookup"><span data-stu-id="758a5-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="758a5-110">Unlisting um item como módulo ou script na galeria do PowerShell irá removê-lo no separador itens. Além disso, não listados itens deixarão de estar Detetáveis utilizando a barra de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="758a5-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="758a5-111">É a única forma de transferir um item não listado para especificar o nome exato e a versão do item.</span><span class="sxs-lookup"><span data-stu-id="758a5-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="758a5-112">Por este motivo, unlisting de um item não irão interromper a outros módulos ou scripts que dependem dele.</span><span class="sxs-lookup"><span data-stu-id="758a5-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="758a5-113">Para unlist o item, visite a página de detalhes do item e selecione 'Eliminar Item'.</span><span class="sxs-lookup"><span data-stu-id="758a5-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="758a5-114">Desmarque a caixa de verificação 'Apresentados' e clique em Guardar.</span><span class="sxs-lookup"><span data-stu-id="758a5-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="758a5-115">**Como posso remover um item?**</span><span class="sxs-lookup"><span data-stu-id="758a5-115">**How can I remove an item?**</span></span>

<span data-ttu-id="758a5-116">Se ocorrer um cenário em que a eliminação do item é necessária, contacte os administradores de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="758a5-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="758a5-117">Cenários de eliminação válidos são:</span><span class="sxs-lookup"><span data-stu-id="758a5-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="758a5-118">Problemas de violação de direitos de autor.</span><span class="sxs-lookup"><span data-stu-id="758a5-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="758a5-119">Item contém conteúdo potencialmente prejudicial.</span><span class="sxs-lookup"><span data-stu-id="758a5-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="758a5-120">O item contém dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="758a5-120">Item contains sensitive data.</span></span>

<span data-ttu-id="758a5-121">Para submeter um eliminar o Item pedido aos administradores de galeria do PowerShell, visite a página de detalhes do item e selecione contacte o suporte.</span><span class="sxs-lookup"><span data-stu-id="758a5-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>