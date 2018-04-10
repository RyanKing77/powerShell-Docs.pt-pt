---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC WaitForAny
ms.openlocfilehash: 3d73c16397d9a18805184e6a5bb8561483144898
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="7941b-103">Recursos do DSC WaitForAny</span><span class="sxs-lookup"><span data-stu-id="7941b-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="7941b-104">Aplica-se a: Windows PowerShell 5.1 e posterior</span><span class="sxs-lookup"><span data-stu-id="7941b-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="7941b-105">O **WaitForSome** recurso de configuração de estado pretendido (DSC) pode ser utilizado dentro de um bloco de nó num [configuração DSC](configurations.md) para especificar dependências em configurações nos outros nós.</span><span class="sxs-lookup"><span data-stu-id="7941b-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="7941b-106">Este recurso é bem sucedida se se o recurso especificado pelo **ResourceName** se encontra no estado pretendido em quaisquer nós de destino definido na propriedade o **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="7941b-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="7941b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7941b-107">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="7941b-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7941b-108">Properties</span></span>

|  <span data-ttu-id="7941b-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="7941b-109">Property</span></span>  |  <span data-ttu-id="7941b-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="7941b-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="7941b-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="7941b-111">ResourceName</span></span>| <span data-ttu-id="7941b-112">O nome de recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="7941b-112">The resource name to depend on.</span></span> <span data-ttu-id="7941b-113">Se este recurso pertence a uma configuração diferente, o nome de formato "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="7941b-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="7941b-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="7941b-114">NodeName</span></span>| <span data-ttu-id="7941b-115">Os nós de destino do recurso dependem.</span><span class="sxs-lookup"><span data-stu-id="7941b-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="7941b-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="7941b-116">RetryIntervalSec</span></span>| <span data-ttu-id="7941b-117">O número de segundos antes de repetir a operação.</span><span class="sxs-lookup"><span data-stu-id="7941b-117">The number of seconds before retrying.</span></span> <span data-ttu-id="7941b-118">Mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="7941b-118">Minimum is 1.</span></span>|
| <span data-ttu-id="7941b-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="7941b-119">RetryCount</span></span>| <span data-ttu-id="7941b-120">O número máximo de vezes para tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="7941b-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="7941b-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="7941b-121">ThrottleLimit</span></span>| <span data-ttu-id="7941b-122">Número de máquinas para ligar em simultâneo.</span><span class="sxs-lookup"><span data-stu-id="7941b-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="7941b-123">Predefinição é novo-cimsession predefinido.</span><span class="sxs-lookup"><span data-stu-id="7941b-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="7941b-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="7941b-124">DependsOn</span></span> | <span data-ttu-id="7941b-125">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="7941b-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7941b-126">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7941b-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="7941b-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7941b-127">Example</span></span>

<span data-ttu-id="7941b-128">Para obter um exemplo de como utilizar este recurso, consulte [especificar dependências entre nós](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="7941b-128">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>