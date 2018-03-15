---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Utilizar o DSC no Microsoft Azure
ms.openlocfilehash: d164fc107ec9fecbb8e399d0089501cababde8c4
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="7710c-103">Utilizar o DSC no Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="7710c-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="7710c-104">Estado de desired Configuration (DSC) é suportada no Microsoft Azure através de [processador de extensão de configuração de estado pretendido do Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) e através de [Automation DSC do Azure](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="7710c-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="7710c-105">Processador de extensão de configuração de estado da Desired do Azure</span><span class="sxs-lookup"><span data-stu-id="7710c-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="7710c-106">A extensão de DSC do Azure permite VMs alojadas no Microsoft Azure para serem geridos pelo DSC.</span><span class="sxs-lookup"><span data-stu-id="7710c-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span> <span data-ttu-id="7710c-107">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="7710c-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="7710c-108">Processador de extensão de configuração de estado da Desired do Azure</span><span class="sxs-lookup"><span data-stu-id="7710c-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [<span data-ttu-id="7710c-109">Windows VMSS e configuração de estado pretendido com modelos Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="7710c-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [<span data-ttu-id="7710c-110">Transmissão de credenciais para o processador de extensão de DSC do Azure</span><span class="sxs-lookup"><span data-stu-id="7710c-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [<span data-ttu-id="7710c-111">Histórico de extensão de configuração de estado da Desired do Azure</span><span class="sxs-lookup"><span data-stu-id="7710c-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="7710c-112">DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="7710c-112">Azure Automation DSC</span></span>

<span data-ttu-id="7710c-113">O [serviço de automatização do Azure](/services/automation/) permite-lhe gerir nós geridos a partir do Azure, recursos e configurações de DSC.</span><span class="sxs-lookup"><span data-stu-id="7710c-113">The [Azure Automation service](/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="7710c-114">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="7710c-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="7710c-115">DSC de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="7710c-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="7710c-116">Introdução ao Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="7710c-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="7710c-117">Máquinas de integração de gestão do Automation DSC do Azure</span><span class="sxs-lookup"><span data-stu-id="7710c-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)

