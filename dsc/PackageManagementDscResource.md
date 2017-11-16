---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC PackageManagement
ms.openlocfilehash: a984fbf5db561a696d89b60dde8b92096c6e4924
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="13e00-103">Recursos do DSC PackageManagement</span><span class="sxs-lookup"><span data-stu-id="13e00-103">DSC PackageManagement Resource</span></span>

> <span data-ttu-id="13e00-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="13e00-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="13e00-105">O **PackageManagement** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes de gestão de pacotes num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="13e00-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="13e00-106">Este recurso necessita do **PackageManagement** módulo, disponível a partir do http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="13e00-106">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="13e00-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13e00-107">Syntax</span></span>

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="13e00-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="13e00-108">Properties</span></span>
|  <span data-ttu-id="13e00-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="13e00-109">Property</span></span>  |  <span data-ttu-id="13e00-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="13e00-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="13e00-111">Nome</span><span class="sxs-lookup"><span data-stu-id="13e00-111">Name</span></span>| <span data-ttu-id="13e00-112">Especifica o nome do pacote para ser instalada ou desinstalada.</span><span class="sxs-lookup"><span data-stu-id="13e00-112">Specifies the name of the Package to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="13e00-113">Origem</span><span class="sxs-lookup"><span data-stu-id="13e00-113">Source</span></span>| <span data-ttu-id="13e00-114">Especifica o nome da origem do pacote, onde pode encontrar o pacote.</span><span class="sxs-lookup"><span data-stu-id="13e00-114">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="13e00-115">Isto pode ser um URI ou uma origem registado com recurso Register-PackageSource ou PackageManagementSource DSC.</span><span class="sxs-lookup"><span data-stu-id="13e00-115">This can either be a URI or a source registered with Register-PackageSource or PackageManagementSource DSC resource.</span></span> <span data-ttu-id="13e00-116">O recurso de DSC MSFT_PackageManagementSource também pode registar uma origem de pacote.</span><span class="sxs-lookup"><span data-stu-id="13e00-116">The DSC resource MSFT_PackageManagementSource can also register a package source.</span></span>| 
| <span data-ttu-id="13e00-117">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="13e00-117">Ensure</span></span>| <span data-ttu-id="13e00-118">Determina se o pacote é para ser instalada ou desinstalada.</span><span class="sxs-lookup"><span data-stu-id="13e00-118">Determines whether the package is to be installed or uninstalled.</span></span>| 
| <span data-ttu-id="13e00-119">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="13e00-119">RequiredVersion</span></span>| <span data-ttu-id="13e00-120">Especifica a versão exata do pacote que pretende instalar.</span><span class="sxs-lookup"><span data-stu-id="13e00-120">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="13e00-121">Se não especificar este parâmetro, este recurso de DSC instala a versão disponível mais recente do pacote que também coincida com qualquer versão máxima especificada pelo parâmetro MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="13e00-121">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="13e00-122">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="13e00-122">MinimumVersion</span></span>| <span data-ttu-id="13e00-123">Especifica o mínimo permitido de versão do pacote que pretende instalar.</span><span class="sxs-lookup"><span data-stu-id="13e00-123">Specifies the minimum allowed version of the package that you want to install.</span></span> <span data-ttu-id="13e00-124">Se adicionar este parâmetro, neste intalls de recursos do DSC a versão disponível mais recente do pacote que também coincida com qualquer versão especificada máximo especificado pelo parâmetro MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="13e00-124">If you do not add this parameter, this DSC resource intalls the highest available version of the package that also satisfies any maximum specified version specified by the MaximumVersion parameter.</span></span>| 
| <span data-ttu-id="13e00-125">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="13e00-125">MaximumVersion</span></span>| <span data-ttu-id="13e00-126">Especifica o máximo permitido de versão do pacote que pretende instalar.</span><span class="sxs-lookup"><span data-stu-id="13e00-126">Specifies the maximum allowed version of the package that you want to install.</span></span> <span data-ttu-id="13e00-127">Se não especificar este parâmetro, este recurso de DSC instala a versão disponível mais elevado numeradas do pacote.</span><span class="sxs-lookup"><span data-stu-id="13e00-127">If you do not specify this parameter, this DSC resource installs the highest-numbered available version of the package.</span></span>| 
| <span data-ttu-id="13e00-128">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="13e00-128">SourceCredential</span></span> | <span data-ttu-id="13e00-129">Especifica uma conta de utilizador que tenha direitos para instalar um pacote para uma origem ou o fornecedor do pacote especificado.</span><span class="sxs-lookup"><span data-stu-id="13e00-129">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span>| 
| <span data-ttu-id="13e00-130">ProviderName</span><span class="sxs-lookup"><span data-stu-id="13e00-130">ProviderName</span></span>| <span data-ttu-id="13e00-131">Especifica um nome de fornecedor do pacote para o qual pretende definir o âmbito da pesquisa de pacote.</span><span class="sxs-lookup"><span data-stu-id="13e00-131">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="13e00-132">Pode obter os nomes de fornecedor do pacote, executando o cmdlet Get-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="13e00-132">You can get package provider names by running the Get-PackageProvider cmdlet.</span></span>| 
| <span data-ttu-id="13e00-133">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="13e00-133">AdditionalParameters</span></span>| <span data-ttu-id="13e00-134">Fornecedor parâmetros específicos que são transmitidos como uma tabela hash.</span><span class="sxs-lookup"><span data-stu-id="13e00-134">Provider specific parameters that are passed as an Hashtable.</span></span> <span data-ttu-id="13e00-135">Por exemplo, para o fornecedor do NuGet pode passar parâmetros adicionais, como DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="13e00-135">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span>| 

