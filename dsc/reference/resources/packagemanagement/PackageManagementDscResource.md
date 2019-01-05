---
ms.date: 06/20/2018
keywords: DSC, powershell, configuração, a configuração
title: Recursos do DSC PackageManagement
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048485"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="9bdc3-103">Recursos do DSC PackageManagement</span><span class="sxs-lookup"><span data-stu-id="9bdc3-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="9bdc3-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bdc3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="9bdc3-105">O **PackageManagement** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes de gestão de pacotes num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="9bdc3-106">Este recurso requer o **PackageManagement** módulo, disponível no [ http://PowerShellGallery.com ](http://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="9bdc3-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](http://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9bdc3-107">O **PackageManagement** módulo deve ser, pelo menos, versão 1.1.7.0 as seguintes informações de propriedade esteja correto.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="9bdc3-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bdc3-108">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="9bdc3-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9bdc3-109">Properties</span></span>

| <span data-ttu-id="9bdc3-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="9bdc3-110">Property</span></span> | <span data-ttu-id="9bdc3-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bdc3-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="9bdc3-112">Nome</span><span class="sxs-lookup"><span data-stu-id="9bdc3-112">Name</span></span>| <span data-ttu-id="9bdc3-113">Especifica o nome do pacote a ser instalada ou desinstalada.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="9bdc3-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="9bdc3-114">AdditionalParameters</span></span>| <span data-ttu-id="9bdc3-115">Tabela de hash específica do fornecedor de parâmetros transferidos para `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="9bdc3-116">Por exemplo, para o fornecedor de NuGet pode transmitir parâmetros adicionais, como DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="9bdc3-117">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="9bdc3-117">Ensure</span></span>| <span data-ttu-id="9bdc3-118">Determina se o pacote é para ser instalada ou desinstalada.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="9bdc3-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9bdc3-119">MaximumVersion</span></span>|<span data-ttu-id="9bdc3-120">Especifica o máximo permitido de versão do pacote que pretende localizar.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="9bdc3-121">Se não adicionar este parâmetro, o recurso localiza a versão mais recente disponível do pacote.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="9bdc3-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9bdc3-122">MinimumVersion</span></span>|<span data-ttu-id="9bdc3-123">Especifica o mínimo de versão do pacote que pretende localizar.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="9bdc3-124">Se não adicionar este parâmetro, o recurso localiza a versão mais recente disponível do pacote que satisfaça também qualquer versão especificada máximo especificado pelos _MaximumVersion_ parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="9bdc3-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="9bdc3-125">ProviderName</span></span>| <span data-ttu-id="9bdc3-126">Especifica um nome de fornecedor do pacote ao qual pretende definir o âmbito da pesquisa de pacote.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="9bdc3-127">Pode obter nomes de fornecedor do pacote ao executar o `Get-PackageProvider` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="9bdc3-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9bdc3-128">RequiredVersion</span></span>| <span data-ttu-id="9bdc3-129">Especifica a versão exata do pacote que pretende instalar.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="9bdc3-130">Se não especificar este parâmetro, este recurso de DSC instala a versão disponível mais recente do pacote que também coincida com qualquer versão máximo especificado pelos _MaximumVersion_ parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="9bdc3-131">Origem</span><span class="sxs-lookup"><span data-stu-id="9bdc3-131">Source</span></span>| <span data-ttu-id="9bdc3-132">Especifica o nome da origem do pacote, onde o pacote pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="9bdc3-133">Isso pode ser um URI ou uma origem de registada com `Register-PackageSource` ou recurso de DSC PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="9bdc3-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="9bdc3-134">SourceCredential</span></span> | <span data-ttu-id="9bdc3-135">Especifica uma conta de utilizador que tenha direitos para instalar um pacote para um fornecedor do pacote especificado ou a origem.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="9bdc3-136">Parâmetros adicionais</span><span class="sxs-lookup"><span data-stu-id="9bdc3-136">Additional Parameters</span></span>

<span data-ttu-id="9bdc3-137">A tabela seguinte apresenta uma lista de opções para a propriedade AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-137">The following table lists options for the AdditionalParameters property.</span></span>

| <span data-ttu-id="9bdc3-138">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9bdc3-138">Parameter</span></span> | <span data-ttu-id="9bdc3-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bdc3-139">Description</span></span> |
| --- | --- |
| <span data-ttu-id="9bdc3-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="9bdc3-140">DestinationPath</span></span>| <span data-ttu-id="9bdc3-141">Utilizado por fornecedores, como o fornecedor de Nuget incorporado.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="9bdc3-142">Especifica uma localização do ficheiro onde pretende que o pacote a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="9bdc3-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="9bdc3-143">InstallationPolicy</span></span>| <span data-ttu-id="9bdc3-144">Utilizado por fornecedores, como o fornecedor de Nuget incorporado.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="9bdc3-145">Determina se confiam origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="9bdc3-146">Um dos: `Untrusted`, `Trusted`.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-146">One of: `Untrusted`, `Trusted`.</span></span>|

## <a name="example"></a><span data-ttu-id="9bdc3-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bdc3-147">Example</span></span>

<span data-ttu-id="9bdc3-148">Este exemplo instala o **JQuery** pacote NuGet e **GistProvider** módulo do PowerShell com o **PackageManagement** recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="9bdc3-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="9bdc3-149">Este exemplo primeiro garante que as origens de pacotes estão disponíveis, em seguida, define o estado esperado dos **JQuery** e **GistProvider** pacotes (NuGet e o PowerShell, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="9bdc3-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```