---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 5b9eea1c90bfd5a8cee3897d832bf7775a750308
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="932b6-102">Separação do nó e IDs de configuração</span><span class="sxs-lookup"><span data-stu-id="932b6-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="932b6-103">Descrição geral</span><span class="sxs-lookup"><span data-stu-id="932b6-103">Overview</span></span>

<span data-ttu-id="932b6-104">Para fornecer uma experiência mais flexível e simplificada quando o DSC no modo de extração, foi adicionado um número de funcionalidades nesta versão.</span><span class="sxs-lookup"><span data-stu-id="932b6-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="932b6-105">Estas funcionalidades são concebidas para permitir que tem a flexibilidade para configurar e implementar configurações em vários nós, enquanto ainda estado e comunicar informações para cada nó individualmente facilmente.</span><span class="sxs-lookup"><span data-stu-id="932b6-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span> <span data-ttu-id="932b6-106">Estas funcionalidades são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="932b6-106">These features are as follows:</span></span>

* <span data-ttu-id="932b6-107">Um nome de configuração que identifica a configuração de um computador.</span><span class="sxs-lookup"><span data-stu-id="932b6-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="932b6-108">Este nome pode ser partilhado por vários nós de destino</span><span class="sxs-lookup"><span data-stu-id="932b6-108">This name can be shared by multiple target nodes</span></span> 
* <span data-ttu-id="932b6-109">Um ID de agente que identifica exclusivamente um único nó</span><span class="sxs-lookup"><span data-stu-id="932b6-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="932b6-110">Um passo de registo que só ocorre pela primeira vez um nó de destino estabelece ligação a um servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="932b6-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="932b6-111">**Nota:** estas funções e funcionalidades foram adicionadas e não substituem os conceitos e funcionalidades existentes de extração.</span><span class="sxs-lookup"><span data-stu-id="932b6-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="932b6-112">Pode utilizar estas novas funcionalidades ou antigos com o novo servidor de solicitação envio nesta versão.</span><span class="sxs-lookup"><span data-stu-id="932b6-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="932b6-113">Para obter mais informações, consulte [configurar um cliente de solicitação utilizando nomes de configuração](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="932b6-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>

