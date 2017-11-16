---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WaitForAll
ms.openlocfilehash: dcc23ad4e6905bc277ad39348350d5425fc90ad7
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="e18c2-103">Recursos do DSC WaitForAll</span><span class="sxs-lookup"><span data-stu-id="e18c2-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="e18c2-104">Aplica-se a: Windows PowerShell 5.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="e18c2-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="e18c2-105">O **WaitForAll** recurso de configuração de estado pretendido (DSC) pode ser utilizado dentro de um bloco de nó num [configuração DSC](configurations.md) para especificar dependências em configurações nos outros nós.</span><span class="sxs-lookup"><span data-stu-id="e18c2-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="e18c2-106">Este recurso é bem sucedida se se o recurso especificado pelo **ResourceName** se encontra no estado pretendido em todos os nós de destino definido na propriedade o **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="e18c2-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="e18c2-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e18c2-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="e18c2-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e18c2-108">Properties</span></span>

|  <span data-ttu-id="e18c2-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e18c2-109">Property</span></span>  |  <span data-ttu-id="e18c2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="e18c2-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="e18c2-111">resourceName</span><span class="sxs-lookup"><span data-stu-id="e18c2-111">ResourceName</span></span>| <span data-ttu-id="e18c2-112">O nome de recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="e18c2-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="e18c2-113">nodeName</span><span class="sxs-lookup"><span data-stu-id="e18c2-113">NodeName</span></span>| <span data-ttu-id="e18c2-114">Os nós de destino do recurso dependem.</span><span class="sxs-lookup"><span data-stu-id="e18c2-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="e18c2-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="e18c2-115">RetryIntervalSec</span></span>| <span data-ttu-id="e18c2-116">O número de segundos antes de repetir a operação.</span><span class="sxs-lookup"><span data-stu-id="e18c2-116">The number of seconds before retrying.</span></span> <span data-ttu-id="e18c2-117">Mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="e18c2-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="e18c2-118">retryCount</span><span class="sxs-lookup"><span data-stu-id="e18c2-118">RetryCount</span></span>| <span data-ttu-id="e18c2-119">O número máximo de vezes para tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="e18c2-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="e18c2-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="e18c2-120">ThrottleLimit</span></span>| <span data-ttu-id="e18c2-121">Número de máquinas para ligar em simultâneo.</span><span class="sxs-lookup"><span data-stu-id="e18c2-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="e18c2-122">Predefinição é novo-cimsession predefinido.</span><span class="sxs-lookup"><span data-stu-id="e18c2-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="e18c2-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="e18c2-123">DependsOn</span></span> | <span data-ttu-id="e18c2-124">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="e18c2-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e18c2-125">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e18c2-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="e18c2-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e18c2-126">Example</span></span>

<span data-ttu-id="e18c2-127">Para obter um exemplo de como utilizar este recurso, consulte [especificar dependências entre nós](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="e18c2-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

