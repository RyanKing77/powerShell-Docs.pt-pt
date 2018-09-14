---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Comece com a galeria do PowerShell
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523061"
---
# <a name="get-started-with-the-powershell-gallery"></a><span data-ttu-id="bcb15-103">Comece com a galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="bcb15-103">Get Started with the PowerShell Gallery</span></span>

<span data-ttu-id="bcb15-104">O modo adequado para instalar itens a partir da galeria do PowerShell é usar os cmdlets do [PowerShellGet](/powershell/module/powershellget) módulo.</span><span class="sxs-lookup"><span data-stu-id="bcb15-104">The proper way to install items from the PowerShell Gallery is to use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module.</span></span> <span data-ttu-id="bcb15-105">Não é necessário iniciar sessão para transferir os itens da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bcb15-105">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="bcb15-106">É possível transferir um pacote a partir da galeria do PowerShell diretamente, mas não se trata de uma abordagem recomendada.</span><span class="sxs-lookup"><span data-stu-id="bcb15-106">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span> <span data-ttu-id="bcb15-107">Para obter mais detalhes, consulte [transferir o pacote Manual](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span><span class="sxs-lookup"><span data-stu-id="bcb15-107">For more details, see [Manual Package Download](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).</span></span>  


## <a name="discovering-items-from-the-powershell-gallery"></a><span data-ttu-id="bcb15-108">A detetar itens da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="bcb15-108">Discovering items from the PowerShell Gallery</span></span>

<span data-ttu-id="bcb15-109">Pode encontrar itens na galeria do PowerShell com o **pesquisa** controle neste site, ou ao navegar por meio das páginas de Scripts e módulos.</span><span class="sxs-lookup"><span data-stu-id="bcb15-109">You can find items in the PowerShell Gallery by using the **Search** control on this website, or by browsing through the Modules and Scripts pages.</span></span> <span data-ttu-id="bcb15-110">Também pode encontrar itens da galeria do PowerShell ao executar o [Find-Module][] e [Find-Script][] cmdlets, dependendo do tipo de item, com `-Repository PSGallery`.</span><span class="sxs-lookup"><span data-stu-id="bcb15-110">You can also find items from the PowerShell Gallery by running the [Find-Module][] and [Find-Script][] cmdlets, depending on the item type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="bcb15-111">Filtragem de resultados a partir da galeria pode ser feito utilizando os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="bcb15-111">Filtering results from the Gallery can be done by using the following parameters:</span></span>

- <span data-ttu-id="bcb15-112">Nome</span><span class="sxs-lookup"><span data-stu-id="bcb15-112">Name</span></span>
- <span data-ttu-id="bcb15-113">AllVersions</span><span class="sxs-lookup"><span data-stu-id="bcb15-113">AllVersions</span></span>
- <span data-ttu-id="bcb15-114">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="bcb15-114">MinimumVersion</span></span>
- <span data-ttu-id="bcb15-115">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="bcb15-115">RequiredVersion</span></span>
- <span data-ttu-id="bcb15-116">Sinalizador</span><span class="sxs-lookup"><span data-stu-id="bcb15-116">Tag</span></span>
- <span data-ttu-id="bcb15-117">Inclui</span><span class="sxs-lookup"><span data-stu-id="bcb15-117">Includes</span></span>
- <span data-ttu-id="bcb15-118">DscResource</span><span class="sxs-lookup"><span data-stu-id="bcb15-118">DscResource</span></span>
- <span data-ttu-id="bcb15-119">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="bcb15-119">RoleCapability</span></span>
- <span data-ttu-id="bcb15-120">Comando</span><span class="sxs-lookup"><span data-stu-id="bcb15-120">Command</span></span>
- <span data-ttu-id="bcb15-121">Filtro</span><span class="sxs-lookup"><span data-stu-id="bcb15-121">Filter</span></span>

<span data-ttu-id="bcb15-122">Se só estiver interessado em detetar recursos de DSC específicos na galeria, pode executar o [Find-DscResource] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bcb15-122">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="bcb15-123">Find-DscResource devolve dados nos recursos de DSC contidos na galeria.</span><span class="sxs-lookup"><span data-stu-id="bcb15-123">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="bcb15-124">Como recursos de DSC sempre são fornecidos como parte de um módulo, ainda precisa executar [Install-Module][] para instalar esses recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="bcb15-124">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-items-in-the-powershell-gallery"></a><span data-ttu-id="bcb15-125">Saber mais sobre os itens da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="bcb15-125">Learning about items in the PowerShell Gallery</span></span>

