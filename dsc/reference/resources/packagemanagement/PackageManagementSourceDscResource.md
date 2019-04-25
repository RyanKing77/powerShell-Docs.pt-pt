---
ms.date: 06/20/2018
keywords: DSC, powershell, configuração, a configuração
title: Recursos do DSC PackageManagementSource
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077590"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="d8c38-103">Recursos do DSC PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="d8c38-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="d8c38-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="d8c38-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="d8c38-105">O **PackageManagementSource** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para registar ou anular o registo de origens do pacote de gestão num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="d8c38-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="d8c38-106">**Origens de gestão do pacote registadas dessa forma são registadas no contexto de sistema, utilizável pela conta do sistema ou pelo motor de DSC.**</span><span class="sxs-lookup"><span data-stu-id="d8c38-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="d8c38-107">Este recurso requer o **PackageManagement** módulo, disponível no http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="d8c38-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8c38-108">O **PackageManagement** módulo deve ser, pelo menos, versão 1.1.7.0 as seguintes informações de propriedade esteja correto.</span><span class="sxs-lookup"><span data-stu-id="d8c38-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8c38-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8c38-109">Syntax</span></span>

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a><span data-ttu-id="d8c38-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d8c38-110">Properties</span></span>

|  <span data-ttu-id="d8c38-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d8c38-111">Property</span></span>  |  <span data-ttu-id="d8c38-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8c38-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="d8c38-113">Nome</span><span class="sxs-lookup"><span data-stu-id="d8c38-113">Name</span></span>| <span data-ttu-id="d8c38-114">Especifica o nome da origem do pacote a ser efetuado ou cancelado no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="d8c38-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="d8c38-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="d8c38-115">ProviderName</span></span>| <span data-ttu-id="d8c38-116">Especifica o nome do fornecedor OneGet por meio do qual pode fornecer interoperabilidade com a origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="d8c38-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="d8c38-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="d8c38-117">SourceLocation</span></span>| <span data-ttu-id="d8c38-118">Especifica o URI de origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="d8c38-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="d8c38-119">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="d8c38-119">Ensure</span></span>| <span data-ttu-id="d8c38-120">Determina se a origem do pacote deve ser efetuado ou cancelado.</span><span class="sxs-lookup"><span data-stu-id="d8c38-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="d8c38-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="d8c38-121">InstallationPolicy</span></span>| <span data-ttu-id="d8c38-122">Utilizado por fornecedores, como o fornecedor de Nuget incorporado.</span><span class="sxs-lookup"><span data-stu-id="d8c38-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="d8c38-123">Determina se confiam origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="d8c38-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="d8c38-124">Um dos: "Não confiáveis", "fidedigno".</span><span class="sxs-lookup"><span data-stu-id="d8c38-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="d8c38-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="d8c38-125">SourceCredential</span></span>| <span data-ttu-id="d8c38-126">Fornece acesso ao pacote de sobre uma origem remota.</span><span class="sxs-lookup"><span data-stu-id="d8c38-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="d8c38-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8c38-127">Example</span></span>

<span data-ttu-id="d8c38-128">Neste exemplo registra o http://nuget.org pacote de origem com o **PackageManagementSource** recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="d8c38-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```