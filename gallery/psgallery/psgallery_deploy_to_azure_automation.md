---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 8da4eabead6a419dc0c01c74335c06bf8be25d0c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
<a name="deploy-to-azure-automation"></a>Implementar a Automatização do Azure
===========================

A implementar no botão de automatização do Azure na página de detalhes do item irá implementar o item da galeria do PowerShell a automatização do Azure.

![Implementar no botão de automatização do Azure](Images/DeployToAzureAutomationButton.png)

Quando clica, este irá redirecioná-lo para o Portal de gestão do Azure, onde poderá iniciar sessão com as credenciais da conta do Azure.
Se o item inclui dependências, todas as dependências irão ser implementadas, bem como a automatização do Azure.

Aviso: Se o mesmo item e a versão já existirem na sua conta de automatização, implementar a política novamente da galeria do PowerShell irá substituir o item na sua conta de automatização.

Se implementar um módulo, será apresentada na secção de módulos da automatização do Azure.  Se implementar um script, será apresentada na secção de Runbooks da automatização do Azure.

A implementar no botão de automatização do Azure pode ser desativado através da adição de etiqueta AzureAutomationNotSupported para os metadados do item.

Para saber mais sobre a automatização do Azure, consulte o Web site da automatização do Azure [Web site da automatização do Azure](http://azure.microsoft.com/services/automation/).