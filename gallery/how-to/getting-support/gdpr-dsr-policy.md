---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galeria, powershell, psgallery, GDPR
title: Conformidade GDPR de galeria do PowerShell
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="5052a-103">Conformidade GDPR de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="5052a-104">Descrição geral</span><span class="sxs-lookup"><span data-stu-id="5052a-104">Overview</span></span>

<span data-ttu-id="5052a-105">Na Maio de 2018, uma lei da privacidade Europa, o geral dados proteção Regulamento (GDPR), entra em vigor.</span><span class="sxs-lookup"><span data-stu-id="5052a-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="5052a-106">O GDPR impõe novas regras em empresas, agências governamentais, não lucros e outras organizações que oferta bens serviços e para as pessoas da União Europeia (EU) ou que recolher e analisam dados associados ao residentes de EU.</span><span class="sxs-lookup"><span data-stu-id="5052a-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="5052a-107">O GDPR aplica-se, independentemente de onde estão localizadas.</span><span class="sxs-lookup"><span data-stu-id="5052a-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="5052a-108">Este artigo fornece os passos sobre como eliminar os dados pessoais da galeria do PowerShell e pode ser utilizado para suportar as obrigações sob o GDPR.</span><span class="sxs-lookup"><span data-stu-id="5052a-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="5052a-109">Se estiver à procura de informações gerais sobre GDPR, consulte o [secção GDPR do portal do serviço de confiança](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="5052a-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="5052a-110">Dados de identificação pessoal</span><span class="sxs-lookup"><span data-stu-id="5052a-110">Personally identifiable data</span></span>

<span data-ttu-id="5052a-111">A galeria do PowerShell armazena as seguintes informações que podem ser fornecidas por utilizadores, que podem conter informações pessoais:</span><span class="sxs-lookup"><span data-stu-id="5052a-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

* <span data-ttu-id="5052a-112">Conta de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-112">PowerShell Gallery account</span></span>
* <span data-ttu-id="5052a-113">Itens publicados para a galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-113">Items published to the PowerShell Gallery</span></span>
* <span data-ttu-id="5052a-114">Correspondência de e-mail de e-mail com a equipa de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="5052a-115">A maioria dos utilizadores não criar uma conta de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5052a-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="5052a-116">Não é necessária uma conta, exceto se publicar um item ou utilizar a funcionalidade de "Proprietário contacte" na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5052a-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="5052a-117">Além de correspondência de e-mail de correio eletrónico iniciada pelo utilizador, Galeria do PowerShell não armazena dados pessoalmente identificáveis para os utilizadores que não criou uma conta.</span><span class="sxs-lookup"><span data-stu-id="5052a-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="5052a-118">Os utilizadores que criar uma conta de galeria do PowerShell podem publicar itens de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5052a-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="5052a-119">Esses itens deverão estar código do PowerShell, mas podem conter outras informações, incluindo informações pessoais.</span><span class="sxs-lookup"><span data-stu-id="5052a-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="5052a-120">As informações abaixo mostram como obter todos os itens tiver publicado a galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5052a-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="5052a-121">Exportação DSR dos dados de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="5052a-122">As secções seguintes descrevem como galeria do PowerShell suporta pedidos de assunto de dados (DSR), por explicar como exportar informações armazenadas na galeria do PowerShell e como a eliminação destas informações do pedido.</span><span class="sxs-lookup"><span data-stu-id="5052a-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="5052a-123">Correio Eletrónico</span><span class="sxs-lookup"><span data-stu-id="5052a-123">Email</span></span>

<span data-ttu-id="5052a-124">Correspondência de e-mail de correio eletrónico pode incluir qualquer um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="5052a-124">Email correspondence may include any of the following:</span></span>

* <span data-ttu-id="5052a-125">E-mail enviado para os proprietários de galeria do PowerShell itens, se a análise de código analisa detetou um problema com qualquer item que tem publicado a galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
* <span data-ttu-id="5052a-126">E-mail enviado por qualquer pessoa para a equipa de galeria do PowerShell utilizando o endereço de e-mail na página "Contacte-na" (cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="5052a-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page (cgadmin@microsoft.com)</span></span>
* <span data-ttu-id="5052a-127">Registar utilizadores utilizam a funcionalidade de "Proprietário contacte" na galeria do PowerShell para enviar correio eletrónico para o proprietário de um item na galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="5052a-128">Mensagens de correio eletrónico enviadas pelo ou a galeria do PowerShell tem uma política de retenção de 90 dias para suportar as investigações de segurança possível deverão ser detetado código malicioso na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5052a-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="5052a-129">Os e-mails são eliminados pela política após 90 dias.</span><span class="sxs-lookup"><span data-stu-id="5052a-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="5052a-130">Pode pedir cópias de todas as mensagens de correio eletrónico enviadas para ou a partir do seu endereço de e-mail e a galeria do PowerShell nos últimos 90 dias.</span><span class="sxs-lookup"><span data-stu-id="5052a-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="5052a-131">Para pedir esta correspondência de e-mail, envie um e-mail para cgadmin@microsoft.com, com o título: "DSR pedido para e-mails relacionadas com esta conta".</span><span class="sxs-lookup"><span data-stu-id="5052a-131">To request this correspondence, send an email to cgadmin@microsoft.com, with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="5052a-132">No corpo da mensagem de estado as informações que estão a pedir (por exemplo: Envie todas as mensagens de correio eletrónico enviado para ou recebeu este endereço de e-mail.) Todos os e-mails que envolvem o seu endereço de e-mail no prazo de 90 dias do pedido serão enviadas dentro de 7 dias úteis.</span><span class="sxs-lookup"><span data-stu-id="5052a-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="5052a-133">Informações de conta de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="5052a-134">Se tiver criado uma conta de galeria do PowerShell, pode encontrar todas as informações pessoais que tenham sido armazenadas na galeria do PowerShell, efetuando os seguintes passos:</span><span class="sxs-lookup"><span data-stu-id="5052a-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="5052a-135">Inicie sessão na galeria do PowerShell, em seguida, clique no nome de utilizador</span><span class="sxs-lookup"><span data-stu-id="5052a-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="5052a-136">A seguinte página apresentada é a página de conta, que mostra o endereço de e-mail utilizado para a conta de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="5052a-137">Se tiver criado mais do que uma conta na galeria do PowerShell, terá de repetir estes passos para cada conta.</span><span class="sxs-lookup"><span data-stu-id="5052a-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="5052a-138">Itens de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="5052a-139">Para facilitar a exportar itens publicados para a galeria do PowerShell, iremos tiver publicado o script "GetPSGalleryItemsForAuthor" para a galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5052a-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="5052a-140">Este script exporta uma cópia de cada versão de todos os itens a colocar na galeria do PowerShell com base nas informações de autor armazenadas no item.</span><span class="sxs-lookup"><span data-stu-id="5052a-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="5052a-141">O autor é armazenado no manifesto item quando publicar o item.</span><span class="sxs-lookup"><span data-stu-id="5052a-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="5052a-142">Não há nenhuma garantia de que o autor é a mesma identidade que a conta que utiliza na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5052a-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="5052a-143">Se utilizar outro valor no campo autor, terá de fornecer esse valor quando utilizar este script.</span><span class="sxs-lookup"><span data-stu-id="5052a-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="5052a-144">Pode transferir o script utilizando o seguinte comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5052a-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

<span data-ttu-id="5052a-145">Em seguida, pode executar o script diretamente, executando os seguintes comandos do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5052a-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="5052a-146">Será solicitado para fornecer o autor e uma pasta no seu sistema onde pretende que os itens sejam guardados.</span><span class="sxs-lookup"><span data-stu-id="5052a-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="5052a-147">Eliminar dados pessoais da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="5052a-148">Para eliminar a conta de galeria do PowerShell ou de qualquer item proprietário na galeria do PowerShell, enviar correio eletrónico para cgadmin@microsoft.com com o título: "GDPR pedido para itens relacionados com esta conta".</span><span class="sxs-lookup"><span data-stu-id="5052a-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="5052a-149">No corpo da mensagem de estado as informações que pretende que foi eliminado.</span><span class="sxs-lookup"><span data-stu-id="5052a-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="5052a-150">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5052a-150">For example:</span></span>

* <span data-ttu-id="5052a-151">Elimine x.y.z de versão do meu item "nome do item de"</span><span class="sxs-lookup"><span data-stu-id="5052a-151">Please delete version x.y.z of my item "item name"</span></span>
* <span data-ttu-id="5052a-152">Elimine todas as versões do meu item "nome do item de"</span><span class="sxs-lookup"><span data-stu-id="5052a-152">Please delete all versions of my item "item name"</span></span>
* <span data-ttu-id="5052a-153">Elimine a minha conta de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5052a-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="5052a-154">Os administradores de galeria do PowerShell irão responder dentro de 7 dias úteis.</span><span class="sxs-lookup"><span data-stu-id="5052a-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="5052a-155">Os itens especificados serão eliminados dentro de 30 dias após o pedido é enviado.</span><span class="sxs-lookup"><span data-stu-id="5052a-155">The items specified will be deleted within 30 days after the request is sent.</span></span>
