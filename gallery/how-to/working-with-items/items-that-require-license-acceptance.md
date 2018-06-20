---
ms.date: 06/12/2017
contributor: Farehar
keywords: Galeria do powershell, psgallery
title: Solicite a aceitação de licença
ms.openlocfilehash: 69787cdb12aa47223072551c9b68fc046573f022
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218404"
---
# <a name="require-license-acceptance"></a>Solicite a aceitação de licença

Necessitam de texto de aceitação de licença aparece na página de detalhes do item de módulos que solicite a aceitação de licença. Licença do módulo pode ser visualizada clicando na ligação 'Vista License.txt'.

![Solicite a aceitação de licença](../../Images/RequireLicenseAcceptance.png)

Serão solicitados aos utilizadores para aceitar a licença ao instalar, guardar ou atualizar o módulo através de PowerShellGet ou ao implementar a automatização do Azure.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Exigir a Aceitação da Licença ao Implementar a Automatização do Azure

Se o módulo que está a ser implementado para a automatização do Azure requer a aceitação de licença, a IU do portal mostrará uma indicação de exclusão de responsabilidade ' Este módulo requer a aceitação de licença. Ao clicar em OK, está a aceitar os termos de licenciamento.'

![Implementar no Azure automatização requer a aceitação de licença](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>obter mais detalhes

[Solicite a aceitação de licença no PowerShellGet](../../concepts/module-license-acceptance.md)
[Web site da automatização do Azure](/azure/automation)