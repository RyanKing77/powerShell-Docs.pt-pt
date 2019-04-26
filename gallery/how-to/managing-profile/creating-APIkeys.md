---
ms.date: 09/10/2018
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Gerir chaves de API
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084367"
---
# <a name="managing-api-keys"></a><span data-ttu-id="a6f7b-103">Gerir chaves de API</span><span class="sxs-lookup"><span data-stu-id="a6f7b-103">Managing API keys</span></span>

<span data-ttu-id="a6f7b-104">A galeria do PowerShell suportam a criação de várias chaves de API para suportar uma gama de requisitos de publicação.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="a6f7b-105">Uma chave de API pode aplicar a um ou mais pacotes, concede privilégios específicos e tem uma data de expiração.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6f7b-106">Os utilizadores que publicado na galeria do PowerShell antes da introdução das chaves de API âmbito terão uma "chave de API de acesso total".</span><span class="sxs-lookup"><span data-stu-id="a6f7b-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="a6f7b-107">As chaves de acesso total não têm os aperfeiçoamentos de segurança incorporados no âmbito chaves de API.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="a6f7b-108">As chaves de acesso total para nunca expirar e aplicar a tudo o que propriedade do utilizador.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="a6f7b-109">Se eliminar esta chave, não pode ser recriada.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="a6f7b-110">A imagem seguinte mostra as opções disponíveis durante a criação de uma chave de API de âmbito.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-110">The following image shows the options available when creating a scoped API key.</span></span>

![Criação de chaves de API](../../Images/PSGallery_KeyScoped.png)

<span data-ttu-id="a6f7b-112">Neste exemplo, criámos uma chave de API com o nome **AzureRMDataFactory**.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="a6f7b-113">Este valor de chave pode ser utilizado para enviar pacotes com nomes que começam com "AzureRM.DataFactory" e é válido durante 365 dias.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="a6f7b-114">Este é um cenário típico quando equipas diferentes dentro da mesma organização trabalham em diferentes pacotes.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="a6f7b-115">Os membros da Equipe tem uma chave que lhe concede privilégios para o pacote específico funcionam no.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="a6f7b-116">O valor de expiração impede a utilização de chaves esquecidas ou obsoletas.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="a6f7b-117">Usando padrões de blob</span><span class="sxs-lookup"><span data-stu-id="a6f7b-117">Using glob patterns</span></span>

<span data-ttu-id="a6f7b-118">Se trabalha em vários pacotes, pode utilizar padrões de globbing para corresponder a vários pacotes como um grupo.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="a6f7b-119">Permissões da chave de API que se aplicam a todos os novos pacotes de correspondência entre o padrão de blob.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="a6f7b-120">Por exemplo, o exemplo anterior utiliza um **padrão de blob** valor de 'AzureRM.DataFactory\*'.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="a6f7b-121">Pode enviar um pacote designado "AzureRm.DataFactoryV2.Netcore' usando esta chave, uma vez que o pacote corresponde ao padrão blob.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="a6f7b-122">Criar chaves de API de forma segura</span><span class="sxs-lookup"><span data-stu-id="a6f7b-122">Create API keys securely</span></span>

<span data-ttu-id="a6f7b-123">Para segurança, um valor de chave recentemente criado nunca é mostrado no ecrã e só está disponível com o botão de copiar, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Obter novo valor de chave de API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="a6f7b-125">Só pode copiar o valor da chave de API imediatamente depois de criar ou atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="a6f7b-126">Ele não será apresentado e não estará acessível novamente depois da página é atualizada.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="a6f7b-127">Se perder o valor da chave, tem de utilizar a voltar a gerar e copie a chave depois é regenerado.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="a6f7b-128">Permissões da chave e de expiração</span><span class="sxs-lookup"><span data-stu-id="a6f7b-128">Key permissions and expiration</span></span>

