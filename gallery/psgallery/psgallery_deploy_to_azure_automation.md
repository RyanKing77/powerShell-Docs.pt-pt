---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
<a name="deploy-to-azure-automation"></a>Implementar a automatização do Azure
===========================

A implementar no botão de automatização do Azure na página de detalhes do item irá implementar o item da galeria do PowerShell a automatização do Azure.

![Implementar no botão de automatização do Azure](Images/DeployToAzureAutomationButton.png)

Quando clica, este irá redirecioná-lo para o Portal de gestão do Azure, onde poderá iniciar sessão com as credenciais da conta do Azure.
Se o item inclui dependências, todas as dependências irão ser implementadas, bem como a automatização do Azure.

Aviso: Se o mesmo item e a versão já existirem na sua conta de automatização, implementar a política novamente da galeria do PowerShell irá substituir o item na sua conta de automatização.

Se implementar um módulo, será apresentada na secção de módulos da automatização do Azure.  Se implementar um script, será apresentada na secção de Runbooks da automatização do Azure.

A implementar no botão de automatização do Azure pode ser desativado através da adição de etiqueta AzureAutomationNotSupported para os metadados do item.

Para saber mais sobre a automatização do Azure, consulte o Web site da automatização do Azure [Web site da automatização do Azure](http://azure.microsoft.com/en-us/services/automation/).

