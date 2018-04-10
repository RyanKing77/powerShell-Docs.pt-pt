---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: DSC PackageManagementSource Resource
ms.openlocfilehash: 8c0cb5a3b0a019ddb5ed995406f499298103b07c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="2e954-103">DSC PackageManagementSource Resource</span><span class="sxs-lookup"><span data-stu-id="2e954-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="2e954-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2e954-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2e954-105">O **PackageManagementSource** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para registar ou anular o registo de origens de pacote de gestão num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="2e954-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="2e954-106">**Origens de gestão do pacote registadas desta forma estão registadas no contexto de sistema utilizável pela conta de sistema ou pelo motor de DSC.**</span><span class="sxs-lookup"><span data-stu-id="2e954-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="2e954-107">Este recurso necessita do **PackageManagement** módulo, disponível a partir do http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="2e954-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="2e954-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e954-108">Syntax</span></span>

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="2e954-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2e954-109">Properties</span></span>
|  <span data-ttu-id="2e954-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="2e954-110">Property</span></span>  |  <span data-ttu-id="2e954-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e954-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="2e954-112">Nome</span><span class="sxs-lookup"><span data-stu-id="2e954-112">Name</span></span>| <span data-ttu-id="2e954-113">Especifica o nome da origem do pacote para ser registado ou não registados no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="2e954-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="2e954-114">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="2e954-114">Ensure</span></span>| <span data-ttu-id="2e954-115">Determina se a origem do pacote está a ser registado ou não registados.</span><span class="sxs-lookup"><span data-stu-id="2e954-115">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="2e954-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="2e954-116">InstallationPolicy</span></span>| <span data-ttu-id="2e954-117">Determina se confiar na origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="2e954-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="2e954-118">Um dos: "Não fidedignas", "Fidedigna".</span><span class="sxs-lookup"><span data-stu-id="2e954-118">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="2e954-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="2e954-119">ProviderName</span></span>| <span data-ttu-id="2e954-120">Especifica o nome do fornecedor OneGet através do qual pode interoperabilidade com a origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="2e954-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="2e954-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="2e954-121">SourceUri</span></span>| <span data-ttu-id="2e954-122">Especifica o URI da origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="2e954-122">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="2e954-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="2e954-123">SourceCredential</span></span>| <span data-ttu-id="2e954-124">Fornece acesso ao pacote de uma origem remota.</span><span class="sxs-lookup"><span data-stu-id="2e954-124">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="2e954-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e954-125">Example</span></span>

<span data-ttu-id="2e954-126">Neste exemplo regista o http://nuget.org origem do pacote com o **PackageManagementSource** recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="2e954-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```