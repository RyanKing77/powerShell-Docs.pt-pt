---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: "Gerir proprietários de Item"
ms.openlocfilehash: fcd538148f9ff1ac96324b567d54d643f1756c93
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="managing-item-owners"></a><span data-ttu-id="9e4e0-103">Gerir proprietários de Item</span><span class="sxs-lookup"><span data-stu-id="9e4e0-103">Managing Item Owners</span></span>

<span data-ttu-id="9e4e0-104">Propriedade de um item na galeria do PowerShell é definida pela que publicado o item da galeria.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-104">Ownership of an item in the PowerShell Gallery is defined by who published the item to the gallery.</span></span>
<span data-ttu-id="9e4e0-105">Por vezes, estes metadados tem de ser geridos fora a publicação de item inicial, o que significa que os metadados de proprietário tem de ser mutável enquanto o próprio item não é.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-105">Sometimes this metadata needs to be managed beyond the initial item publishing, which means the owner metadata needs to be mutable while the item itself is not.</span></span>

<span data-ttu-id="9e4e0-106">Todos os proprietários do item são elementos.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-106">All item owners are peers.</span></span> <span data-ttu-id="9e4e0-107">Isto significa que qualquer proprietário do item de pode publicar uma nova versão de um item.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-107">This means any item owner can publish a new version of an item.</span></span> <span data-ttu-id="9e4e0-108">Também significa que qualquer proprietário do item pode remover quaisquer outro proprietário do item.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-108">It also means that any item owner can remove any other item owner.</span></span> <span data-ttu-id="9e4e0-109">Não existe nenhum proprietário tem autoridade mais que outros proprietários.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-109">No owner has more authority than other owners.</span></span>  

## <a name="setting-an-items-initial-owner"></a><span data-ttu-id="9e4e0-110">Definir o proprietário inicial de um Item</span><span class="sxs-lookup"><span data-stu-id="9e4e0-110">Setting an Item's Initial Owner</span></span> 

<span data-ttu-id="9e4e0-111">Quando um novo item é publicado na galeria do PowerShell, o proprietário inicial é definido pelo utilizador que publicou o item.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-111">When a new item is published to PowerShell Gallery, the initial owner is defined by the user that published the item.</span></span> <span data-ttu-id="9e4e0-112">É determinado pela cujo API chave foi utilizada o cmdlet do módulo de publicar.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="9e4e0-113">A adição de proprietários</span><span class="sxs-lookup"><span data-stu-id="9e4e0-113">Adding Owners</span></span>

<span data-ttu-id="9e4e0-114">Depois de publicar um item a galeria do PowerShell, é fácil convidar utilizadores adicionais para se tornar os proprietários de um item.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-114">Once an item has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of an item.</span></span>

