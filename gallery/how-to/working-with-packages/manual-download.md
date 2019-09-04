---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeria, PowerShell, psgallery
title: Transferência manual de pacotes
ms.openlocfilehash: c0a96e866dfd27f9b2170ea540ec6dd0c67701fd
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215459"
---
# <a name="manual-package-download"></a><span data-ttu-id="52c77-103">Transferência manual de pacotes</span><span class="sxs-lookup"><span data-stu-id="52c77-103">Manual Package Download</span></span>

<span data-ttu-id="52c77-104">O Galeria do PowerShell dá suporte ao download de um pacote diretamente do site, sem usar os cmdlets do PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="52c77-104">The PowerShell Gallery supports downloading a package from the website directly, without using the PowerShellGet cmdlets.</span></span> <span data-ttu-id="52c77-105">Você pode baixar qualquer pacote como um arquivo de pacote`.nupkg`NuGet (), que você pode copiar para um repositório interno.</span><span class="sxs-lookup"><span data-stu-id="52c77-105">You can download any package as a NuGet package (`.nupkg`) file, which you can then copy to an internal repository.</span></span>

> [!NOTE]
> <span data-ttu-id="52c77-106">O download do pacote manual **não** se destina como uma substituição `Install-Module` para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="52c77-106">Manual package download is **not** intended as a replacement for the `Install-Module` cmdlet.</span></span>
> <span data-ttu-id="52c77-107">O download do pacote não instala o módulo ou o script.</span><span class="sxs-lookup"><span data-stu-id="52c77-107">Downloading the package doesn't install the module or script.</span></span> <span data-ttu-id="52c77-108">As dependências não estão incluídas no pacote NuGet baixado.</span><span class="sxs-lookup"><span data-stu-id="52c77-108">Dependencies aren't included in the NuGet package downloaded.</span></span> <span data-ttu-id="52c77-109">As instruções a seguir são fornecidas apenas para fins de referência.</span><span class="sxs-lookup"><span data-stu-id="52c77-109">The following instructions are provided for reference purposes only.</span></span>

## <a name="using-manual-download-to-acquire-a-package"></a><span data-ttu-id="52c77-110">Usando o download manual para adquirir um pacote</span><span class="sxs-lookup"><span data-stu-id="52c77-110">Using manual download to acquire a package</span></span>

<span data-ttu-id="52c77-111">Cada página tem um link para download manual, como mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="52c77-111">Each page has a link for Manual Download, as shown here:</span></span>

![Download manual](../../Images/packagedisplaypagewithpseditions.png)

<span data-ttu-id="52c77-113">Para baixar manualmente, clique em **baixar o arquivo RAW nupkg**.</span><span class="sxs-lookup"><span data-stu-id="52c77-113">To download manually, click on **Download the raw nupkg file**.</span></span> <span data-ttu-id="52c77-114">Uma cópia do pacote é copiada para a pasta de download do seu navegador com o `<name>.<version>.nupkg`nome.</span><span class="sxs-lookup"><span data-stu-id="52c77-114">A copy of the package is copied to the download folder for your browser with the name `<name>.<version>.nupkg`.</span></span>

<span data-ttu-id="52c77-115">Um pacote NuGet é um arquivo ZIP com arquivos extras contendo informações sobre o conteúdo do pacote.</span><span class="sxs-lookup"><span data-stu-id="52c77-115">A NuGet package is a ZIP archive with extra files containing information about the contents of the package.</span></span> <span data-ttu-id="52c77-116">Alguns navegadores, como o Internet Explorer, substituem automaticamente a `.zip`extensão de `.nupkg` arquivo por.</span><span class="sxs-lookup"><span data-stu-id="52c77-116">Some browsers, like Internet Explorer, automatically replace the `.nupkg` file extension with `.zip`.</span></span> <span data-ttu-id="52c77-117">Para expandir o pacote, renomeie `.nupkg` o `.zip`arquivo como, se necessário, e extraia o conteúdo para uma pasta local.</span><span class="sxs-lookup"><span data-stu-id="52c77-117">To expand the package, rename the `.nupkg` file to `.zip`, if needed, then extract the contents to a local folder.</span></span>

