---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="293bb-102">Recursos de DSC com base na classe</span><span class="sxs-lookup"><span data-stu-id="293bb-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="293bb-103">Definir os recursos de DSC com classes</span><span class="sxs-lookup"><span data-stu-id="293bb-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="293bb-104">Com base nos comentários, que fizemos criação de recursos de DSC com base na classe mais simples e mais fácil de compreender.</span><span class="sxs-lookup"><span data-stu-id="293bb-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span> <span data-ttu-id="293bb-105">As principais diferenças entre um recurso de DSC com base na classe e um fornecedor de recursos de DSC de cmdlet são:</span><span class="sxs-lookup"><span data-stu-id="293bb-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="293bb-106">Não é necessário um ficheiro MOF para o esquema.</span><span class="sxs-lookup"><span data-stu-id="293bb-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="293bb-107">A **DSCResource** subpasta da pasta do módulo não é necessária.</span><span class="sxs-lookup"><span data-stu-id="293bb-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="293bb-108">Um ficheiro de módulo do PowerShell pode conter várias classes de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="293bb-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="293bb-109">Para obter mais informações, consulte [escrever um recurso personalizado de DSC com classes de PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="293bb-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>

