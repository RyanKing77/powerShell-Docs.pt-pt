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
# <a name="using-dsc-on-microsoft-azure"></a>Utilizar o DSC no Microsoft Azure

Desired State Configuration (DSC) é suportada no Microsoft Azure através da [processador de extensões do Azure Desired State Configuration](/azure/virtual-machines/extensions/dsc-overview) e através de [DSC de automatização do Azure](/azure/automation/automation-dsc-overview).

## <a name="azure-desired-state-configuration-extension-handler"></a>Processador de extensões do Azure Desired State Configuration

A extensão DSC do Azure permite VMs alojadas no Microsoft Azure para serem geridos com o DSC.
Para mais informações, consulte os seguintes tópicos:

- [Processador de extensões do Azure Desired State Configuration](/azure/virtual-machines/extensions/dsc-overview)
- [VMSS do Windows e de Desired State Configuration com modelos Azure Resource Manager](/azure/virtual-machines/extensions/dsc-template)
- [Passar credenciais para o manipulador de extensão DSC do Azure](/azure/virtual-machines/extensions/dsc-credentials)
- [Histórico da extensão Azure Desired State Configuration](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>DSC de automatização do Azure

O [serviço de automatização do Azure](https://azure.microsoft.com/en-us/services/automation/) permite-lhe gerir configurações de DSC, recursos e nós geridos a partir do Azure. Para mais informações, consulte os seguintes tópicos:

- [DSC de automatização do Azure](/azure/automation/automation-dsc-overview)
- [Introdução ao DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started)
- [Integrar computadores para gestão pelo DSC de automatização do Azure](/azure/automation/automation-dsc-onboarding)