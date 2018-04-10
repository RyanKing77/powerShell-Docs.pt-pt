---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgallery_status
ms.openlocfilehash: 08d09ce83b5133598152186e12fc8ced90c36a88
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a><span data-ttu-id="9a343-103">Estado de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a343-103">PowerShell Gallery Status</span></span>
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a><span data-ttu-id="9a343-104">10/10/2017 - galeria do PowerShell disponível para 2 horas 10/10/17</span><span class="sxs-lookup"><span data-stu-id="9a343-104">10/10/2017 - PowerShell Gallery unavailable for 2 hours 10/10/17</span></span>

<span data-ttu-id="9a343-105">__Resumo de impacto__: A Galeria do PowerShell teve um período de latência muito elevado, resultando em problemas de ligação intermitente, a partir, aproximadamente, as 17: 00 (PDT) 10/10/17.</span><span class="sxs-lookup"><span data-stu-id="9a343-105">__Summary of Impact__: The PowerShell Gallery experienced a period of very high latency, resulting in intermittent connection issues, beginning approximately 5pm (PDT) 10/10/17.</span></span> <span data-ttu-id="9a343-106">Ao resolver o problema, o site foi colocado offline para 2 horas iniciar aproximadamente as 22: 00 (PDT).</span><span class="sxs-lookup"><span data-stu-id="9a343-106">While resolving the issue, the site was taken offline for 2 hours starting approximately 10pm (PDT).</span></span> <span data-ttu-id="9a343-107">O site foi restaurado pouco tempo antes de à meia-noite 10/10/2017.</span><span class="sxs-lookup"><span data-stu-id="9a343-107">The site was restored shortly before midnight 10/10/2017.</span></span>

<span data-ttu-id="9a343-108">__Causa raiz__: A causa raiz a latência elevada ainda está a ser investigada.</span><span class="sxs-lookup"><span data-stu-id="9a343-108">__Root Cause__: The root cause of the high latency is still being investigated.</span></span>

<span data-ttu-id="9a343-109">__Resolução__: os serviços web que tiveram de ser colocado offline e restaurado para resolver o problema principal.</span><span class="sxs-lookup"><span data-stu-id="9a343-109">__Resolution__: The web services had to be taken offline and restored in order to address the primary issue.</span></span>

<span data-ttu-id="9a343-110">__Próximos passos__: A causa de raiz para o problema original que está a ser investigada.</span><span class="sxs-lookup"><span data-stu-id="9a343-110">__Next Steps__: The root cause for the original issue is being investigated.</span></span>

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="9a343-111">01/06/2017 - implementar para a automatização do Azure não está disponível</span><span class="sxs-lookup"><span data-stu-id="9a343-111">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="9a343-112">__Resumo de impacto__: implementar itens com as dependências de automatização do Azure da galeria do PowerShell está atualmente indisponível.</span><span class="sxs-lookup"><span data-stu-id="9a343-112">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="9a343-113">Importar itens da galeria do PowerShell de dentro da automatização do Azure ainda está disponível.</span><span class="sxs-lookup"><span data-stu-id="9a343-113">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>

<span data-ttu-id="9a343-114">__Causa raiz__: itens que terem dependências de outros utilizadores e de ter sido implementadas anteriormente a automatização do Azure, não serão possível implementar a automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="9a343-114">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="9a343-115">Engenheiros de tem identificado um problema com a forma como modelos ARM são gerados para itens com dependências para implementar a funcionalidade de automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="9a343-115">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="9a343-116">__Resolução__: engenheiros estiver a trabalhar para resolver o problema.</span><span class="sxs-lookup"><span data-stu-id="9a343-116">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="9a343-117">A solução atual para os utilizadores é para importar o item da galeria do PowerShell a partir de dentro da automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="9a343-117">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span>

