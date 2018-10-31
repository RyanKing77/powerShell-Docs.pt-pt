---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galeria, powershell, psgallery, com o GDPR
title: Conformidade do GDPR de galeria do PowerShell
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002655"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="3c574-103">Conformidade do GDPR de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="3c574-104">Descrição geral</span><span class="sxs-lookup"><span data-stu-id="3c574-104">Overview</span></span>

<span data-ttu-id="3c574-105">Em Maio de 2018, uma lei de privacidade na Europa, os dados de proteção Regulamento geral (GDPR), que demorou o efeito.</span><span class="sxs-lookup"><span data-stu-id="3c574-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), took effect.</span></span>
<span data-ttu-id="3c574-106">O GDPR impõe as regras de novo em empresas, organismos públicos, sem fins lucrativos e outras organizações que oferta bens e serviços a pessoas localizadas na União Europeia (UE), ou que recolhem e analisam os dados associados a residentes da UE.</span><span class="sxs-lookup"><span data-stu-id="3c574-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="3c574-107">O GDPR aplica-se, independentemente de onde estão localizados.</span><span class="sxs-lookup"><span data-stu-id="3c574-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="3c574-108">Este artigo fornece os passos para saber como eliminar os dados pessoais da galeria do PowerShell e pode ser utilizado para suportar as suas obrigações sob o GDPR.</span><span class="sxs-lookup"><span data-stu-id="3c574-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="3c574-109">Se estiver procurando por informações gerais sobre o GDPR, consulte a [secção GDPR para o portal de confiança do serviço](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="3c574-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="3c574-110">Dados pessoalmente identificáveis</span><span class="sxs-lookup"><span data-stu-id="3c574-110">Personally identifiable data</span></span>

<span data-ttu-id="3c574-111">A galeria do PowerShell armazena as seguintes informações que possam ser fornecidas por utilizadores, que podem conter informações pessoais:</span><span class="sxs-lookup"><span data-stu-id="3c574-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

- <span data-ttu-id="3c574-112">Conta da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-112">PowerShell Gallery account</span></span>
- <span data-ttu-id="3c574-113">Pacotes publicados na galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-113">Packages published to the PowerShell Gallery</span></span>
- <span data-ttu-id="3c574-114">Correspondência de e-mail com a equipe de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="3c574-115">A maioria dos usuários não crie uma conta de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c574-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="3c574-116">Não é necessária uma conta, a menos que pretende publicar um pacote ou utilizar a funcionalidade de "Contacte o proprietário" na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c574-116">An account is not required unless you are going to publish a package or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="3c574-117">Diferente de correspondência de e-mail iniciada pelo utilizador, a galeria do PowerShell não armazena dados pessoalmente identificáveis para os utilizadores que não criou uma conta.</span><span class="sxs-lookup"><span data-stu-id="3c574-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="3c574-118">Os utilizadores que criam uma conta de galeria do PowerShell podem publicar pacotes da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c574-118">Users who create a PowerShell Gallery account can publish packages to the PowerShell Gallery.</span></span>
<span data-ttu-id="3c574-119">Esses pacotes são esperados que seja o código do PowerShell, mas poderão conter outras informações incluindo informações pessoais.</span><span class="sxs-lookup"><span data-stu-id="3c574-119">Those packages are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="3c574-120">As informações abaixo irão mostrar como pode obter todos os pacotes de ter publicado na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c574-120">The information below will show how you can get all the packages you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="3c574-121">Exportação DSR de dados da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="3c574-122">As secções seguintes descrevem como a galeria do PowerShell suporta pedidos de dados (DSR), explicando como exportar informações armazenadas na galeria do PowerShell e como solicitar a eliminação dessas informações.</span><span class="sxs-lookup"><span data-stu-id="3c574-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="3c574-123">Correio Eletrónico</span><span class="sxs-lookup"><span data-stu-id="3c574-123">Email</span></span>

<span data-ttu-id="3c574-124">Correspondência de e-mail pode incluir qualquer um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="3c574-124">Email correspondence may include any of the following:</span></span>

