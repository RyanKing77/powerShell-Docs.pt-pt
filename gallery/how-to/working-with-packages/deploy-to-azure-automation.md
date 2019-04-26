---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Implementar a Automatização do Azure
ms.openlocfilehash: dc382b1cf3ceaa787f54c555d01e6bd9ba70e680
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084895"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="bd992-103">Implementar a Automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="bd992-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="bd992-104">A implementar no botão de automatização do Azure na página de detalhes do pacote irá implementar o pacote a partir da galeria do PowerShell para a automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="bd992-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![Implementar no botão de automatização do Azure](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="bd992-106">Quando clicado, este irá redirecioná-lo ao Portal de gestão do Azure, onde iniciar sessão com as suas credenciais de conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="bd992-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="bd992-107">Se o pacote inclui dependências, todas as dependências serão implementadas para automatização do Azure também.</span><span class="sxs-lookup"><span data-stu-id="bd992-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="bd992-108">Se o pacote e versão mesmo já existam na sua conta de automatização, implantando-o novamente a partir da galeria do PowerShell irá substituir o pacote na sua conta de automatização.</span><span class="sxs-lookup"><span data-stu-id="bd992-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="bd992-109">Se implementar um módulo, ele será exibido na seção de módulos da automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="bd992-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="bd992-110">Se implementar um script, ele será exibido na secção de Runbooks da automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="bd992-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="bd992-111">A implementar no botão de automatização do Azure pode ser desativado ao adicionar a marca de AzureAutomationNotSupported para os metadados do pacote.</span><span class="sxs-lookup"><span data-stu-id="bd992-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="bd992-112">Exigir a Aceitação da Licença ao Implementar a Automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="bd992-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="bd992-113">Se o módulo a ser implementado para automatização do Azure requer a aceitação da licença, a IU do portal mostrará uma indicação de isenção de responsabilidade ' Este módulo requer a aceitação da licença.</span><span class="sxs-lookup"><span data-stu-id="bd992-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="bd992-114">Ao clicar em OK, está a aceitar estes termos de licenciamento. "</span><span class="sxs-lookup"><span data-stu-id="bd992-114">By clicking OK, you are accepting license terms.'</span></span>

![Implementar no Azure a automação requer a aceitação da licença](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="bd992-116">Obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="bd992-116">More details</span></span>

- [<span data-ttu-id="bd992-117">Exigir a aceitação da licença no PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bd992-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="bd992-118">Exigir a aceitação da licença na galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd992-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="bd992-119">Web site de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="bd992-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
