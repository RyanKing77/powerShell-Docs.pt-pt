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
# <a name="powershell-gallery-account-settings"></a>Definições da Conta da Galeria do PowerShell

Sua conta da galeria do PowerShell é um nome visível publicamente que está ligado a uma identidade. Essa identidade é a um ID de Microsoft, como `user@hotmail.com` ou `user@outlook.com`, ou uma conta do Azure Active Directory (AAD).

A galeria do PowerShell fornece as seguintes definições de conta:

- A conta de e-mail associada à conta de galeria do PowerShell
- Opções para notificações por e-mail enviadas a partir da galeria do PowerShell
- A conta de utilizador associada à sua conta da galeria do PowerShell
- A imagem associada à sua conta de galeria do PowerShell

## <a name="email-address"></a>Endereço de correio eletrónico

O endereço de e-mail é o destino para as notificações de galeria do PowerShell. Não tem de acordo com a conta de início de sessão. Pode utilizar qualquer conta de e-mail que tem acesso. Seu endereço de e-mail diretamente nunca é fornecido da galeria do PowerShell para outros utilizadores.

![Alterar o endereço de e-mail](../../Images/PSGallery_AcccountEmailAddress.png)

Ao introduzir um novo endereço de e-mail, a galeria do PowerShell envia um e-mail de verificação para esse endereço. O e-mail de verificação contém uma ligação para a galeria do PowerShell para concluir o processo de alteração. Até concluir o processo de verificação, todas as notificações são enviadas para o endereço anterior.

## <a name="email-notifications"></a>Notificações por e-mail

Galeria do PowerShell fornece as seguintes opções de notificação:

- Os utilizadores possam contactar-me através da galeria do PowerShell
- Notificar-me quando um pacote é enviado para a galeria do PowerShell com a minha conta

![Alterar o endereço de e-mail](../../Images/PSGallery_AccountEmailOptions.png)

Conforme observado na página, não não possível desativar as notificações críticas da galeria do PowerShell.
Estes incluem:

- Notificações de segurança
- Notificações de gestão de conta de administradores da galeria do PowerShell
- Notificações sobre os testes executam da galeria do PowerShell para efetuar de envios

## <a name="change-your-login-account"></a>Alterar a sua conta de início de sessão

Para alterar a conta de início de sessão, precisa estar conectado com a conta atual. Utilize os seguintes passos para concluir a alteração.

![Definições de conta de início de sessão](../../Images/PSGallery_LoginAccountSettings.png)

1. Clique em **alterar conta**. Uma janela de pop-up explica que alterar a conta de início de sessão aplica a todos os usos dessa conta na galeria do PowerShell. Reveja as informações, em seguida, clique em **OK** para continuar.

   ![Definições de conta de início de sessão](../../Images/PSGallery_LoginAccountChange-1.png)

2. É solicitado que inicie sessão com o _nova conta_.

   ![Definições de conta de início de sessão](../../Images/PSGallery_LoginAccountChange-2.png)

3. Quando clica em **seguinte**, verá uma mensagem que tem sessão iniciada com a conta atual.
   Clique em **iniciar sessão fora e inicie sessão com uma conta diferente**.

   ![Definições de conta de início de sessão](../../Images/PSGallery_LoginAccountChange-3.png)

4. Introduza a palavra-passe da nova conta. Depois de introduzir a palavra-passe, é reencaminhado para a página de definições de conta, que mostra que a conta de início de sessão foi atualizada.


## <a name="enable-two-factor-authentication-2fa"></a>Ativar a autenticação de dois fatores (2FA)

Autenticação de dois fatores é recomendada para todos os utilizadores que publicar manualmente para a galeria do PowerShell. Para ativar a autenticação de dois fatores, a conta de início de sessão tem de ter, pelo menos, duas formas de autenticação registrado. Uma é uma palavra-passe e os outros formulários podem ser:

- Um número de telefone que pode receber mensagens de texto
- Uma aplicação de autenticador registado, como o Microsoft Authenticator para o seu telemóvel

Esses formulários de autenticação tem de ser configurados nas informações da sua conta do AAD ou nas suas definições de segurança da conta ID Microsoft.

Quando a 2FA estiver ativada, tem de autenticar com as configurado formas de autenticação, sempre que iniciar sessão na galeria do PowerShell.

> [!IMPORTANT]
> Ativar a autenticação de dois fatores para o site da galeria do PowerShell não tem de ativar a 2FA para todos os usos da sua conta de início de sessão. Para obter mais informações, consulte [sobre a verificação de dois passos](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).

## <a name="change-your-profile-picture"></a>Alterar a sua imagem do perfil

A galeria do PowerShell se baseia em Gravatar para armazenar e exibir a imagem associada com seu perfil. Para atualizar a sua imagem de perfil, visite [Gravatar.com](http://www.gravatar.com/).
