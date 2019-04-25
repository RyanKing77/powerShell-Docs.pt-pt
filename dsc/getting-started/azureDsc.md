---
ms.date: 03/15/2018
keywords: DSC, powershell, configuração, a configuração
title: Utilizar o DSC no Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079885"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="49634-103">Utilizar o DSC no Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="49634-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="49634-104">Desired State Configuration (DSC) é suportada no Microsoft Azure através da [processador de extensões do Azure Desired State Configuration](/azure/virtual-machines/extensions/dsc-overview) e através de [DSC de automatização do Azure](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="49634-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="49634-105">Processador de extensões do Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="49634-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="49634-106">A extensão DSC do Azure permite VMs alojadas no Microsoft Azure para serem geridos com o DSC.</span><span class="sxs-lookup"><span data-stu-id="49634-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="49634-107">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="49634-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="49634-108">Processador de extensões do Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="49634-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="49634-109">VMSS do Windows e de Desired State Configuration com modelos Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="49634-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="49634-110">Passar credenciais para o manipulador de extensão DSC do Azure</span><span class="sxs-lookup"><span data-stu-id="49634-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="49634-111">Histórico da extensão Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="49634-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="49634-112">DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="49634-112">Azure Automation DSC</span></span>

<span data-ttu-id="49634-113">O [serviço de automatização do Azure](https://azure.microsoft.com/en-us/services/automation/) permite-lhe gerir configurações de DSC, recursos e nós geridos a partir do Azure.</span><span class="sxs-lookup"><span data-stu-id="49634-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="49634-114">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="49634-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="49634-115">DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="49634-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="49634-116">Introdução ao DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="49634-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="49634-117">Integrar computadores para gestão pelo DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="49634-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)