<span data-ttu-id="52c77-118">Um arquivo de pacote NuGet inclui os seguintes **elementos específicos do NuGet** que não fazem parte do código do pacote original:</span><span class="sxs-lookup"><span data-stu-id="52c77-118">A NuGet package file includes the following **NuGet-specific elements** that aren't part of the original packaged code:</span></span>

- <span data-ttu-id="52c77-119">Uma pasta chamada `_rels` -contém um `.rels` arquivo que lista as dependências</span><span class="sxs-lookup"><span data-stu-id="52c77-119">A folder named `_rels` - contains a `.rels` file that lists the dependencies</span></span>
- <span data-ttu-id="52c77-120">Uma pasta chamada `package` -contém os dados específicos do NuGet</span><span class="sxs-lookup"><span data-stu-id="52c77-120">A folder named `package` - contains the NuGet-specific data</span></span>
- <span data-ttu-id="52c77-121">Um arquivo nomeado `[Content_Types].xml` -descreve como as extensões como o PowerShellGet funcionam com o NuGet</span><span class="sxs-lookup"><span data-stu-id="52c77-121">A file named `[Content_Types].xml` - describes how extensions like PowerShellGet work with NuGet</span></span>
- <span data-ttu-id="52c77-122">Um arquivo chamado `<name>.nuspec` -contém a massa dos metadados</span><span class="sxs-lookup"><span data-stu-id="52c77-122">A file named `<name>.nuspec` - contains the bulk of the metadata</span></span>

## <a name="installing-powershell-modules-from-a-nuget-package"></a><span data-ttu-id="52c77-123">Instalando módulos do PowerShell de um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="52c77-123">Installing PowerShell modules from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="52c77-124">Essas instruções **não** dão o mesmo resultado que a execução `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="52c77-124">These instructions **DO NOT** give the same result as running `Install-Module`.</span></span> <span data-ttu-id="52c77-125">Essas instruções atendem aos requisitos mínimos.</span><span class="sxs-lookup"><span data-stu-id="52c77-125">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="52c77-126">Eles não se destinam a ser `Install-Module`uma substituição para.</span><span class="sxs-lookup"><span data-stu-id="52c77-126">They aren't intended to be a replacement for `Install-Module`.</span></span>
> <span data-ttu-id="52c77-127">Algumas etapas executadas pelo `Install-Module` não são incluídas.</span><span class="sxs-lookup"><span data-stu-id="52c77-127">Some steps performed by `Install-Module` aren't included.</span></span>