<span data-ttu-id="9a343-118">__Próximos passos__: engenheiros de libertar a correção em breve.</span><span class="sxs-lookup"><span data-stu-id="9a343-118">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="9a343-119">Entretanto, utilize a solução recomendada.</span><span class="sxs-lookup"><span data-stu-id="9a343-119">In the meantime, please use the recommended workaround.</span></span>


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="9a343-120">04/11/2017 - os utilizadores não é possível iniciar sessão com contas do Azure Active Directory (AAD)</span><span class="sxs-lookup"><span data-stu-id="9a343-120">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="9a343-121">__Resumo de impacto__: alguns utilizadores não conseguiram iniciar sessão na galeria do PowerShell com contas do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="9a343-121">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span>

<span data-ttu-id="9a343-122">__Causa raiz__: durante uma atualização para interagir com mais segurança no AAD, uma alteração da definição foi perdida.</span><span class="sxs-lookup"><span data-stu-id="9a343-122">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span>
<span data-ttu-id="9a343-123">O teste concluído para validar a alteração não incluiu determinados tipos de contas do AAD, pelo que a implementação proceeded.</span><span class="sxs-lookup"><span data-stu-id="9a343-123">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="9a343-124">__Resolução__: engenheiros identificou a definição em falta e corrigiu o problema.</span><span class="sxs-lookup"><span data-stu-id="9a343-124">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span>

<span data-ttu-id="9a343-125">__Próximos passos__: podemos irá modificar nosso teste para incluir um conjunto alargado de tipos de contas do AAD.</span><span class="sxs-lookup"><span data-stu-id="9a343-125">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="9a343-126">27/03/2017 - RESOLVIDO: não é possível ver páginas individuais, módulo e scripts</span><span class="sxs-lookup"><span data-stu-id="9a343-126">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="9a343-127">__Resumo de impacto__: direcionar ligações para páginas individuais, módulo e script no https://www.powershellgallery.com foram interrompidas.</span><span class="sxs-lookup"><span data-stu-id="9a343-127">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="9a343-128">Isto foi reportado em todas as regiões.</span><span class="sxs-lookup"><span data-stu-id="9a343-128">This was being reported across all the regions.</span></span> <span data-ttu-id="9a343-129">Isto não afetar qualquer um dos PowerShellGet cmdlets ie., módulo de instalação, o Script de atualização, publicar-Module, de Script de instalação, atualização-Module, publicar-Scirpt continuou a trabalhar.</span><span class="sxs-lookup"><span data-stu-id="9a343-129">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="9a343-130">__Causa raiz__: engenheiros de identificar a causa como um problema ao chamar botões como o Facebook para a página de redes sociais.</span><span class="sxs-lookup"><span data-stu-id="9a343-130">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>

