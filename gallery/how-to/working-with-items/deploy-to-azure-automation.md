---
ms.date: 06/12/2017
contributor: JKeithB
keywords: cmdlet do powershell do galeria, psgallery
title: Implementar a Automatização do Azure
ms.openlocfilehash: ced67809387a85e089259edf6b091d68e58ba6a7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-to-azure-automation"></a>Implementar a Automatização do Azure

A implementar no botão de automatização do Azure na página de detalhes do item irá implementar o item da galeria do PowerShell a automatização do Azure.

![Implementar no botão de automatização do Azure](../../Images/DeployToAzureAutomationButton.png)

Quando clica, este irá redirecioná-lo para o Portal de gestão do Azure, onde poderá iniciar sessão com as credenciais da conta do Azure.
Se o item inclui dependências, todas as dependências irão ser implementadas, bem como a automatização do Azure.

> [!WARNING]
> Se o mesmo item e a versão já existirem na sua conta de automatização, implementar a política novamente da galeria do PowerShell irá substituir o item na sua conta de automatização.

Se implementar um módulo, será apresentada na secção de módulos da automatização do Azure.  Se implementar um script, será apresentada na secção de Runbooks da automatização do Azure.

A implementar no botão de automatização do Azure pode ser desativado através da adição de etiqueta AzureAutomationNotSupported para os metadados do item.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Exigir a Aceitação da Licença ao Implementar a Automatização do Azure

Se o módulo que está a ser implementado para a automatização do Azure requer a aceitação de licença, a IU do portal mostrará uma indicação de exclusão de responsabilidade ' Este módulo requer a aceitação de licença. Ao clicar em OK, está a aceitar os termos de licenciamento.'

![Implementar no Azure automatização requer a aceitação de licença](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>obter mais detalhes

- [Solicite a aceitação de licença no PowerShellGet](../../concepts/module-license-acceptance.md)
- [Solicite a aceitação de licença na galeria do PowerShell](items-that-require-license-acceptance.md)
- [Site de automatização do Azure](http://azure.microsoft.com/services/automation/)
