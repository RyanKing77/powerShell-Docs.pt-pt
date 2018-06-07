---
ms.date: 06/20/2018
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC PackageManagement
ms.openlocfilehash: 3d52934b130d59acee4d7f8a92da2c743c1eb305
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753792"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="2143a-103">Recursos do DSC PackageManagement</span><span class="sxs-lookup"><span data-stu-id="2143a-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="2143a-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2143a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="2143a-105">O **PackageManagement** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes de gestão de pacotes num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="2143a-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="2143a-106">Este recurso necessita do **PackageManagement** módulo, disponível a partir do http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="2143a-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2143a-107">O **PackageManagement** módulo deve ser, pelo menos, versão 1.1.7.0 as seguintes informações de propriedade corretas.</span><span class="sxs-lookup"><span data-stu-id="2143a-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="2143a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2143a-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="2143a-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2143a-109">Properties</span></span>

|  <span data-ttu-id="2143a-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2143a-110">Property</span></span>  |  <span data-ttu-id="2143a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="2143a-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="2143a-112">Nome</span><span class="sxs-lookup"><span data-stu-id="2143a-112">Name</span></span>| <span data-ttu-id="2143a-113">Especifica o nome do pacote para ser instalada ou desinstalada.</span><span class="sxs-lookup"><span data-stu-id="2143a-113">Specifies the name of the Package to be installed or uninstalled.</span></span>|
| <span data-ttu-id="2143a-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="2143a-114">AdditionalParameters</span></span>| <span data-ttu-id="2143a-115">Tabela de hash específica do fornecedor de parâmetros transferidos para `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="2143a-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="2143a-116">Por exemplo, para o fornecedor do NuGet pode passar parâmetros adicionais, como DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="2143a-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>|
| <span data-ttu-id="2143a-117">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="2143a-117">Ensure</span></span>| <span data-ttu-id="2143a-118">Determina se o pacote é para ser instalada ou desinstalada.</span><span class="sxs-lookup"><span data-stu-id="2143a-118">Determines whether the package is to be installed or uninstalled.</span></span>|
| <span data-ttu-id="2143a-119">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="2143a-119">MaximumVersion</span></span>|<span data-ttu-id="2143a-120">Especifica o máximo permitido de versão do pacote que pretende localizar.</span><span class="sxs-lookup"><span data-stu-id="2143a-120">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="2143a-121">Se não adicionar este parâmetro, o recurso localiza a versão disponível mais recente do pacote.</span><span class="sxs-lookup"><span data-stu-id="2143a-121">If you do not add this parameter, the resource finds the highest available version of the package.</span></span>|
| <span data-ttu-id="2143a-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="2143a-122">MinimumVersion</span></span>|<span data-ttu-id="2143a-123">Especifica o mínimo permitido de versão do pacote que pretende localizar.</span><span class="sxs-lookup"><span data-stu-id="2143a-123">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="2143a-124">Se não adicionar este parâmetro, o recurso localiza a versão disponível mais recente do pacote que também coincida com qualquer versão especificada máximo especificado pelo _MaximumVersion_ parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2143a-124">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="2143a-125">ProviderName</span><span class="sxs-lookup"><span data-stu-id="2143a-125">ProviderName</span></span>| <span data-ttu-id="2143a-126">Especifica um nome de fornecedor do pacote para o qual pretende definir o âmbito da pesquisa de pacote.</span><span class="sxs-lookup"><span data-stu-id="2143a-126">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="2143a-127">Pode obter os nomes de fornecedor do pacote, executando o `Get-PackageProvider` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2143a-127">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>|
| <span data-ttu-id="2143a-128">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="2143a-128">RequiredVersion</span></span>| <span data-ttu-id="2143a-129">Especifica a versão exata do pacote que pretende instalar.</span><span class="sxs-lookup"><span data-stu-id="2143a-129">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="2143a-130">Se não especificar este parâmetro, este recurso de DSC instala a versão disponível mais recente do pacote que também coincida com qualquer versão máxima especificada pelo _MaximumVersion_ parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2143a-130">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the _MaximumVersion_ parameter.</span></span>|
| <span data-ttu-id="2143a-131">Origem</span><span class="sxs-lookup"><span data-stu-id="2143a-131">Source</span></span>| <span data-ttu-id="2143a-132">Especifica o nome da origem do pacote, onde pode encontrar o pacote.</span><span class="sxs-lookup"><span data-stu-id="2143a-132">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="2143a-133">Isto pode ser um URI ou uma origem registada com `Register-PackageSource` ou recurso PackageManagementSource DSC.</span><span class="sxs-lookup"><span data-stu-id="2143a-133">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span>|
| <span data-ttu-id="2143a-134">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="2143a-134">SourceCredential</span></span> | <span data-ttu-id="2143a-135">Especifica uma conta de utilizador que tenha direitos para instalar um pacote para uma origem ou o fornecedor do pacote especificado.</span><span class="sxs-lookup"><span data-stu-id="2143a-135">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>|

## <a name="additional-parameters"></a><span data-ttu-id="2143a-136">Parâmetros adicionais</span><span class="sxs-lookup"><span data-stu-id="2143a-136">Additional Parameters</span></span>

<span data-ttu-id="2143a-137">A tabela seguinte lista as opções para a propriedade AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="2143a-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="2143a-138">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="2143a-138">Parameter</span></span>  | <span data-ttu-id="2143a-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="2143a-139">Description</span></span>   |
|---|---|
| <span data-ttu-id="2143a-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="2143a-140">DestinationPath</span></span>| <span data-ttu-id="2143a-141">Utilizada pelos fornecedores, tais como o fornecedor do Nuget incorporada.</span><span class="sxs-lookup"><span data-stu-id="2143a-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="2143a-142">Especifica uma localização de ficheiros onde pretende que o pacote de instalação.</span><span class="sxs-lookup"><span data-stu-id="2143a-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="2143a-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="2143a-143">InstallationPolicy</span></span>| <span data-ttu-id="2143a-144">Utilizada pelos fornecedores, tais como o fornecedor do Nuget incorporada.</span><span class="sxs-lookup"><span data-stu-id="2143a-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="2143a-145">Determina se confiar origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="2143a-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="2143a-146">Um dos: "Não fidedignas", "Fidedigna".</span><span class="sxs-lookup"><span data-stu-id="2143a-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="2143a-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2143a-147">Example</span></span>

<span data-ttu-id="2143a-148">Este exemplo instala o **JQuery** pacote NuGet e **GistProvider** utilizando o módulo PowerShell do **PackageManagement** recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="2143a-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="2143a-149">Neste exemplo garante primeiro as origens de pacotes estão disponíveis, em seguida, define o estado esperado do **JQuery** e **GistProvider** pacotes (NuGet e o PowerShell, respetivamente).</span><span class="sxs-lookup"><span data-stu-id="2143a-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

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