---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058204"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="498a0-102">Separação dos IDs de Nó e de Configuração</span><span class="sxs-lookup"><span data-stu-id="498a0-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="498a0-103">Descrição geral</span><span class="sxs-lookup"><span data-stu-id="498a0-103">Overview</span></span>

<span data-ttu-id="498a0-104">Para fornecer uma experiência mais flexível e simplificada ao utilizar o DSC no modo de solicitação, adicionámos várias funcionalidades nesta versão.</span><span class="sxs-lookup"><span data-stu-id="498a0-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="498a0-105">Estas funcionalidades destinam-se para permitir que tem a flexibilidade de facilmente configurar e implementar configurações em vários nós, enquanto ainda controlar o estado e informações para cada nó de relatórios individualmente.</span><span class="sxs-lookup"><span data-stu-id="498a0-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="498a0-106">Esses recursos são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="498a0-106">These features are as follows:</span></span>

* <span data-ttu-id="498a0-107">Um nome de configuração que identifica a configuração de um computador.</span><span class="sxs-lookup"><span data-stu-id="498a0-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="498a0-108">Este nome pode ser partilhado por vários nós de destino</span><span class="sxs-lookup"><span data-stu-id="498a0-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="498a0-109">Um ID de agente que identifica exclusivamente um único nó</span><span class="sxs-lookup"><span data-stu-id="498a0-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="498a0-110">Um passo de registo que ocorre apenas na primeira vez que um nó de destino se liga a um servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="498a0-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="498a0-111">**Nota:** Esses recursos e funcionalidades foram adicionadas e não substituir o existente de solicitação de funcionalidades e conceitos.</span><span class="sxs-lookup"><span data-stu-id="498a0-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="498a0-112">Pode usar esses novos recursos ou antigos com o novo servidor de solicitação de envio nesta versão.</span><span class="sxs-lookup"><span data-stu-id="498a0-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="498a0-113">Para obter mais informações, consulte [como configurar um cliente de solicitação através de nomes de configuração](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="498a0-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