## <a name="additional-parameters"></a><span data-ttu-id="13e00-136">Parâmetros adicionais</span><span class="sxs-lookup"><span data-stu-id="13e00-136">Additional Parameters</span></span>
<span data-ttu-id="13e00-137">A tabela seguinte lista as opções para a propriedade AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="13e00-137">The following table lists options for the AdditionalParameters property.</span></span>
|  <span data-ttu-id="13e00-138">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="13e00-138">Parameter</span></span>  | <span data-ttu-id="13e00-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="13e00-139">Description</span></span>   | 
|---|---|
| <span data-ttu-id="13e00-140">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="13e00-140">DestinationPath</span></span>| <span data-ttu-id="13e00-141">Utilizada pelos fornecedores, tais como o fornecedor do Nuget incorporada.</span><span class="sxs-lookup"><span data-stu-id="13e00-141">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="13e00-142">Especifica uma localização de ficheiros onde pretende que o pacote de instalação.</span><span class="sxs-lookup"><span data-stu-id="13e00-142">Specifies a file location where you want the package to be installed.</span></span>|
| <span data-ttu-id="13e00-143">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="13e00-143">InstallationPolicy</span></span>| <span data-ttu-id="13e00-144">Utilizada pelos fornecedores, tais como o fornecedor do Nuget incorporada.</span><span class="sxs-lookup"><span data-stu-id="13e00-144">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="13e00-145">Determina se confiar origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="13e00-145">Determines whether you trust the package's source.</span></span> <span data-ttu-id="13e00-146">Um dos: "Não fidedignas", "Fidedigna".</span><span class="sxs-lookup"><span data-stu-id="13e00-146">One of: "Untrusted", "Trusted".</span></span>|

## <a name="example"></a><span data-ttu-id="13e00-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13e00-147">Example</span></span>

<span data-ttu-id="13e00-148">Este exemplo instala o **JQuery** pacote NuGet e **GistProvider** utilizando o módulo PowerShell do **PackageManagement** recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="13e00-148">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="13e00-149">Neste exemplo garante primeiro as origens de pacotes estão disponíveis, em seguida, define o estado esperado do **JQuery** e **GistProvider** pacotes (NuGet e o PowerShell, respetivamente).</span><span class="sxs-lookup"><span data-stu-id="13e00-149">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{    
    PackageManagementSource SourceRepository 
    { 
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
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