- <span data-ttu-id="3c574-125">E-mail enviado para os proprietários de galeria do PowerShell pacotes se a análise de código analisa detetou um problema com qualquer pacote que tiverem publicado na galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-125">Email sent to the owners of PowerShell Gallery packages if the code analysis scans detected an issue with any package they have published to the PowerShell Gallery</span></span>
- <span data-ttu-id="3c574-126">E-mail enviado por qualquer pessoa para o agrupamento de galeria do PowerShell com o endereço de e-mail na página "Fale Conosco" [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="3c574-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span></span>
- <span data-ttu-id="3c574-127">Registado utilizadores que utilizam a funcionalidade de "Contacte o proprietário" na galeria do PowerShell para enviar um e-mail para o proprietário de um pacote na galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of a package in the PowerShell Gallery</span></span>

<span data-ttu-id="3c574-128">Mensagens de e-mail enviadas por ou para a galeria do PowerShell têm uma política de retenção de 90 dias para suportar as investigações de segurança possível de código malicioso deverão ser detetado na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c574-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="3c574-129">Mensagens de correio eletrónico são eliminadas por política após 90 dias.</span><span class="sxs-lookup"><span data-stu-id="3c574-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="3c574-130">Pode solicitar cópias de todas as mensagens de e-mail enviadas ou recebidas por seu endereço de e-mail e a galeria do PowerShell dentro os últimos 90 dias.</span><span class="sxs-lookup"><span data-stu-id="3c574-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="3c574-131">Para pedir essa correspondência, envie um e-mail para [ cgadmin@microsoft.com ](mailto:cgadmin@microsoft.com), com o título: "Pedido DSR para e-mails relacionadas a esta conta".</span><span class="sxs-lookup"><span data-stu-id="3c574-131">To request this correspondence, send an email to [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="3c574-132">No corpo da mensagem, que está a solicitar de informações de estado (por exemplo: Envie todas as mensagens de correio eletrónico enviadas ou recebidas a partir deste endereço de e-mail.) Todos os e-mails que envolvem o seu endereço de e-mail no prazo de 90 dias do pedido serão enviados dentro de 7 dias de negócios.</span><span class="sxs-lookup"><span data-stu-id="3c574-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="3c574-133">Informações de conta da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="3c574-134">Se tiver criado uma conta de galeria do PowerShell, pode encontrar todas as informações pessoais que tenham sido armazenadas na galeria do PowerShell, efetuando os seguintes passos:</span><span class="sxs-lookup"><span data-stu-id="3c574-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="3c574-135">Entrar para a galeria do PowerShell, em seguida, clique em seu nome de utilizador</span><span class="sxs-lookup"><span data-stu-id="3c574-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="3c574-136">A próxima página apresentada é a página de conta, que mostra o endereço de e-mail utilizado para a conta de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="3c574-137">Se tiver criado mais de uma conta na galeria do PowerShell, terá de repetir essas etapas para cada conta.</span><span class="sxs-lookup"><span data-stu-id="3c574-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="packages-in-the-powershell-gallery"></a><span data-ttu-id="3c574-138">Pacotes na galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-138">Packages in the PowerShell Gallery</span></span>

<span data-ttu-id="3c574-139">Para facilitar a exportar pacotes publicados na galeria do PowerShell, publicamos o script "GetPSGalleryItemsForAuthor" para a galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c574-139">To facilitate exporting packages published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="3c574-140">Este script exporta uma cópia de cada versão de cada pacote inserida na galeria do PowerShell com base nas informações de autor, armazenadas no pacote.</span><span class="sxs-lookup"><span data-stu-id="3c574-140">This script exports a copy of every version of every package put into the PowerShell Gallery based on the author information stored in the package.</span></span>

> [!NOTE]
> <span data-ttu-id="3c574-141">O autor é armazenado no manifesto do pacote quando publica o seu pacote.</span><span class="sxs-lookup"><span data-stu-id="3c574-141">The Author is stored in the package manifest when you publish your package.</span></span>
> <span data-ttu-id="3c574-142">Não é garantido que o autor é a mesma identidade que a conta que utiliza na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c574-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="3c574-143">Se usar algum outro valor no campo de autor, terá de fornecer esse valor ao utilizar este script.</span><span class="sxs-lookup"><span data-stu-id="3c574-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="3c574-144">Pode transferir o script usando o seguinte comando do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3c574-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script Get-repository psgallery
```

<span data-ttu-id="3c574-145">Em seguida, pode executar o script diretamente, executando os seguintes comandos do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3c574-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="3c574-146">Será solicitado a fornecer o autor e uma pasta no seu sistema onde pretende que os pacotes a serem salvos.</span><span class="sxs-lookup"><span data-stu-id="3c574-146">You will be prompted to supply the Author and a folder on your system where you want the packages to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="3c574-147">A eliminar os dados pessoais da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="3c574-148">Para eliminar a sua conta da galeria do PowerShell ou de qualquer pacote que é proprietário na galeria do PowerShell, envie um e-mail para cgadmin@microsoft.com com o título: "Pedido de GDPR para itens relacionados a esta conta".</span><span class="sxs-lookup"><span data-stu-id="3c574-148">To delete your PowerShell Gallery account or any package you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="3c574-149">No corpo da mensagem de estado as informações que pretende que foi eliminada.</span><span class="sxs-lookup"><span data-stu-id="3c574-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="3c574-150">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3c574-150">For example:</span></span>

- <span data-ttu-id="3c574-151">Elimine x.y. z da versão de meu pacote do "nome do pacote"</span><span class="sxs-lookup"><span data-stu-id="3c574-151">Please delete version x.y.z of my package "package name"</span></span>
- <span data-ttu-id="3c574-152">Elimine todas as versões do meu pacote do "nome do pacote"</span><span class="sxs-lookup"><span data-stu-id="3c574-152">Please delete all versions of my package "package name"</span></span>
- <span data-ttu-id="3c574-153">Elimine a minha conta da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c574-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="3c574-154">Os administradores de galeria do PowerShell irão responder dentro de 7 dias de negócios.</span><span class="sxs-lookup"><span data-stu-id="3c574-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="3c574-155">Os pacotes especificados serão eliminados dentro de 30 dias após a solicitação é enviada.</span><span class="sxs-lookup"><span data-stu-id="3c574-155">The packages specified will be deleted within 30 days after the request is sent.</span></span>
