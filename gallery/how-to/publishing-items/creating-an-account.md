---
ms.date: 06/12/2017
contributor: JKeithB
keywords: cmdlet do powershell do galeria, psgallery
title: Criar uma conta de galeria do PowerShell
ms.openlocfilehash: 4a44b51967ea8acdd331f6b3c682fc5884bd2f54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
## <a name="creating-a-powershell-gallery-account"></a>Criar uma conta de galeria do PowerShell

Tem de ser estabelecida uma conta de galeria do PowerShell antes de publicar nada para a galeria do PowerShell.
As contas de galeria do PowerShell devem ser ligadas a uma conta de e-mail do Azure Active Directory ou uma conta de e-mail do Microsoft (com um domínio do outlook.com, hotmail.com, etc.)

Para criar uma conta de galeria do PowerShell, aceda a https://PowerShellGallery.com e clique em "Registar" (ver a imagem abaixo).

![Registar a nova conta](../../Images/CreatingAccount-Register.png)

Na página seguinte, para utilizar uma conta do Azure Active Directory, selecione "Trabalho ou escola conta" e iniciar sessão com a sua conta.
Para utilizar uma conta Microsoft - por exemplo, um num domínio Hotmail.com ou Outlook.com - escolha "Conta pessoal" e iniciar sessão.

Depois de ter sessão iniciada, será solicitado para criar um nome de utilizador para a galeria do PowerShell.
Reveja os termos de utilização e a política de privacidade que estejam ligadas no, introduza um nome de utilizador e, em seguida, clique em registar.

Nota: Não é possível alterar este nome de conta quando for criado.
Consulte [Gerir proprietários do Item](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) para obter detalhes adicionais relacionados com este.

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Práticas recomendadas para contas de galeria do PowerShell

É importante que a conta de e-mail utilizada com a sua conta de galeria do PowerShell ser ativamente monitorizadas.
Todos os communiction com os proprietários de itens de galeria do PowerShell é efetuada através de e-mail utilizando o endereço associado à sua conta de galeria do PowerShell.
Se não conseguimos contactar o proprietário do item, a equipa de operações poderá ser necessário eliminar um item em algumas circunstâncias.

As organizações a publiquem para a galeria do PowerShell, muitas vezes, criar uma conta exclusiva para o efeito no Outlook.com ou outro domínio da conta Microsoft.
Em muitos casos essa conta não é regularmente monitorizada.
Nesse caso é uma melhor prática utilizar o reencaminhamento do Outlook para enviar correio eletrónico para outra conta, normalmente, um dentro da organização, que será monitorizada pela owner(s) item.

Se existirem vários proprietários associados um item, todas as comunicações que vêm da galeria do PowerShell passa a todos os proprietários.
Consulte [Gerir proprietários do Item](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) para obter detalhes adicionais sobre como adicionar os proprietários de um item.