<span data-ttu-id="9a343-131">__Resolução__: engenheiros de corrigido o problema, desativando as informações de contagem do Facebook.</span><span class="sxs-lookup"><span data-stu-id="9a343-131">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="9a343-132">__Próximos passos__: foi aberto um problema de controlo interno para corrigir o nosso utilização da API do Facebook.</span><span class="sxs-lookup"><span data-stu-id="9a343-132">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="9a343-133">15/12/2016 - não é possível enviar mensagens de correio eletrónico através do Web site de PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="9a343-133">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="9a343-134">__Resumo de impacto__: entre 13/12/2016 e 15/12/2016, as mensagens enviadas por proprietários de contacto, Gerir proprietários, contacte o suporte ou abuso do relatório não foram recebidas por administradores de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a343-134">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="9a343-135">__Causa raiz__: engenheiros de identificar a causa como um problema de autenticação com o servidor de SMTP.</span><span class="sxs-lookup"><span data-stu-id="9a343-135">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>
<span data-ttu-id="9a343-136">__Resolução__: engenheiros foram capazes de resolver o problema de autenticação e restaurar a ligação ao servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="9a343-136">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>
<span data-ttu-id="9a343-137">__Próximos passos__: Se utilizou as ligações de proprietários de contacto, Gerir proprietários, contacte o suporte ou relatório abuso para enviar correio para cgadmin@microsoft.com durante este tempo e não tenham respondeu, volte a tentar.</span><span class="sxs-lookup"><span data-stu-id="9a343-137">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="9a343-138">Pedimos desculpa pelo incómodo.</span><span class="sxs-lookup"><span data-stu-id="9a343-138">We apologize for the inconvenience.</span></span>



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="9a343-139">8/10/2016 - resolvido: não é possível enviar e-mails para cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="9a343-139">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="9a343-140">__Resumo de impacto__: entre 8/5/2016 e 8/10/2016, os clientes não conseguiram enviar e-mails para cgadmin@microsoft.com, ou utilizar a funcionalidade contacte-nos.</span><span class="sxs-lookup"><span data-stu-id="9a343-140">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>
<span data-ttu-id="9a343-141">__Causa raiz__: engenheiros de identificar a causa como uma alteração da configuração da conta de e-mail.</span><span class="sxs-lookup"><span data-stu-id="9a343-141">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>
<span data-ttu-id="9a343-142">__Resolução__: engenheiros trabalhado para resolver o problema de configuração.</span><span class="sxs-lookup"><span data-stu-id="9a343-142">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>
<span data-ttu-id="9a343-143">__Próximos passos__: se utilizado na ligação contacte-nos ou enviar correio para cgadmin@microsoft.com durante este tempo e não tenham respondeu, volte a tentar.</span><span class="sxs-lookup"><span data-stu-id="9a343-143">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="9a343-144">Agradecemos-lhe por sua paciência.</span><span class="sxs-lookup"><span data-stu-id="9a343-144">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="9a343-145">13/7/2016 - transferir itens falhou</span><span class="sxs-lookup"><span data-stu-id="9a343-145">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="9a343-146">__Resumo de impacto__: entre 11/7/2016 e 13/7/2016, um subconjunto de clientes teve a problemas de transferência de itens da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a343-146">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="9a343-147">O problema provável apresentado próprio a seguinte mensagem de erro devolvido de instalação-módulo/Install-Script e guardar-módulo/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="9a343-147">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
PS C:\> Install-Module xStorage
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because:
End of Central Directory record could not be found. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ...
$null = PackageManagement\Install-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult:
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}'
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

<span data-ttu-id="9a343-148">__Causa raiz preliminar__: engenheiros identificado um problema com o Azure fornecer rede conteúdos (CDN), que foi implementada para a galeria do PowerShell em 11/7/2016.</span><span class="sxs-lookup"><span data-stu-id="9a343-148">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>
<span data-ttu-id="9a343-149">__Mitigação__: engenheiros desativada CDN do Azure na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a343-149">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="9a343-150">__Próximos passos__: investigue a causa raiz subjacente e a desenvolver uma solução para impedir futuras ocorrências.</span><span class="sxs-lookup"><span data-stu-id="9a343-150">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="9a343-151">19/5/2016 - transferir itens falhou</span><span class="sxs-lookup"><span data-stu-id="9a343-151">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="9a343-152">__Resumo de impacto__: entre 17/5/2016 e 19/5/2016, um subconjunto de clientes teve a problemas de transferência de itens da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a343-152">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="9a343-153">O problema provável apresentado próprio a seguinte mensagem de erro devolvido de instalação-módulo/Install-Script e guardar-módulo/Save-Script:</span><span class="sxs-lookup"><span data-stu-id="9a343-153">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because:
End of Central Directory record could not be found.
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install.
WARNING: Package 'AzureRM' failed to install.
VERBOSE: Module 'AzureRM.Network' was saved successfully.
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the
module 'AzureRM'.
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully.
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 +
$null = PackageManagement\Save-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ +
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage)
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage
```

<span data-ttu-id="9a343-154">__Causa raiz preliminar__: engenheiros identificada uma falha no fornecedor subjacente do Azure fornecer rede conteúdos (CDN), que foi implementada para a galeria do PowerShell em 17/5/2016.</span><span class="sxs-lookup"><span data-stu-id="9a343-154">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>
<span data-ttu-id="9a343-155">__Mitigação__: engenheiros desativada CDN do Azure na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a343-155">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>
<span data-ttu-id="9a343-156">__Próximos passos__: investigue a causa raiz subjacente e a desenvolver uma solução para impedir futuras ocorrências.</span><span class="sxs-lookup"><span data-stu-id="9a343-156">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>