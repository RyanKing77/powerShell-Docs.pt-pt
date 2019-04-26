---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Gerir os proprietários de pacote
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084152"
---
# <a name="managing-package-owners"></a><span data-ttu-id="e075d-103">Gerir os proprietários de pacote</span><span class="sxs-lookup"><span data-stu-id="e075d-103">Managing package owners</span></span>

<span data-ttu-id="e075d-104">Propriedade de um pacote na galeria do PowerShell é definida pelo pacote que publicado na galeria.</span><span class="sxs-lookup"><span data-stu-id="e075d-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="e075d-105">Por vezes, estes metadados precisam ser gerenciada para além de publicação do pacote inicial, o que significa que os metadados de proprietário tem de ser mutáveis, enquanto o pacote propriamente dito não é.</span><span class="sxs-lookup"><span data-stu-id="e075d-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="e075d-106">Todos os proprietários de pacote são elementos.</span><span class="sxs-lookup"><span data-stu-id="e075d-106">All package owners are peers.</span></span>
<span data-ttu-id="e075d-107">Isso significa que qualquer proprietário do pacote pode publicar uma nova versão de um pacote.</span><span class="sxs-lookup"><span data-stu-id="e075d-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="e075d-108">Isso também significa que qualquer proprietário do pacote pode remover qualquer proprietário do pacote.</span><span class="sxs-lookup"><span data-stu-id="e075d-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="e075d-109">Nenhum proprietário tem autoridade mais do que outros proprietários.</span><span class="sxs-lookup"><span data-stu-id="e075d-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="e075d-110">Definir o proprietário de um pacote inicial</span><span class="sxs-lookup"><span data-stu-id="e075d-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="e075d-111">Quando um novo pacote for publicado na galeria do PowerShell, o proprietário inicial é definido pelo utilizador que publicou o pacote.</span><span class="sxs-lookup"><span data-stu-id="e075d-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="e075d-112">Tal é determinado pela cuja API chave foi utilizada no cmdlet Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="e075d-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="e075d-113">Adicionar proprietários</span><span class="sxs-lookup"><span data-stu-id="e075d-113">Adding Owners</span></span>

