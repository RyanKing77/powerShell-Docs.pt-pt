---
ms.date: 09/05/2018
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Definições da Conta da Galeria do PowerShell
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002791"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="7c05d-103">Definições da Conta da Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c05d-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="7c05d-104">Sua conta da galeria do PowerShell é um nome visível publicamente que está ligado a uma identidade.</span><span class="sxs-lookup"><span data-stu-id="7c05d-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="7c05d-105">Essa identidade é a um ID de Microsoft, como `user@hotmail.com` ou `user@outlook.com`, ou uma conta do Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="7c05d-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="7c05d-106">A galeria do PowerShell fornece as seguintes definições de conta:</span><span class="sxs-lookup"><span data-stu-id="7c05d-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="7c05d-107">A conta de e-mail associada à conta de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c05d-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="7c05d-108">Opções para notificações por e-mail enviadas a partir da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c05d-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="7c05d-109">A conta de utilizador associada à sua conta da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c05d-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="7c05d-110">A imagem associada à sua conta de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c05d-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="7c05d-111">Endereço de correio eletrónico</span><span class="sxs-lookup"><span data-stu-id="7c05d-111">Email address</span></span>

<span data-ttu-id="7c05d-112">O endereço de e-mail é o destino para as notificações de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c05d-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="7c05d-113">Não tem de acordo com a conta de início de sessão.</span><span class="sxs-lookup"><span data-stu-id="7c05d-113">It does not have to match the login account.</span></span> <span data-ttu-id="7c05d-114">Pode utilizar qualquer conta de e-mail que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="7c05d-114">You may use any email account you have access to.</span></span> <span data-ttu-id="7c05d-115">Seu endereço de e-mail diretamente nunca é fornecido da galeria do PowerShell para outros utilizadores.</span><span class="sxs-lookup"><span data-stu-id="7c05d-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![Alterar o endereço de e-mail](../../Images/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="7c05d-117">Ao introduzir um novo endereço de e-mail, a galeria do PowerShell envia um e-mail de verificação para esse endereço.</span><span class="sxs-lookup"><span data-stu-id="7c05d-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="7c05d-118">O e-mail de verificação contém uma ligação para a galeria do PowerShell para concluir o processo de alteração.</span><span class="sxs-lookup"><span data-stu-id="7c05d-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="7c05d-119">Até concluir o processo de verificação, todas as notificações são enviadas para o endereço anterior.</span><span class="sxs-lookup"><span data-stu-id="7c05d-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="7c05d-120">Notificações por e-mail</span><span class="sxs-lookup"><span data-stu-id="7c05d-120">Email notifications</span></span>

