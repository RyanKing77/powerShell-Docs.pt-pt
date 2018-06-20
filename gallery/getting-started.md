---
ms.date: 06/12/2017
contributor: JKeithB
keywords: cmdlet do powershell do galeria, psgallery
title: Introdução à galeria do PowerShell
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190167"
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="f6c92-103">Introdução à galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6c92-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="f6c92-104">Transferência de itens da galeria do PowerShell para o sistema necessita de [PowerShellGet](/powershell/module/powershellget) módulo.</span><span class="sxs-lookup"><span data-stu-id="f6c92-104">Downloading items from the PowerShell Gallery to your system requires the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="f6c92-105">Pode encontrar o módulo de PowerShellGet em qualquer um dos seguintes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="f6c92-105">You can find the PowerShellGet module in any of the following.</span></span> <span data-ttu-id="f6c92-106">Não é necessário iniciar sessão transferir os itens da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6c92-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="f6c92-107">Deteção de itens da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6c92-107">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="f6c92-108">Pode encontrar itens na galeria do PowerShell, utilizando o **pesquisa** controlo neste Web site ou pela navegação nas páginas de módulos e Scripts.</span><span class="sxs-lookup"><span data-stu-id="f6c92-108">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="f6c92-109">Também pode encontrar itens da galeria do PowerShell, executando o [encontrar o módulo][] e [localizar Script][] cmdlets, consoante o tipo de item com `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="f6c92-109">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="f6c92-110">Filtrar os resultados da galeria do pode ser feito utilizando os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="f6c92-110">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="f6c92-111">Nome</span><span class="sxs-lookup"><span data-stu-id="f6c92-111">Name</span></span>
- <span data-ttu-id="f6c92-112">AllVersions</span><span class="sxs-lookup"><span data-stu-id="f6c92-112">AllVersions</span></span>
- <span data-ttu-id="f6c92-113">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f6c92-113">MinimumVersion</span></span>
- <span data-ttu-id="f6c92-114">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f6c92-114">RequiredVersion</span></span>
- <span data-ttu-id="f6c92-115">Sinalizador</span><span class="sxs-lookup"><span data-stu-id="f6c92-115">Tag</span></span>
- <span data-ttu-id="f6c92-116">Inclui</span><span class="sxs-lookup"><span data-stu-id="f6c92-116">Includes</span></span>
- <span data-ttu-id="f6c92-117">DscResource</span><span class="sxs-lookup"><span data-stu-id="f6c92-117">DscResource</span></span>
- <span data-ttu-id="f6c92-118">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="f6c92-118">RoleCapability</span></span>
- <span data-ttu-id="f6c92-119">Comando</span><span class="sxs-lookup"><span data-stu-id="f6c92-119">Command</span></span>
- <span data-ttu-id="f6c92-120">filtro</span><span class="sxs-lookup"><span data-stu-id="f6c92-120">Filter</span></span>

<span data-ttu-id="f6c92-121">Se apenas estiver interessado em detetar recursos de DSC específicos na galeria, pode executar o [localizar DscResource] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6c92-121">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="f6c92-122">Localizar DscResource devolve dados contidos na Galeria de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="f6c92-122">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="f6c92-123">Porque os recursos de DSC são sempre fornecidos como parte de um módulo, é preciso executar [Instalar módulo][] para instalar esses recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="f6c92-123">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="f6c92-124">Saber mais sobre itens de galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6c92-124">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="f6c92-125">Depois de ter identificado um item que está interessado em, poderá querer saber mais acerca do mesmo.</span><span class="sxs-lookup"><span data-stu-id="f6c92-125">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="f6c92-126">Pode fazê-lo, examinando página específica desse item na galeria.</span><span class="sxs-lookup"><span data-stu-id="f6c92-126">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="f6c92-127">Nessa página, poderá ver todos os metadados carregados com do item.</span><span class="sxs-lookup"><span data-stu-id="f6c92-127">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="f6c92-128">Estes metadados de um item é fornecido pelo autor do item e não é verificado pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f6c92-128">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="f6c92-129">O proprietário do item vivamente está associado à conta de galeria utilizada para publicar o item e é mais fidedigno que o campo autor.</span><span class="sxs-lookup"><span data-stu-id="f6c92-129">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="f6c92-130">Se detetar um item que sentir não está publicado em boa fé, clique em **relatório abuso** na página esse item.</span><span class="sxs-lookup"><span data-stu-id="f6c92-130">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="f6c92-131">Se estiver a executar [encontrar o módulo][] ou [localizar Script][], pode ver estes dados no objeto PSGetModuleInfo devolvido.</span><span class="sxs-lookup"><span data-stu-id="f6c92-131">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="f6c92-132">Por exemplo, executar `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` devolve dados no módulo PSReadLine na galeria.</span><span class="sxs-lookup"><span data-stu-id="f6c92-132">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="f6c92-133">Transferência de itens da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6c92-133">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="f6c92-134">Aconselhamo-o seguinte processo quando a transferência de itens da galeria do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f6c92-134">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="f6c92-135">Inspecione</span><span class="sxs-lookup"><span data-stu-id="f6c92-135">Inspect</span></span>

