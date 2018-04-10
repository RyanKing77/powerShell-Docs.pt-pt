---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgalleryint_status
ms.openlocfilehash: 4f7d300bb07fcbdb100c2fb029f8f66ab260fe7a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a><span data-ttu-id="91608-103">Estado de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="91608-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="91608-104">27/03/2017 - RESOLVIDO: não é possível ver páginas individuais, módulo e scripts</span><span class="sxs-lookup"><span data-stu-id="91608-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="91608-105">__Resumo de impacto__: direcionar ligações para páginas individuais, módulo e script no https://www.powershellgallery.com foram interrompidas.</span><span class="sxs-lookup"><span data-stu-id="91608-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="91608-106">Isto foi reportado em todas as regiões.</span><span class="sxs-lookup"><span data-stu-id="91608-106">This was being reported across all the regions.</span></span> <span data-ttu-id="91608-107">Isto não afetar qualquer um dos PowerShellGet cmdlets ie., instale-Module, Script de atualização, publicar-Module, de Script de instalação, atualização-Module, publicar-Script continuou a trabalhar.</span><span class="sxs-lookup"><span data-stu-id="91608-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="91608-108">__Causa raiz__: engenheiros de identificar a causa como um problema ao chamar botões como o Facebook para a página de redes sociais.</span><span class="sxs-lookup"><span data-stu-id="91608-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>

<span data-ttu-id="91608-109">__Resolução__: engenheiros de corrigido o problema, desativando as informações de contagem do Facebook.</span><span class="sxs-lookup"><span data-stu-id="91608-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="91608-110">__Próximos passos__: foi aberto um problema de controlo interno para corrigir o nosso utilização da API do Facebook.</span><span class="sxs-lookup"><span data-stu-id="91608-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="91608-111">15/12/2016 - não é possível enviar mensagens de correio eletrónico através do Web site de PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="91608-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="91608-112">__Resumo de impacto__: entre 13/12/2016 e 15/12/2016, as mensagens enviadas por proprietários de contacto, Gerir proprietários, contacte o suporte ou abuso do relatório não foram recebidas por administradores de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91608-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="91608-113">__Causa raiz__: engenheiros de identificar a causa como um problema de autenticação com o servidor de SMTP.</span><span class="sxs-lookup"><span data-stu-id="91608-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>
<span data-ttu-id="91608-114">__Resolução__: engenheiros foram capazes de resolver o problema de autenticação e restaurar a ligação ao servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="91608-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>
<span data-ttu-id="91608-115">__Próximos passos__: Se utilizou as ligações de proprietários de contacto, Gerir proprietários, contacte o suporte ou relatório abuso para enviar correio para cgadmin@microsoft.com durante este tempo e não tenham respondeu, volte a tentar.</span><span class="sxs-lookup"><span data-stu-id="91608-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="91608-116">Pedimos desculpa pelo incómodo.</span><span class="sxs-lookup"><span data-stu-id="91608-116">We apologize for the inconvenience.</span></span>


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="91608-117">8/10/2016 - resolvido: não é possível enviar e-mails para cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="91608-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="91608-118">__Resumo de impacto__: entre 8/5/2016 e 8/10/2016, os clientes não conseguiram enviar e-mails para cgadmin@microsoft.com, ou utilizar a funcionalidade contacte-nos.</span><span class="sxs-lookup"><span data-stu-id="91608-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>
<span data-ttu-id="91608-119">__Causa raiz__: engenheiros de identificar a causa como uma alteração da configuração da conta de e-mail.</span><span class="sxs-lookup"><span data-stu-id="91608-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>
<span data-ttu-id="91608-120">__Resolução__: engenheiros trabalhado para resolver o problema de configuração.</span><span class="sxs-lookup"><span data-stu-id="91608-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>
<span data-ttu-id="91608-121">__Próximos passos__: se utilizado na ligação contacte-nos ou enviar correio para cgadmin@microsoft.com durante este tempo e não tenham respondeu, volte a tentar.</span><span class="sxs-lookup"><span data-stu-id="91608-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="91608-122">Agradecemos-lhe por sua paciência.</span><span class="sxs-lookup"><span data-stu-id="91608-122">Thank you for your patience.</span></span>