<span data-ttu-id="7c05d-121">Galeria do PowerShell fornece as seguintes opções de notificação:</span><span class="sxs-lookup"><span data-stu-id="7c05d-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="7c05d-122">Os utilizadores possam contactar-me através da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c05d-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="7c05d-123">Notificar-me quando um pacote é enviado para a galeria do PowerShell com a minha conta</span><span class="sxs-lookup"><span data-stu-id="7c05d-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![Alterar o endereço de e-mail](../../Images/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="7c05d-125">Conforme observado na página, não não possível desativar as notificações críticas da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c05d-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="7c05d-126">Estes incluem:</span><span class="sxs-lookup"><span data-stu-id="7c05d-126">These include:</span></span>

- <span data-ttu-id="7c05d-127">Notificações de segurança</span><span class="sxs-lookup"><span data-stu-id="7c05d-127">Security notifications</span></span>
- <span data-ttu-id="7c05d-128">Notificações de gestão de conta de administradores da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c05d-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="7c05d-129">Notificações sobre os testes executam da galeria do PowerShell para efetuar de envios</span><span class="sxs-lookup"><span data-stu-id="7c05d-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="7c05d-130">Alterar a sua conta de início de sessão</span><span class="sxs-lookup"><span data-stu-id="7c05d-130">Change your login account</span></span>

<span data-ttu-id="7c05d-131">Para alterar a conta de início de sessão, precisa estar conectado com a conta atual.</span><span class="sxs-lookup"><span data-stu-id="7c05d-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="7c05d-132">Utilize os seguintes passos para concluir a alteração.</span><span class="sxs-lookup"><span data-stu-id="7c05d-132">Use the following steps to complete the change.</span></span>

![Definições de conta de início de sessão](../../Images/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="7c05d-134">Clique em **alterar conta**.</span><span class="sxs-lookup"><span data-stu-id="7c05d-134">Click on **Change Account**.</span></span> <span data-ttu-id="7c05d-135">Uma janela de pop-up explica que alterar a conta de início de sessão aplica a todos os usos dessa conta na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c05d-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="7c05d-136">Reveja as informações, em seguida, clique em **OK** para continuar.</span><span class="sxs-lookup"><span data-stu-id="7c05d-136">Review the information, then click **OK** to continue.</span></span>

   ![Definições de conta de início de sessão](../../Images/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="7c05d-138">É solicitado que inicie sessão com o _nova conta_.</span><span class="sxs-lookup"><span data-stu-id="7c05d-138">You are then prompted to sign in using the _new account_.</span></span>

   ![Definições de conta de início de sessão](../../Images/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="7c05d-140">Quando clica em **seguinte**, verá uma mensagem que tem sessão iniciada com a conta atual.</span><span class="sxs-lookup"><span data-stu-id="7c05d-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="7c05d-141">Clique em **iniciar sessão fora e inicie sessão com uma conta diferente**.</span><span class="sxs-lookup"><span data-stu-id="7c05d-141">Click **Sign out and sign in with a different account**.</span></span>

   ![Definições de conta de início de sessão](../../Images/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="7c05d-143">Introduza a palavra-passe da nova conta.</span><span class="sxs-lookup"><span data-stu-id="7c05d-143">Enter the password of the new account.</span></span> <span data-ttu-id="7c05d-144">Depois de introduzir a palavra-passe, é reencaminhado para a página de definições de conta, que mostra que a conta de início de sessão foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="7c05d-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>


## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="7c05d-145">Ativar a autenticação de dois fatores (2FA)</span><span class="sxs-lookup"><span data-stu-id="7c05d-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="7c05d-146">Autenticação de dois fatores é recomendada para todos os utilizadores que publicar manualmente para a galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c05d-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="7c05d-147">Para ativar a autenticação de dois fatores, a conta de início de sessão tem de ter, pelo menos, duas formas de autenticação registrado.</span><span class="sxs-lookup"><span data-stu-id="7c05d-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="7c05d-148">Uma é uma palavra-passe e os outros formulários podem ser:</span><span class="sxs-lookup"><span data-stu-id="7c05d-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="7c05d-149">Um número de telefone que pode receber mensagens de texto</span><span class="sxs-lookup"><span data-stu-id="7c05d-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="7c05d-150">Uma aplicação de autenticador registado, como o Microsoft Authenticator para o seu telemóvel</span><span class="sxs-lookup"><span data-stu-id="7c05d-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="7c05d-151">Esses formulários de autenticação tem de ser configurados nas informações da sua conta do AAD ou nas suas definições de segurança da conta ID Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7c05d-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="7c05d-152">Quando a 2FA estiver ativada, tem de autenticar com as configurado formas de autenticação, sempre que iniciar sessão na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c05d-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c05d-153">Ativar a autenticação de dois fatores para o site da galeria do PowerShell não tem de ativar a 2FA para todos os usos da sua conta de início de sessão.</span><span class="sxs-lookup"><span data-stu-id="7c05d-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="7c05d-154">Para obter mais informações, consulte [sobre a verificação de dois passos](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span><span class="sxs-lookup"><span data-stu-id="7c05d-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="7c05d-155">Alterar a sua imagem do perfil</span><span class="sxs-lookup"><span data-stu-id="7c05d-155">Change your profile picture</span></span>

<span data-ttu-id="7c05d-156">A galeria do PowerShell se baseia em Gravatar para armazenar e exibir a imagem associada com seu perfil.</span><span class="sxs-lookup"><span data-stu-id="7c05d-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="7c05d-157">Para atualizar a sua imagem de perfil, visite [Gravatar.com](http://www.gravatar.com/).</span><span class="sxs-lookup"><span data-stu-id="7c05d-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
