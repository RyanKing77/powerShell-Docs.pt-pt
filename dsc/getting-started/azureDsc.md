---
ms.date: 03/15/2018
keywords: DSC, powershell, configuração, a configuração
title: Utilizar o DSC no Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404653"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="0ef10-103">Utilizar o DSC no Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="0ef10-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="0ef10-104">Desired State Configuration (DSC) é suportada no Microsoft Azure através da [processador de extensões do Azure Desired State Configuration](/azure/virtual-machines/extensions/dsc-overview) e através de [DSC de automatização do Azure](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="0ef10-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="0ef10-105">Processador de extensões do Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="0ef10-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="0ef10-106">A extensão DSC do Azure permite VMs alojadas no Microsoft Azure para serem geridos com o DSC.</span><span class="sxs-lookup"><span data-stu-id="0ef10-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="0ef10-107">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="0ef10-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="0ef10-108">Processador de extensões do Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="0ef10-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="0ef10-109">VMSS do Windows e de Desired State Configuration com modelos Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="0ef10-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="0ef10-110">Passar credenciais para o manipulador de extensão DSC do Azure</span><span class="sxs-lookup"><span data-stu-id="0ef10-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="0ef10-111">Histórico da extensão Azure Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="0ef10-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="0ef10-112">DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="0ef10-112">Azure Automation DSC</span></span>

<span data-ttu-id="0ef10-113">O [serviço de automatização do Azure](https://azure.microsoft.com/en-us/services/automation/) permite-lhe gerir configurações de DSC, recursos e nós geridos a partir do Azure.</span><span class="sxs-lookup"><span data-stu-id="0ef10-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="0ef10-114">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="0ef10-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="0ef10-115">DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="0ef10-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="0ef10-116">Introdução ao DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="0ef10-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="0ef10-117">Integrar computadores para gestão pelo DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="0ef10-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)