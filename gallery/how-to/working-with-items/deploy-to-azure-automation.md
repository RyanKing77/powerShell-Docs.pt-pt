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
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="eae52-103">Implementar a Automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="eae52-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="eae52-104">A implementar no botão de automatização do Azure na página de detalhes do item irá implementar o item da galeria do PowerShell a automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="eae52-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Implementar no botão de automatização do Azure](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="eae52-106">Quando clica, este irá redirecioná-lo para o Portal de gestão do Azure, onde poderá iniciar sessão com as credenciais da conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="eae52-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="eae52-107">Se o item inclui dependências, todas as dependências irão ser implementadas, bem como a automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="eae52-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="eae52-108">Se o mesmo item e a versão já existirem na sua conta de automatização, implementar a política novamente da galeria do PowerShell irá substituir o item na sua conta de automatização.</span><span class="sxs-lookup"><span data-stu-id="eae52-108">If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="eae52-109">Se implementar um módulo, será apresentada na secção de módulos da automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="eae52-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="eae52-110">Se implementar um script, será apresentada na secção de Runbooks da automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="eae52-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="eae52-111">A implementar no botão de automatização do Azure pode ser desativado através da adição de etiqueta AzureAutomationNotSupported para os metadados do item.</span><span class="sxs-lookup"><span data-stu-id="eae52-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="eae52-112">Exigir a Aceitação da Licença ao Implementar a Automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="eae52-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="eae52-113">Se o módulo que está a ser implementado para a automatização do Azure requer a aceitação de licença, a IU do portal mostrará uma indicação de exclusão de responsabilidade ' Este módulo requer a aceitação de licença.</span><span class="sxs-lookup"><span data-stu-id="eae52-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="eae52-114">Ao clicar em OK, está a aceitar os termos de licenciamento.'</span><span class="sxs-lookup"><span data-stu-id="eae52-114">By clicking OK, you are accepting license terms.'</span></span>

![Implementar no Azure automatização requer a aceitação de licença](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="eae52-116">obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="eae52-116">More details</span></span>

- [<span data-ttu-id="eae52-117">Solicite a aceitação de licença no PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="eae52-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="eae52-118">Solicite a aceitação de licença na galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="eae52-118">Require License Acceptance in PowerShell Gallery</span></span>](items-that-require-license-acceptance.md)
- [<span data-ttu-id="eae52-119">Site de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="eae52-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