<span data-ttu-id="bcb15-126">Depois de identificar um item que está interessado, pode querer saber mais sobre ele.</span><span class="sxs-lookup"><span data-stu-id="bcb15-126">Once you've identified an item you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="bcb15-127">Pode fazê-lo, examinando a página específica desse item na galeria.</span><span class="sxs-lookup"><span data-stu-id="bcb15-127">You can do this by examining that item's specific page on the Gallery.</span></span> <span data-ttu-id="bcb15-128">Nessa página, poderá ver todos os metadados carregados com o item.</span><span class="sxs-lookup"><span data-stu-id="bcb15-128">On that page, you'll be able to see all of the metadata uploaded with the item.</span></span> <span data-ttu-id="bcb15-129">Esses metadados para um item é fornecido pelo autor do item e não é verificado pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bcb15-129">This metadata for an item is provided by the item's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="bcb15-130">O proprietário do item está intimamente ligado à conta utilizada para publicar o item de galeria e é mais confiável do que o campo de autor.</span><span class="sxs-lookup"><span data-stu-id="bcb15-130">The Owner of the item is strongly tied to the Gallery account used to publish the item, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="bcb15-131">Se descobrir que um item que se sentir não está publicado em boa fé, clique em **relatar abuso** na página desse item.</span><span class="sxs-lookup"><span data-stu-id="bcb15-131">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