<span data-ttu-id="e075d-114">Quando um pacote foi publicado na galeria do PowerShell, é fácil convidar utilizadores adicionais para se tornar os proprietários de um pacote.</span><span class="sxs-lookup"><span data-stu-id="e075d-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="e075d-115">[Inicie sessão no](https://powershellgallery.com/users/account/LogOn) na galeria do PowerShell com a conta que seja o proprietário atual de um pacote.</span><span class="sxs-lookup"><span data-stu-id="e075d-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="e075d-116">Navegar para uma página de pacote usando a guia "Itens", pesquisa ou ao clicar em seu nome de utilizador e, em seguida [ **Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="e075d-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="e075d-117">Quando a sessão iniciada como proprietário de um pacote, existe uma ligação de "Gerir proprietários" no lado esquerdo, clique em.</span><span class="sxs-lookup"><span data-stu-id="e075d-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="e075d-118">Introduza o nome de utilizador da pessoa a adicionar como proprietário e clique em "Adicionar".</span><span class="sxs-lookup"><span data-stu-id="e075d-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="e075d-119">Uma mensagem de e-mail, em seguida, é enviada para o novo proprietário conjunta, como um convite para se tornar um proprietário de um pacote.</span><span class="sxs-lookup"><span data-stu-id="e075d-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="e075d-120">Uma vez que o utilizador clica na ligação, são coproprietário completo com controlo total sobre um pacote, incluindo a capacidade de remover outros utilizadores como proprietários.</span><span class="sxs-lookup"><span data-stu-id="e075d-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="e075d-121">**TENHA EM ATENÇÃO**: Até que o novo proprietário confirma a propriedade, eles *não irá* listado como proprietário de um pacote.</span><span class="sxs-lookup"><span data-stu-id="e075d-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="e075d-122">Ao visualizar o **gerir os proprietários** página, verá uma entrada pendente"aprovação" nos proprietários atuais.</span><span class="sxs-lookup"><span data-stu-id="e075d-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="e075d-123">Esse convite pode ser removida; assim como outros proprietários podem ser removidos.</span><span class="sxs-lookup"><span data-stu-id="e075d-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="e075d-124">Esse processo de convites impede os utilizadores de outros utilizadores a adicionar incorretamente como proprietários dos seus pacotes.</span><span class="sxs-lookup"><span data-stu-id="e075d-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="e075d-125">Tenha em atenção que os metadados de "Autores" são puramente de forma livre texto; apenas "proprietários" são controlados.</span><span class="sxs-lookup"><span data-stu-id="e075d-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="e075d-126">Remover proprietários</span><span class="sxs-lookup"><span data-stu-id="e075d-126">Removing Owners</span></span>

<span data-ttu-id="e075d-127">Quando um pacote tem vários proprietários e um tem de ser removido, o processo é simple:</span><span class="sxs-lookup"><span data-stu-id="e075d-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="e075d-128">[Inicie sessão no](https://powershellgallery.com/users/account/LogOn) galeria do PowerShell com a conta que seja o proprietário atual de um pacote;</span><span class="sxs-lookup"><span data-stu-id="e075d-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="e075d-129">Navegar para uma página de pacote usando a guia de pacotes, pesquisa ou ao clicar em seu nome de utilizador e, em seguida [ **Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="e075d-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="e075d-130">Quando a sessão iniciada como proprietário de um pacote, existe uma ligação de "Gerir proprietários" no lado esquerdo clique;</span><span class="sxs-lookup"><span data-stu-id="e075d-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="e075d-131">Clique na ligação "Remover" junto ao proprietário a ser removido.</span><span class="sxs-lookup"><span data-stu-id="e075d-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="e075d-132">Transferir a propriedade de pacote</span><span class="sxs-lookup"><span data-stu-id="e075d-132">Transferring Package Ownership</span></span>

<span data-ttu-id="e075d-133">Por vezes, recebemos pedidos de suporte para transferir a propriedade de pacote de um usuário para outro, mas quase sempre é possível fazê-la manualmente.</span><span class="sxs-lookup"><span data-stu-id="e075d-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="e075d-134">Transferir a propriedade de um usuário para outro é simplesmente uma combinação de dois recursos acima.</span><span class="sxs-lookup"><span data-stu-id="e075d-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="e075d-135">O proprietário atual convida o novo utilizador para se tornar um coproprietário e o novo utilizador aceita o convite;</span><span class="sxs-lookup"><span data-stu-id="e075d-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="e075d-136">O novo utilizador remove o utilizador antigo da lista de proprietários.</span><span class="sxs-lookup"><span data-stu-id="e075d-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="e075d-137">Este pedido aparecer em dois formulários, mas o processo funciona da mesma.</span><span class="sxs-lookup"><span data-stu-id="e075d-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="e075d-138">A propriedade de pacote está mudando de um desenvolvedor para outro</span><span class="sxs-lookup"><span data-stu-id="e075d-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="e075d-139">O pacote foi acidentalmente publicado a utilização da conta errada</span><span class="sxs-lookup"><span data-stu-id="e075d-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="e075d-140">Pacotes órfãos</span><span class="sxs-lookup"><span data-stu-id="e075d-140">Orphaned Packages</span></span>

<span data-ttu-id="e075d-141">Um último cenário ocorreu, mas não várias vezes.</span><span class="sxs-lookup"><span data-stu-id="e075d-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="e075d-142">Pacotes se tornaram órfãos e a única conta de proprietário do pacote não pode ser utilizada para adicionar novos proprietários.</span><span class="sxs-lookup"><span data-stu-id="e075d-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="e075d-143">Aqui estão alguns exemplos deste cenário:</span><span class="sxs-lookup"><span data-stu-id="e075d-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="e075d-144">A conta do proprietário está associada um endereço de e-mail que já não existe e o utilizador esqueceu a palavra-passe</span><span class="sxs-lookup"><span data-stu-id="e075d-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="e075d-145">O proprietário registado saiu da empresa que produz o pacote e não é possível aceder ao atualizar a propriedade de pacote</span><span class="sxs-lookup"><span data-stu-id="e075d-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="e075d-146">Devido a um erro que afetou apenas um punhado de pacotes, o pacote é de alguma maneira ownerless na Galeria</span><span class="sxs-lookup"><span data-stu-id="e075d-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="e075d-147">Os administradores de galeria do PowerShell pode acessar o link "Gerenciar proprietários" para qualquer pacote.</span><span class="sxs-lookup"><span data-stu-id="e075d-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="e075d-148">Se for o proprietário legítimo de um pacote e não é possível contactar o proprietário atual para obter permissões de propriedade, utilize a ligação de "Relatar Abuso" na Galeria para alcançar os administradores de galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e075d-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="e075d-149">Podemos, em seguida, seguirá um processo para verificar a sua propriedade do pacote.</span><span class="sxs-lookup"><span data-stu-id="e075d-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="e075d-150">Se determinarmos que deve ser um proprietário do pacote, iremos utilizar a ligação de "Gerir proprietários" para o pacote, nós mesmos e enviar-lhe o convite para se tornar um proprietário.</span><span class="sxs-lookup"><span data-stu-id="e075d-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="e075d-151">Podemos fará isso apenas depois de verificar que deve ser um proprietário e o processo varia por circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="e075d-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="e075d-152">Muitas vezes, utilizaremos o URL do projeto do pacote para encontrar uma forma de contactar o proprietário do projeto, mas podemos também utilizar, Twitter, E-Mail ou outro meio para contactar o proprietário do projeto.</span><span class="sxs-lookup"><span data-stu-id="e075d-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
