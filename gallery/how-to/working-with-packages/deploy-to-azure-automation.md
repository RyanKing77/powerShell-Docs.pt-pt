---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Implementar a Automatização do Azure
ms.openlocfilehash: dc382b1cf3ceaa787f54c555d01e6bd9ba70e680
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004142"
---
# <a name="deploy-to-azure-automation"></a>Implementar a Automatização do Azure

A implementar no botão de automatização do Azure na página de detalhes do pacote irá implementar o pacote a partir da galeria do PowerShell para a automatização do Azure.

![Implementar no botão de automatização do Azure](../../Images/DeployToAzureAutomationButton.png)

Quando clicado, este irá redirecioná-lo ao Portal de gestão do Azure, onde iniciar sessão com as suas credenciais de conta do Azure.
Se o pacote inclui dependências, todas as dependências serão implementadas para automatização do Azure também.

> [!WARNING]
> Se o pacote e versão mesmo já existam na sua conta de automatização, implantando-o novamente a partir da galeria do PowerShell irá substituir o pacote na sua conta de automatização.

Se implementar um módulo, ele será exibido na seção de módulos da automatização do Azure.  Se implementar um script, ele será exibido na secção de Runbooks da automatização do Azure.

A implementar no botão de automatização do Azure pode ser desativado ao adicionar a marca de AzureAutomationNotSupported para os metadados do pacote.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Exigir a Aceitação da Licença ao Implementar a Automatização do Azure

Se o módulo a ser implementado para automatização do Azure requer a aceitação da licença, a IU do portal mostrará uma indicação de isenção de responsabilidade ' Este módulo requer a aceitação da licença. Ao clicar em OK, está a aceitar estes termos de licenciamento. "

![Implementar no Azure a automação requer a aceitação da licença](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Obter mais detalhes

- [Exigir a aceitação da licença no PowerShellGet](../../concepts/module-license-acceptance.md)
- [Exigir a aceitação da licença na galeria do PowerShell](packages-that-require-license-acceptance.md)
- [Web site de automatização do Azure](http://azure.microsoft.com/services/automation/)
