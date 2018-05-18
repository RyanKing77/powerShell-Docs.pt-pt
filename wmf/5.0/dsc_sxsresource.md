---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="dd99e-102">Suporte de controlo de versões de módulo de lado a lado dos recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="dd99e-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="dd99e-103">Os módulos que contêm recursos de DSC podem ser instalados lado a lado e configurações de DSC podem utilizar uma versão específica do recurso que está instalado no sistema.</span><span class="sxs-lookup"><span data-stu-id="dd99e-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="dd99e-104">Para obter mais informações, consulte [através de recursos com várias versões](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="dd99e-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="dd99e-105">Problemas conhecidos</span><span class="sxs-lookup"><span data-stu-id="dd99e-105">Known issues</span></span>

<span data-ttu-id="dd99e-106">Nesta versão, os seguintes são problemas conhecidos da instalação lado a lado:</span><span class="sxs-lookup"><span data-stu-id="dd99e-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="dd99e-107">Não é suportada a utilizar duas versões diferentes do recurso dentro da mesma configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="dd99e-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