<span data-ttu-id="bcb15-132">Se estiver a executar [Find-Module][] ou [Find-Script][], pode ver estes dados no objeto PSGetModuleInfo retornado.</span><span class="sxs-lookup"><span data-stu-id="bcb15-132">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="bcb15-133">Por exemplo, executar `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span><span class="sxs-lookup"><span data-stu-id="bcb15-133">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="bcb15-134">Devolve os dados no módulo PSReadLine na galeria.</span><span class="sxs-lookup"><span data-stu-id="bcb15-134">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-items-from-the-powershell-gallery"></a><span data-ttu-id="bcb15-135">Transferência de itens da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="bcb15-135">Downloading items from the PowerShell Gallery</span></span>

<span data-ttu-id="bcb15-136">Recomendamos o seguinte processo quando a transferência de itens da galeria do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bcb15-136">We encourage the following process when downloading items from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="bcb15-137">Inspecionar</span><span class="sxs-lookup"><span data-stu-id="bcb15-137">Inspect</span></span>

<span data-ttu-id="bcb15-138">Para transferir um item da Galeria para inspeção, execute o [Save-Module][] ou [Save-Script][] cmdlet, dependendo do tipo de item.</span><span class="sxs-lookup"><span data-stu-id="bcb15-138">To download an item from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the item type.</span></span> <span data-ttu-id="bcb15-139">Isto permite-lhe guardar o item localmente sem instalá-lo e inspecionar os conteúdos de item.</span><span class="sxs-lookup"><span data-stu-id="bcb15-139">This lets you save the item locally without installing it, and inspect the item contents.</span></span> <span data-ttu-id="bcb15-140">Não se esqueça de eliminar o item guardado manualmente.</span><span class="sxs-lookup"><span data-stu-id="bcb15-140">Remember to delete the saved item manually.</span></span>

<span data-ttu-id="bcb15-141">Alguns desses itens são criados pela Microsoft e outros são criados pela Comunidade do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bcb15-141">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="bcb15-142">A Microsoft recomenda que reveja o conteúdo e o código de itens na Galeria deste antes da instalação.</span><span class="sxs-lookup"><span data-stu-id="bcb15-142">Microsoft recommends that you review the contents and code of items on this gallery prior to installation.</span></span>

<span data-ttu-id="bcb15-143">Se descobrir que um item que se sentir não está publicado em boa fé, clique em **relatar abuso** na página desse item.</span><span class="sxs-lookup"><span data-stu-id="bcb15-143">If you discover an item that you feel is not published in good faith, click **Report Abuse** on that item's page.</span></span>

### <a name="install"></a><span data-ttu-id="bcb15-144">Instalar</span><span class="sxs-lookup"><span data-stu-id="bcb15-144">Install</span></span>

<span data-ttu-id="bcb15-145">Para instalar um item da Galeria para uso, execute o [Install-Module][] ou [Script de instalação][] cmdlet, dependendo do tipo de item.</span><span class="sxs-lookup"><span data-stu-id="bcb15-145">To install an item from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the item type.</span></span>

<span data-ttu-id="bcb15-146">[Install-Module][] instala o módulo para `$env:ProgramFiles\WindowsPowerShell\Modules` por predefinição.</span><span class="sxs-lookup"><span data-stu-id="bcb15-146">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="bcb15-147">Isto requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="bcb15-147">This requires an administrator account.</span></span> <span data-ttu-id="bcb15-148">Se adicionar o `-Scope CurrentUser` parâmetro, o módulo é instalado `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="bcb15-148">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="bcb15-149">[Script de instalação][] instala o script para `$env:ProgramFiles\WindowsPowerShell\Scripts` por predefinição.</span><span class="sxs-lookup"><span data-stu-id="bcb15-149">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="bcb15-150">Isto requer uma conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="bcb15-150">This requires an administrator account.</span></span> <span data-ttu-id="bcb15-151">Se adicionar o `-Scope CurrentUser` parâmetro, o script está instalado para `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="bcb15-151">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="bcb15-152">Por predefinição, [Install-Module][] e [Script de instalação][] instala a versão mais atual de um item.</span><span class="sxs-lookup"><span data-stu-id="bcb15-152">By default, [Install-Module][] and [Install-Script][] installs the most current version of an item.</span></span>
<span data-ttu-id="bcb15-153">Para instalar uma versão mais antiga do item, adicione o `-RequiredVersion` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bcb15-153">To install an older version of the item, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="bcb15-154">Implementar</span><span class="sxs-lookup"><span data-stu-id="bcb15-154">Deploy</span></span>

<span data-ttu-id="bcb15-155">Para implementar um item da galeria do PowerShell para automatização do Azure, clique em **implementar a automatização do Azure** na página de detalhes do item.</span><span class="sxs-lookup"><span data-stu-id="bcb15-155">To deploy an item from the PowerShell Gallery to Azure Automation, click **Deploy to Azure Automation** on the item details page.</span></span> <span data-ttu-id="bcb15-156">Será redirecionado para o Portal de gestão do Azure, em que inicie sessão com as credenciais da conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="bcb15-156">You will be redirected to the Azure Management Portal, where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="bcb15-157">Tenha em atenção que a implementação de itens com dependências implantará todas as dependências para automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="bcb15-157">Note that deploying items with dependencies will deploy all the dependencies to Azure Automation.</span></span> <span data-ttu-id="bcb15-158">O botão "Implementar a automatização do Azure" pode ser desativado ao adicionar o **AzureAutomationNotSupported** etiqueta para os metadados do item.</span><span class="sxs-lookup"><span data-stu-id="bcb15-158">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your item metadata.</span></span>

<span data-ttu-id="bcb15-159">Para saber mais sobre a automatização do Azure, veja a [automatização do Azure](/azure/automation) documentação.</span><span class="sxs-lookup"><span data-stu-id="bcb15-159">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-items-from-the-powershell-gallery"></a><span data-ttu-id="bcb15-160">A atualizar itens da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="bcb15-160">Updating items from the PowerShell Gallery</span></span>

<span data-ttu-id="bcb15-161">Para atualizar itens instalados a partir da galeria do PowerShell, execute o [Update-Module] [-] ou [Script de atualização] [] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bcb15-161">To update items installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="bcb15-162">Quando executado sem quaisquer parâmetros adicionais, [Update-Module] [-] tenta atualizar cada módulo instalado, executando [Install-Module][].</span><span class="sxs-lookup"><span data-stu-id="bcb15-162">When run without any additional parameters, [Update-Module][] attempts to update each module installed by running [Install-Module][].</span></span> <span data-ttu-id="bcb15-163">Para atualizar seletivamente módulos, adicione o `-Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bcb15-163">To selectively update modules, add the `-Name` parameter.</span></span>

<span data-ttu-id="bcb15-164">Da mesma forma, quando executado sem quaisquer parâmetros adicionais, [Script de atualização] [-] também tenta atualizar cada script instalado, executando [Script de instalação][].</span><span class="sxs-lookup"><span data-stu-id="bcb15-164">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update each script installed by running [Install-Script][].</span></span> <span data-ttu-id="bcb15-165">Para atualizar os scripts seletivamente, adicione o `-Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bcb15-165">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="bcb15-166">Itens de lista que tiver instalado a partir da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="bcb15-166">List items that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="bcb15-167">Para saber quais os módulos tiver instalado a partir da galeria do PowerShell, execute o [Get-InstalledModule][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bcb15-167">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="bcb15-168">Este comando lista todos os módulos que tem no seu sistema que foram instalados diretamente a partir da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bcb15-168">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="bcb15-169">Da mesma forma, para saber quais os scripts tiver instalado a partir da galeria do PowerShell, execute o [Get-InstalledScript][] cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bcb15-169">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="bcb15-170">Este comando lista todos os scripts que tem no seu sistema que foram instalados diretamente a partir da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bcb15-170">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Script de instalação]: /powershell/module/powershellget/Install-Script
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script