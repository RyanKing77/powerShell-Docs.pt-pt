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
<a name="deploy-to-azure-automation"></a><span data-ttu-id="1dc6a-103">Implementar a automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="1dc6a-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="1dc6a-104">A implementar no botão de automatização do Azure na página de detalhes do item irá implementar o item da galeria do PowerShell a automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="1dc6a-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Implementar no botão de automatização do Azure](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="1dc6a-106">Quando clica, este irá redirecioná-lo para o Portal de gestão do Azure, onde poderá iniciar sessão com as credenciais da conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="1dc6a-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="1dc6a-107">Se o item inclui dependências, todas as dependências irão ser implementadas, bem como a automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="1dc6a-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="1dc6a-108">Aviso: Se o mesmo item e a versão já existirem na sua conta de automatização, implementar a política novamente da galeria do PowerShell irá substituir o item na sua conta de automatização.</span><span class="sxs-lookup"><span data-stu-id="1dc6a-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="1dc6a-109">Se implementar um módulo, será apresentada na secção de módulos da automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="1dc6a-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="1dc6a-110">Se implementar um script, será apresentada na secção de Runbooks da automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="1dc6a-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="1dc6a-111">A implementar no botão de automatização do Azure pode ser desativado através da adição de etiqueta AzureAutomationNotSupported para os metadados do item.</span><span class="sxs-lookup"><span data-stu-id="1dc6a-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="1dc6a-112">Para saber mais sobre a automatização do Azure, consulte o Web site da automatização do Azure [Web site da automatização do Azure](http://azure.microsoft.com/en-us/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="1dc6a-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/en-us/services/automation/).</span></span>