<span data-ttu-id="f6c92-136">Para transferir um item da Galeria para inspecção, execute o [guardar-Module][] ou [Guardar Script][] cmdlet, consoante o tipo de item.</span><span class="sxs-lookup"><span data-stu-id="f6c92-136">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="f6c92-137">Isto permite-lhe guardar o item localmente sem instalá-lo e inspecionar os conteúdos do item.</span><span class="sxs-lookup"><span data-stu-id="f6c92-137">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="f6c92-138">Lembre-se ao eliminar o item guardado manualmente.</span><span class="sxs-lookup"><span data-stu-id="f6c92-138">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="f6c92-139">Alguns destes itens são criados pela Microsoft e outros são criados pela Comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6c92-139">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="f6c92-140">A Microsoft recomenda que reveja o conteúdo e o código de itens nesta galeria antes da instalação.</span><span class="sxs-lookup"><span data-stu-id="f6c92-140">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="f6c92-141">Se detetar um item que sentir não está publicado em boa fé, clique em **relatório abuso** na página esse item.</span><span class="sxs-lookup"><span data-stu-id="f6c92-141">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="f6c92-142">Instalar</span><span class="sxs-lookup"><span data-stu-id="f6c92-142">Install</span></span>

<span data-ttu-id="f6c92-143">Para instalar um item da Galeria para utilização, execute o [Instalar módulo][] ou [Script de instalação][] cmdlet, consoante o tipo de item.</span><span class="sxs-lookup"><span data-stu-id="f6c92-143">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="f6c92-144">[Instalar módulo][] instala o módulo para `$env:ProgramFiles\WindowsPowerShell\Modules` por predefinição.</span><span class="sxs-lookup"><span data-stu-id="f6c92-144">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="f6c92-145">Isto requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="f6c92-145">This requires an administrator account.</span></span> <span data-ttu-id="f6c92-146">Se adicionar o `-Scope CurrentUser` parâmetro, o módulo está instalado para `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="f6c92-146">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="f6c92-147">[Script de instalação][] instala o script para `$env:ProgramFiles\WindowsPowerShell\Scripts` por predefinição.</span><span class="sxs-lookup"><span data-stu-id="f6c92-147">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="f6c92-148">Isto requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="f6c92-148">This requires an administrator account.</span></span> <span data-ttu-id="f6c92-149">Se adicionar o `-Scope CurrentUser` parâmetro, o script está instalado o `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="f6c92-149">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="f6c92-150">Por predefinição, [Instalar módulo][] e [Script de instalação][] instala a versão mais recente de um item.</span><span class="sxs-lookup"><span data-stu-id="f6c92-150">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="f6c92-151">Para instalar uma versão mais antiga do item, adicione o `-RequiredVersion` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6c92-151">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="f6c92-152">Implementar</span><span class="sxs-lookup"><span data-stu-id="f6c92-152">Deploy</span></span>

<span data-ttu-id="f6c92-153">Para implementar um item da galeria do PowerShell a automatização do Azure, clique em **implementar a automatização do Azure** na página de detalhes do item.</span><span class="sxs-lookup"><span data-stu-id="f6c92-153">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="f6c92-154">Será redirecionado para o Portal de gestão do Azure, onde poderá iniciar sessão com as suas credenciais de conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="f6c92-154">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="f6c92-155">Tenha em atenção que implementar itens com dependências irá implementar todas as dependências da automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="f6c92-155">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="f6c92-156">O botão 'Implementar a automatização do Azure' pode ser desativado através da adição de **AzureAutomationNotSupported** etiquetas para os seus metadados do item.</span><span class="sxs-lookup"><span data-stu-id="f6c92-156">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="f6c92-157">Para saber mais sobre a automatização do Azure, consulte o [da automatização do Azure](/azure/automation) documentação.</span><span class="sxs-lookup"><span data-stu-id="f6c92-157">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="f6c92-158">Atualizar itens da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6c92-158">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="f6c92-159">Para atualizar itens instalados a partir da galeria do PowerShell, execute [atualização-Module] [-] ou [Script de atualização] [] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6c92-159">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="f6c92-160">Quando executar sem quaisquer parâmetros adicionais, [atualização-Module] [-] tenta atualizar cada módulo instalado, executando [Instalar módulo][].</span><span class="sxs-lookup"><span data-stu-id="f6c92-160">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="f6c92-161">Para atualizar seletivamente módulos, adicione o `-Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6c92-161">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="f6c92-162">Da mesma forma, quando executada sem quaisquer parâmetros adicionais, [Script de atualização] [-] também tentar atualizar cada script instalada através da execução [Script de instalação][].</span><span class="sxs-lookup"><span data-stu-id="f6c92-162">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="f6c92-163">Para atualizar seletivamente scripts, adicione o `-Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f6c92-163">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="f6c92-164">Itens de lista que tenha instalado da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6c92-164">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="f6c92-165">Para saber quais os módulos que instalou da galeria do PowerShell, execute o [Get-InstalledModule][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6c92-165">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="f6c92-166">Este comando lista todos os módulos tem no seu sistema, que foram instalados diretamente a partir da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6c92-166">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="f6c92-167">Da mesma forma, para saber quais os scripts que instalou da galeria do PowerShell, execute o [Get-InstalledScript][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6c92-167">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="f6c92-168">Este comando lista todos os scripts que tem no seu sistema, que foram instalados diretamente a partir da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6c92-168">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[localizar DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[encontrar o módulo]: /powershell/module/powershellget/Find-Module
[Find-Module]: /powershell/module/powershellget/Find-Module
[localizar Script]: /powershell/module/powershellget/Find-Script
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Instalar módulo]: /powershell/module/powershellget/Install-Module
[Install-Module]: /powershell/module/powershellget/Install-Module
[Script de instalação]: /powershell/module/powershellget/Install-Script
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[guardar-Module]: /powershell/module/powershellget/Save-Module
[Save-Module]: /powershell/module/powershellget/Save-Module
[Guardar Script]: /powershell/module/powershellget/Save-Script
[Save-Script]: /powershell/module/powershellget/Save-Script