1. <span data-ttu-id="9e4e0-115">[Inicie sessão no](https://powershellgallery.com/users/account/LogOn) a galeria do PowerShell com a conta que é o proprietário atual de um item.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of an item.</span></span>
2. <span data-ttu-id="9e4e0-116">Navegue para uma página do item utilizando o separador "Itens", procure-os ou clicando em seu nome de utilizador e, em seguida, [ **gerir os meus itens**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="9e4e0-116">Navigate to an item page using the 'Items' tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="9e4e0-117">Quando tem sessão iniciada como proprietário de um item, há uma ligação 'Gerir proprietários' no lado esquerdo, clique em.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-117">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="9e4e0-118">Introduza o nome de utilizador da pessoa a adicionar como um proprietário e clique em 'Add'.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="9e4e0-119">Mensagens de correio eletrónico é enviada para o novo proprietário conjunta, como um convite para se tornar um proprietário de um item.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-119">An email is then sent to the new co-owner, as an invitation to become an owner of an item.</span></span>
6. <span data-ttu-id="9e4e0-120">Uma vez que o utilizador clica na ligação, são um coproprietário completo, com controlo total sobre um item, incluindo a capacidade de remover a outros utilizadores como proprietários.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-120">Once that user clicks the link, they are a full co-owner with full control over an item, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="9e4e0-121">**Tenha em atenção**: até que o novo proprietário confirma a propriedade, estes *não* estar listado como um proprietário de um item.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of an item.</span></span>
<span data-ttu-id="9e4e0-122">Ao visualizar o **Gerir proprietários** página, verá uma entrada para "pendente aprovação" os proprietários atuais.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="9e4e0-123">Que pode ser removido convite; tal como outros proprietários podem ser removidos.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="9e4e0-124">Este processo de convites para impede que os utilizadores falsely adicionar outros utilizadores como proprietários dos respetivos itens.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-124">This process of invitations prevents users from falsely adding other users as owners of their items.</span></span>

<span data-ttu-id="9e4e0-125">Tenha em atenção que os metadados de "Autores" são o texto puramente livres superior; apenas os proprietários"" são controlados.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="9e4e0-126">Remover os proprietários</span><span class="sxs-lookup"><span data-stu-id="9e4e0-126">Removing Owners</span></span>
<span data-ttu-id="9e4e0-127">Quando um item tem vários proprietários e um tem de ser removido, o processo é simple:</span><span class="sxs-lookup"><span data-stu-id="9e4e0-127">When an item has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="9e4e0-128">[Inicie sessão no](https://powershellgallery.com/users/account/LogOn) a galeria do PowerShell com a conta que é o proprietário atual de um item;</span><span class="sxs-lookup"><span data-stu-id="9e4e0-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of an item;</span></span>
2. <span data-ttu-id="9e4e0-129">Navegue para uma página do item utilizando o separador de itens, procurar ou clicar em seu nome de utilizador e, em seguida, [ **gerir os meus itens**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="9e4e0-129">Navigate to an item page using the Items tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="9e4e0-130">Quando a sessão iniciada como proprietário de um item, há uma ligação 'Gerir proprietários' no lado esquerdo de clicar em;</span><span class="sxs-lookup"><span data-stu-id="9e4e0-130">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="9e4e0-131">Clique na ligação "Remover" junto ao proprietário a serem removidos.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-item-ownership"></a><span data-ttu-id="9e4e0-132">Transferir a propriedade do Item</span><span class="sxs-lookup"><span data-stu-id="9e4e0-132">Transferring Item Ownership</span></span>
<span data-ttu-id="9e4e0-133">Por vezes, obtemos os pedidos de suporte para a transferência de item propriedade de um utilizador para outro, mas pode realizar quase sempre-la manualmente.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-133">We sometimes get support requests to transfer item ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="9e4e0-134">Transferir a propriedade de um utilizador para outra é simplesmente uma combinação de duas funcionalidades acima.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="9e4e0-135">O proprietário atual invites o novo utilizador para se tornar um coproprietário e o utilizador novo aceitar o convite a;</span><span class="sxs-lookup"><span data-stu-id="9e4e0-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="9e4e0-136">O utilizador novo remove o utilizador antigo da lista de proprietários.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="9e4e0-137">Este pedido ficar em alguns formulários, mas o processo funciona da mesma.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-137">This request has come in under a couple forms but the process works the same.</span></span>

* <span data-ttu-id="9e4e0-138">A propriedade do item está a mudar de um programador para outro</span><span class="sxs-lookup"><span data-stu-id="9e4e0-138">The item ownership is changing from one developer to another</span></span>
* <span data-ttu-id="9e4e0-139">Publicar o item foi acidentalmente utilizando a conta de errado</span><span class="sxs-lookup"><span data-stu-id="9e4e0-139">The item was accidentally published using the wrong account</span></span>


## <a name="orphaned-items"></a><span data-ttu-id="9e4e0-140">Itens órfãos</span><span class="sxs-lookup"><span data-stu-id="9e4e0-140">Orphaned Items</span></span>
<span data-ttu-id="9e4e0-141">Ocorreu um último cenário, mas não demasiadas vezes.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="9e4e0-142">Itens ficou órfãos e a única conta de proprietário do item não pode ser utilizada para adicionar os proprietários de novo.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-142">Items have become orphans and the only item owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="9e4e0-143">Seguem-se alguns exemplos deste cenário:</span><span class="sxs-lookup"><span data-stu-id="9e4e0-143">Here are some examples of this scenario:</span></span>

* <span data-ttu-id="9e4e0-144">A conta do proprietário está associada um endereço de correio eletrónico que já não existe e o utilizador tenha esquecido a palavra-passe</span><span class="sxs-lookup"><span data-stu-id="9e4e0-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
* <span data-ttu-id="9e4e0-145">O proprietário registado tiver saído da empresa que produz o item e não é possível aceder ao atualizar a propriedade do item</span><span class="sxs-lookup"><span data-stu-id="9e4e0-145">The registered owner has left the company that produces the item and cannot be reached to update the item ownership</span></span>
* <span data-ttu-id="9e4e0-146">Resultam de erros que afetou apenas alguns dos itens, o item é examinar ownerless na Galeria</span><span class="sxs-lookup"><span data-stu-id="9e4e0-146">Due to a bug that has only affected a handful of items, the item is somehow ownerless on the gallery</span></span>

<span data-ttu-id="9e4e0-147">Os administradores de galeria do PowerShell podem aceder a ligação 'Gerir proprietários' para qualquer item.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any item.</span></span>
<span data-ttu-id="9e4e0-148">Se for o proprietário de um item rightful e não é possível contactar o proprietário atual para obter permissões de propriedade, utilize a ligação 'Relatório abuso' na Galeria para contactar os administradores de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-148">If you are the rightful owner of a item and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="9e4e0-149">Em seguida, iremos segui um processo para verificar a sua propriedade do item.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-149">We will then follow a process to verify your ownership of the item.</span></span>
<span data-ttu-id="9e4e0-150">Se determinar que deve ser um proprietário do item, iremos utilizar na ligação 'Gerir proprietários' para o item ourselves e enviar-lhe o convite para se tornar um proprietário.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-150">If we determine you should be an owner of the item, we will use the 'Manage Owners' link for the item ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="9e4e0-151">Só será efetuado esta depois de verificar que deve ser um proprietário e o processo para este varia consoante o circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="9e4e0-152">Muitas vezes, iremos utilizar o URL de projeto do item para encontrar uma forma de contactar o proprietário do projeto, mas podem também utilizamos Twitter, o E-Mail ou outros meios para contactar o proprietário do projeto.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-152">Often times, we will use the item's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>

