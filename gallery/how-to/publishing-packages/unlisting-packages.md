---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Remover pacotes
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004173"
---
# <a name="unlisting-packages"></a><span data-ttu-id="ba1a9-103">Pacotes unlisting</span><span class="sxs-lookup"><span data-stu-id="ba1a9-103">Unlisting Packages</span></span>

<span data-ttu-id="ba1a9-104">**Por isso que está a remover um pacote de galeria do PowerShell não é exposto como uma opção?**</span><span class="sxs-lookup"><span data-stu-id="ba1a9-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="ba1a9-105">A galeria do PowerShell não suporta utilizadores serem eliminados permanentemente a seus pacotes.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="ba1a9-106">Isto permite que outros possam assumir dependências de seus pacotes sem se preocupar sobre quebras de possíveis no futuro.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="ba1a9-107">Por exemplo, se o módulo de Pester depende do módulo do Azure e o módulo do Azure é removido a partir da galeria, em seguida, o utilizador pode já não utiliza o módulo de Pester.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="ba1a9-108">Em vez de remover um pacote, no entanto, pode unlist-lo em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-108">Instead of removing an package, however, you can unlist it instead.</span></span>

<span data-ttu-id="ba1a9-109">**O que faz a remover um pacote na galeria do PowerShell fazer?**</span><span class="sxs-lookup"><span data-stu-id="ba1a9-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="ba1a9-110">Remover um pacote, como o módulo ou scripts numa galeria do PowerShell irá removê-lo do separador de pacotes. Além disso, os pacotes não listados não será Detetáveis através da barra de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-110">Unlisting a package such as module or script on PowerShell Gallery will remove it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="ba1a9-111">A única forma de transferir um pacote não listado é especificar o nome exato e a versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="ba1a9-112">Por este motivo, a remover de um pacote não irão interromper a outros módulos ou scripts que dependem dele.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-112">Because of this, the unlisting of an package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="ba1a9-113">Unlist seu pacote, visite a página de detalhes do pacote e selecione 'Eliminar módulo'.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="ba1a9-114">Desmarque a caixa de verificação "Apresentados" e clique em Guardar.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="ba1a9-115">**Como posso remover um pacote?**</span><span class="sxs-lookup"><span data-stu-id="ba1a9-115">**How can I remove an package?**</span></span>

<span data-ttu-id="ba1a9-116">Se tiver um cenário em que a eliminação do pacote é necessária, contacte os administradores de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="ba1a9-117">Cenários de eliminação válidos são:</span><span class="sxs-lookup"><span data-stu-id="ba1a9-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="ba1a9-118">Problemas de infração de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="ba1a9-119">Pacote contém conteúdo potencialmente prejudicial.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="ba1a9-120">Pacote contém dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-120">Package contains sensitive data.</span></span>

<span data-ttu-id="ba1a9-121">Para submeter um eliminar pedidos de pacote para os administradores de galeria do PowerShell, visite a página de detalhes do seu pacote e selecione contacte o suporte.</span><span class="sxs-lookup"><span data-stu-id="ba1a9-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
