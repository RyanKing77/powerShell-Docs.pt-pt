---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 6c036c2d8f97e559d20dd3ac40133fa06f5dab08
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="0a5c0-102">Separação dos IDs de Nó e de Configuração</span><span class="sxs-lookup"><span data-stu-id="0a5c0-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="0a5c0-103">Descrição geral</span><span class="sxs-lookup"><span data-stu-id="0a5c0-103">Overview</span></span>

<span data-ttu-id="0a5c0-104">Para fornecer uma experiência mais flexível e simplificada quando o DSC no modo de extração, foi adicionado um número de funcionalidades nesta versão.</span><span class="sxs-lookup"><span data-stu-id="0a5c0-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="0a5c0-105">Estas funcionalidades são concebidas para permitir que tem a flexibilidade para configurar e implementar configurações em vários nós, enquanto ainda estado e comunicar informações para cada nó individualmente facilmente.</span><span class="sxs-lookup"><span data-stu-id="0a5c0-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="0a5c0-106">Estas funcionalidades são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="0a5c0-106">These features are as follows:</span></span>

* <span data-ttu-id="0a5c0-107">Um nome de configuração que identifica a configuração de um computador.</span><span class="sxs-lookup"><span data-stu-id="0a5c0-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="0a5c0-108">Este nome pode ser partilhado por vários nós de destino</span><span class="sxs-lookup"><span data-stu-id="0a5c0-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="0a5c0-109">Um ID de agente que identifica exclusivamente um único nó</span><span class="sxs-lookup"><span data-stu-id="0a5c0-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="0a5c0-110">Um passo de registo que só ocorre pela primeira vez um nó de destino estabelece ligação a um servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="0a5c0-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="0a5c0-111">**Nota:** estas funções e funcionalidades foram adicionadas e não substituem os conceitos e funcionalidades existentes de extração.</span><span class="sxs-lookup"><span data-stu-id="0a5c0-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="0a5c0-112">Pode utilizar estas novas funcionalidades ou antigos com o novo servidor de solicitação envio nesta versão.</span><span class="sxs-lookup"><span data-stu-id="0a5c0-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="0a5c0-113">Para obter mais informações, consulte [configurar um cliente de solicitação utilizando nomes de configuração](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="0a5c0-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
