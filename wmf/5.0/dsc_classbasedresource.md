---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685754"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="d3e6f-102">Recursos de DSC baseados em classes</span><span class="sxs-lookup"><span data-stu-id="d3e6f-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="d3e6f-103">Definir os recursos de DSC com classes</span><span class="sxs-lookup"><span data-stu-id="d3e6f-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="d3e6f-104">Com base nos comentários, fizemos-se a criação de recursos de DSC baseados na classe mais simples e mais fácil de entender.</span><span class="sxs-lookup"><span data-stu-id="d3e6f-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="d3e6f-105">As principais diferenças entre um recurso de DSC baseados na classe e um fornecedor de recursos de DSC de cmdlet são:</span><span class="sxs-lookup"><span data-stu-id="d3e6f-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="d3e6f-106">Não é necessário um ficheiro MOF para o esquema.</span><span class="sxs-lookup"><span data-stu-id="d3e6f-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="d3e6f-107">R **DSCResource** subpasta da pasta do módulo não é necessária.</span><span class="sxs-lookup"><span data-stu-id="d3e6f-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="d3e6f-108">Um arquivo de módulo do PowerShell pode conter várias classes de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="d3e6f-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="d3e6f-109">Para obter mais informações, consulte [escrever um recurso personalizado do DSC com classes do PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="d3e6f-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
