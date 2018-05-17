---
ms.date: 03/15/2018
keywords: DSC, do powershell, a configuração, a configuração
title: Utilizar o DSC no Microsoft Azure
ms.openlocfilehash: d35488c3f66895e930eaa84360f3d3ec9d74e9c7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="using-dsc-on-microsoft-azure"></a>Utilizar o DSC no Microsoft Azure

Estado de desired Configuration (DSC) é suportada no Microsoft Azure através de [processador de extensão de configuração de estado pretendido do Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) e através de [Automation DSC do Azure](/azure/automation/automation-dsc-overview).

## <a name="azure-desired-state-configuration-extension-handler"></a>Processador de extensão de configuração de estado da Desired do Azure

A extensão de DSC do Azure permite VMs alojadas no Microsoft Azure para serem geridos pelo DSC.
Para mais informações, consulte os seguintes tópicos:

- [Processador de extensão de configuração de estado da Desired do Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [Windows VMSS e configuração de estado pretendido com modelos Azure Resource Manager](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [Transmissão de credenciais para o processador de extensão de DSC do Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [Histórico de extensão de configuração de estado da Desired do Azure](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>DSC de automatização do Azure

O [serviço de automatização do Azure](https://azure.microsoft.com/services/automation/) permite-lhe gerir nós geridos a partir do Azure, recursos e configurações de DSC. Para mais informações, consulte os seguintes tópicos:

- [DSC de automatização do Azure](/azure/automation/automation-dsc-overview)
- [Introdução ao Azure Automation DSC](/azure/automation/automation-dsc-getting-started)
- [Máquinas de integração de gestão do Automation DSC do Azure](/azure/automation/automation-dsc-onboarding)