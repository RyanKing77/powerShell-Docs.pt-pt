---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: Criar uma conta de galeria do PowerShell
ms.openlocfilehash: 3ec9ad8f979fc0b88fbee72fc28ad1e3394eb01d
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
---
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="45fe3-103">Criar uma conta de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="45fe3-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="45fe3-104">Tem de ser estabelecida uma conta de galeria do PowerShell antes de publicar nada para a galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45fe3-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="45fe3-105">As contas de galeria do PowerShell devem ser ligadas a uma conta de e-mail do Azure Active Directory ou uma conta de e-mail do Microsoft (com um domínio do outlook.com, hotmail.com, etc.)</span><span class="sxs-lookup"><span data-stu-id="45fe3-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="45fe3-106">Para criar uma conta de galeria do PowerShell, aceda a https://PowerShellGallery.com e clique em "Registar" (ver a imagem abaixo).</span><span class="sxs-lookup"><span data-stu-id="45fe3-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span>

![Registar a nova conta](../../Images/CreatingAccount-Register.png)

<span data-ttu-id="45fe3-108">Na página seguinte, para utilizar uma conta do Azure Active Directory, selecione "Trabalho ou escola conta" e iniciar sessão com a sua conta.</span><span class="sxs-lookup"><span data-stu-id="45fe3-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span>
<span data-ttu-id="45fe3-109">Para utilizar uma conta Microsoft - por exemplo, um num domínio Hotmail.com ou Outlook.com - escolha "Conta pessoal" e iniciar sessão.</span><span class="sxs-lookup"><span data-stu-id="45fe3-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span>

<span data-ttu-id="45fe3-110">Depois de ter sessão iniciada, será solicitado para criar um nome de utilizador para a galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45fe3-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span>
<span data-ttu-id="45fe3-111">Reveja os termos de utilização e a política de privacidade que estejam ligadas no, introduza um nome de utilizador e, em seguida, clique em registar.</span><span class="sxs-lookup"><span data-stu-id="45fe3-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="45fe3-112">Nota: Não é possível alterar este nome de conta quando for criado.</span><span class="sxs-lookup"><span data-stu-id="45fe3-112">Note: This account name cannot be changed once it is created.</span></span>
<span data-ttu-id="45fe3-113">Consulte [Gerir proprietários do Item](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) para obter detalhes adicionais relacionados com este.</span><span class="sxs-lookup"><span data-stu-id="45fe3-113">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="45fe3-114">Práticas recomendadas para contas de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="45fe3-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="45fe3-115">É importante que a conta de e-mail utilizada com a sua conta de galeria do PowerShell ser ativamente monitorizadas.</span><span class="sxs-lookup"><span data-stu-id="45fe3-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="45fe3-116">Todos os communiction com os proprietários de itens de galeria do PowerShell é efetuada através de e-mail utilizando o endereço associado à sua conta de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45fe3-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="45fe3-117">Se não conseguimos contactar o proprietário do item, a equipa de operações poderá ser necessário eliminar um item em algumas circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="45fe3-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="45fe3-118">As organizações a publiquem para a galeria do PowerShell, muitas vezes, criar uma conta exclusiva para o efeito no Outlook.com ou outro domínio da conta Microsoft.</span><span class="sxs-lookup"><span data-stu-id="45fe3-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="45fe3-119">Em muitos casos essa conta não é regularmente monitorizada.</span><span class="sxs-lookup"><span data-stu-id="45fe3-119">In many cases that account is not regularly monitored.</span></span>
<span data-ttu-id="45fe3-120">Nesse caso é uma melhor prática utilizar o reencaminhamento do Outlook para enviar correio eletrónico para outra conta, normalmente, um dentro da organização, que será monitorizada pela owner(s) item.</span><span class="sxs-lookup"><span data-stu-id="45fe3-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="45fe3-121">Se existirem vários proprietários associados um item, todas as comunicações que vêm da galeria do PowerShell passa a todos os proprietários.</span><span class="sxs-lookup"><span data-stu-id="45fe3-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="45fe3-122">Consulte [Gerir proprietários do Item](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) para obter detalhes adicionais sobre como adicionar os proprietários de um item.</span><span class="sxs-lookup"><span data-stu-id="45fe3-122">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span>