<span data-ttu-id="a6f7b-129">Âmbito de chaves de API podem atribuir qualquer uma das seguintes permissões:</span><span class="sxs-lookup"><span data-stu-id="a6f7b-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="a6f7b-130">Novos pacotes de push</span><span class="sxs-lookup"><span data-stu-id="a6f7b-130">Push new packages</span></span>
- <span data-ttu-id="a6f7b-131">Push novo ou pacotes de atualização</span><span class="sxs-lookup"><span data-stu-id="a6f7b-131">Push new or update packages</span></span>
- <span data-ttu-id="a6f7b-132">Unlist pacotes</span><span class="sxs-lookup"><span data-stu-id="a6f7b-132">Unlist packages</span></span>

<span data-ttu-id="a6f7b-133">Cada nova chave tem uma expiração.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-133">Every new key has an expiration.</span></span> <span data-ttu-id="a6f7b-134">O valor de expiração é medido em dias.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-134">The expiration value is measured in days.</span></span> <span data-ttu-id="a6f7b-135">Os valores possíveis de expiração são:</span><span class="sxs-lookup"><span data-stu-id="a6f7b-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="a6f7b-136">1 dia</span><span class="sxs-lookup"><span data-stu-id="a6f7b-136">1 day</span></span>
- <span data-ttu-id="a6f7b-137">90 dias</span><span class="sxs-lookup"><span data-stu-id="a6f7b-137">90 days</span></span>
- <span data-ttu-id="a6f7b-138">180 dias</span><span class="sxs-lookup"><span data-stu-id="a6f7b-138">180 days</span></span>
- <span data-ttu-id="a6f7b-139">270 dias</span><span class="sxs-lookup"><span data-stu-id="a6f7b-139">270 days</span></span>
- <span data-ttu-id="a6f7b-140">365 dias (predefinição)</span><span class="sxs-lookup"><span data-stu-id="a6f7b-140">365 days (default)</span></span>

<span data-ttu-id="a6f7b-141">Estas definições não podem ser alteradas depois da chave é criada.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="a6f7b-142">Não é possível criar uma nova chave que nunca expira.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="a6f7b-143">Editar e excluir as chaves de API existentes</span><span class="sxs-lookup"><span data-stu-id="a6f7b-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="a6f7b-144">Pode alterar algumas definições de uma chave existente.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="a6f7b-145">Como mencionado anteriormente, não é possível modificar o âmbito de segurança para uma chave de API existente ou alterar a expiração.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="a6f7b-146">As opções alteráveis são mostradas na captura de ecrã seguinte:</span><span class="sxs-lookup"><span data-stu-id="a6f7b-146">The changeable options are shown in the following screenshot:</span></span>

![Obter novo valor de chave de API](../../Images/PSGallery_EditAPIKey.png)

<span data-ttu-id="a6f7b-148">Para alterar os pacotes controlados por uma chave, pode selecionar pacotes individuais na lista ou alterar o padrão de blob.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="a6f7b-149">Clicar **regenerar** cria um novo valor de chave.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="a6f7b-150">Tal como quando o criou inicialmente a chave, deve **cópia** o valor da chave imediatamente após a atualizá-los.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="a6f7b-151">O **cópia** opção não está disponível depois de sair desta página.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="a6f7b-152">Clicar **eliminar** exibe uma mensagem de confirmação.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="a6f7b-153">Depois de uma chave é eliminada, ficará inutilizável.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="a6f7b-154">Expiração da chave</span><span class="sxs-lookup"><span data-stu-id="a6f7b-154">Key expiration</span></span>

<span data-ttu-id="a6f7b-155">Dez dias antes da expiração, a galeria do PowerShell envia um e-mail de aviso o titular da conta da chave de API.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="a6f7b-156">Após a expiração, a chave não é utilizável.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="a6f7b-157">É apresentada uma mensagem de aviso na parte superior da página de gestão de chaves de API que mostra as chaves já não são válidas.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="a6f7b-158">Pode gerar um novo valor de chave.</span><span class="sxs-lookup"><span data-stu-id="a6f7b-158">You can generate a new key value.</span></span>
