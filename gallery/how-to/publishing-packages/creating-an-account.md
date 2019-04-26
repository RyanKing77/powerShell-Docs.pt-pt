---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Criar uma conta de galeria do PowerShell
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084215"
---
# <a name="creating-a-powershell-gallery-account"></a>Criar uma conta de galeria do PowerShell

Tem de criar uma conta de galeria do PowerShell antes de publicar nada na galeria do PowerShell.
Contas de galeria do PowerShell têm de ser associadas a uma conta de início de sessão com e-mail ativado. Esta conta pode ser uma conta do Azure Active Directory ou uma ID da Microsoft, como uma conta de e-mail do outlook.com ou hotmail.com.

Para criar uma conta de galeria do PowerShell, aceda a [ https://PowerShellGallery.com ](https://PowerShellGallery.com) e clique em **entrar** conforme mostrado na imagem seguinte.

![Registre-se a nova conta](../../Images/CreateAccount-Register.png)

Para utilizar uma conta do Azure Active Directory, selecione **conta escolar ou profissional**e inicie sessão com a sua conta. Para utilizar um ID Microsoft, escolha **conta pessoal** e iniciar sessão.

Em seguida, lhe for pedido para criar um nome de utilizador para a galeria do PowerShell. Reveja os termos de utilização e a política de privacidade, introduza um nome de utilizador e, em seguida, clique em **registar**.

> [!NOTE]
> O nome da conta não pode ser alterado depois de criado. Para obter mais informações, consulte [proprietários do pacote de gestão](managing-package-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Práticas recomendadas para contas de galeria do PowerShell

É importante monitorizar ativamente a conta de e-mail utilizada com a sua conta da galeria do PowerShell. Todas as comunicações com os proprietários de pacotes de galeria do PowerShell é através deste endereço de e-mail. Se a equipe de operações de galeria do PowerShell não é possível contactar o proprietário de um pacote, podemos poderá ser necessário eliminar um pacote.

As organizações que publica na galeria do PowerShell, muitas vezes, crie uma conta de externa exclusiva para essa finalidade. Recomendamos que utilize o encaminhamento de email para encaminhar as notificações para um endereço dentro da sua organização.

Os proprietários de vários estiverem associados um pacote, todas as notificações de galeria do PowerShell são enviadas para todos os proprietários. Para obter mais informações, consulte [proprietários do pacote de gestão](managing-package-owners.md).