<span data-ttu-id="52c77-128">A abordagem mais fácil é remover os elementos específicos do NuGet da pasta.</span><span class="sxs-lookup"><span data-stu-id="52c77-128">The easiest approach is to remove the NuGet-specific elements from the folder.</span></span> <span data-ttu-id="52c77-129">A remoção dos elementos deixa o código do PowerShell criado pelo autor do pacote.</span><span class="sxs-lookup"><span data-stu-id="52c77-129">Removing the elements leaves the PowerShell code created by the package author.</span></span>
<span data-ttu-id="52c77-130">Para obter a lista de elementos específicos do NuGet, consulte [usando o download manual para adquirir um pacote](#using-manual-download-to-acquire-a-package).</span><span class="sxs-lookup"><span data-stu-id="52c77-130">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

<span data-ttu-id="52c77-131">Os passos são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="52c77-131">The steps are as follows:</span></span>

1. <span data-ttu-id="52c77-132">Extraia o conteúdo do pacote NuGet para uma pasta local.</span><span class="sxs-lookup"><span data-stu-id="52c77-132">Extract the contents of the NuGet package to a local folder.</span></span>
2. <span data-ttu-id="52c77-133">Exclua os elementos específicos do NuGet da pasta.</span><span class="sxs-lookup"><span data-stu-id="52c77-133">Delete the NuGet-specific elements from the folder.</span></span>
3. <span data-ttu-id="52c77-134">Renomeie a pasta.</span><span class="sxs-lookup"><span data-stu-id="52c77-134">Rename the folder.</span></span> <span data-ttu-id="52c77-135">O nome da pasta padrão geralmente `<name>.<version>`é.</span><span class="sxs-lookup"><span data-stu-id="52c77-135">The default folder name is usually `<name>.<version>`.</span></span> <span data-ttu-id="52c77-136">A versão pode incluir `-prerelease` se o módulo estiver marcado como uma versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="52c77-136">The version can include `-prerelease` if the module is tagged as a prerelease version.</span></span> <span data-ttu-id="52c77-137">Renomeie a pasta apenas para o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="52c77-137">Rename the folder to just the module name.</span></span> <span data-ttu-id="52c77-138">Por exemplo, `azurerm.storage.5.0.4-preview` torna `azurerm.storage`-se.</span><span class="sxs-lookup"><span data-stu-id="52c77-138">For example, `azurerm.storage.5.0.4-preview` becomes `azurerm.storage`.</span></span>
4. <span data-ttu-id="52c77-139">Copie a pasta para uma das pastas no `$env:PSModulePath value`.</span><span class="sxs-lookup"><span data-stu-id="52c77-139">Copy the folder to one of the folders in the `$env:PSModulePath value`.</span></span> <span data-ttu-id="52c77-140">`$env:PSModulePath`é um conjunto delimitado por ponto-e-vírgula de caminhos nos quais o PowerShell deve procurar módulos.</span><span class="sxs-lookup"><span data-stu-id="52c77-140">`$env:PSModulePath` is a semicolon-delimited set of paths in which PowerShell should look for modules.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52c77-141">O download manual não inclui nenhuma dependência exigida pelo módulo.</span><span class="sxs-lookup"><span data-stu-id="52c77-141">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="52c77-142">Se o pacote tiver dependências, eles deverão ser instalados no sistema para que este módulo funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="52c77-142">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="52c77-143">O Galeria do PowerShell mostra todas as dependências exigidas pelo pacote.</span><span class="sxs-lookup"><span data-stu-id="52c77-143">The PowerShell Gallery shows all dependencies required by the package.</span></span>

## <a name="installing-powershell-scripts-from-a-nuget-package"></a><span data-ttu-id="52c77-144">Instalando scripts do PowerShell de um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="52c77-144">Installing PowerShell scripts from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="52c77-145">Essas instruções **não** dão o mesmo resultado que a execução `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="52c77-145">These instructions **DO NOT** give the same result as running `Install-Script`.</span></span> <span data-ttu-id="52c77-146">Essas instruções atendem aos requisitos mínimos.</span><span class="sxs-lookup"><span data-stu-id="52c77-146">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="52c77-147">Eles não se destinam a ser `Install-Script`uma substituição para.</span><span class="sxs-lookup"><span data-stu-id="52c77-147">They aren't intended to be a replacement for `Install-Script`.</span></span>

<span data-ttu-id="52c77-148">A abordagem mais fácil é extrair o pacote NuGet e, em seguida, usar o script diretamente.</span><span class="sxs-lookup"><span data-stu-id="52c77-148">The easiest approach is to extract the NuGet package, then use the script directly.</span></span>

<span data-ttu-id="52c77-149">Os passos são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="52c77-149">The steps are as follows:</span></span>

1. <span data-ttu-id="52c77-150">Extraia o conteúdo do pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="52c77-150">Extract the contents of the NuGet package.</span></span>
2. <span data-ttu-id="52c77-151">O `.PS1` arquivo na pasta pode ser usado diretamente deste local.</span><span class="sxs-lookup"><span data-stu-id="52c77-151">The `.PS1` file in the folder can be used directly from this location.</span></span>
3. <span data-ttu-id="52c77-152">Você pode excluir os elementos específicos do NuGet na pasta.</span><span class="sxs-lookup"><span data-stu-id="52c77-152">You may delete the NuGet-specific elements in the folder.</span></span>

<span data-ttu-id="52c77-153">Para obter a lista de elementos específicos do NuGet, consulte [usando o download manual para adquirir um pacote](#using-manual-download-to-acquire-a-package).</span><span class="sxs-lookup"><span data-stu-id="52c77-153">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52c77-154">O download manual não inclui nenhuma dependência exigida pelo módulo.</span><span class="sxs-lookup"><span data-stu-id="52c77-154">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="52c77-155">Se o pacote tiver dependências, eles deverão ser instalados no sistema para que este módulo funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="52c77-155">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="52c77-156">O Galeria do PowerShell mostra todas as dependências exigidas pelo pacote.</span><span class="sxs-lookup"><span data-stu-id="52c77-156">The PowerShell Gallery shows all dependencies required by the package.</span></span>
