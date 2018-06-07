---
ms.date: 06/20/2018
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC PackageManagementSource
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753775"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="0c96f-103">Recursos do DSC PackageManagementSource</span><span class="sxs-lookup"><span data-stu-id="0c96f-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="0c96f-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c96f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="0c96f-105">O **PackageManagementSource** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para registar ou anular o registo de origens de pacote de gestão num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="0c96f-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="0c96f-106">**Origens de gestão do pacote registadas desta forma estão registadas no contexto de sistema utilizável pela conta de sistema ou pelo motor de DSC.**</span><span class="sxs-lookup"><span data-stu-id="0c96f-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="0c96f-107">Este recurso necessita do **PackageManagement** módulo, disponível a partir do http://PowerShellGallery.com.</span><span class="sxs-lookup"><span data-stu-id="0c96f-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c96f-108">O **PackageManagement** módulo deve ser, pelo menos, versão 1.1.7.0 as seguintes informações de propriedade corretas.</span><span class="sxs-lookup"><span data-stu-id="0c96f-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c96f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c96f-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="0c96f-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0c96f-110">Properties</span></span>

|  <span data-ttu-id="0c96f-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0c96f-111">Property</span></span>  |  <span data-ttu-id="0c96f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c96f-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="0c96f-113">Nome</span><span class="sxs-lookup"><span data-stu-id="0c96f-113">Name</span></span>| <span data-ttu-id="0c96f-114">Especifica o nome da origem do pacote para ser registado ou não registados no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="0c96f-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="0c96f-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="0c96f-115">ProviderName</span></span>| <span data-ttu-id="0c96f-116">Especifica o nome do fornecedor OneGet através do qual pode interoperabilidade com a origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="0c96f-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="0c96f-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="0c96f-117">SourceLocation</span></span>| <span data-ttu-id="0c96f-118">Especifica o URI da origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="0c96f-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="0c96f-119">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="0c96f-119">Ensure</span></span>| <span data-ttu-id="0c96f-120">Determina se a origem do pacote está a ser registado ou não registados.</span><span class="sxs-lookup"><span data-stu-id="0c96f-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="0c96f-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="0c96f-121">InstallationPolicy</span></span>| <span data-ttu-id="0c96f-122">Utilizada pelos fornecedores, tais como o fornecedor do Nuget incorporada.</span><span class="sxs-lookup"><span data-stu-id="0c96f-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="0c96f-123">Determina se confiar origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="0c96f-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="0c96f-124">Um dos: "Não fidedignas", "Fidedigna".</span><span class="sxs-lookup"><span data-stu-id="0c96f-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="0c96f-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="0c96f-125">SourceCredential</span></span>| <span data-ttu-id="0c96f-126">Fornece acesso ao pacote de uma origem remota.</span><span class="sxs-lookup"><span data-stu-id="0c96f-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="0c96f-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c96f-127">Example</span></span>

<span data-ttu-id="0c96f-128">Neste exemplo regista o http://nuget.org origem do pacote com o **PackageManagementSource** recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="0c96f-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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