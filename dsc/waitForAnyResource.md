---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WaitForAny
ms.openlocfilehash: 795c005c67c196ef9afb08af790fe2a1695392ec
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="3a8b5-103">Recursos do DSC WaitForAny</span><span class="sxs-lookup"><span data-stu-id="3a8b5-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="3a8b5-104">Aplica-se a: Windows PowerShell 5.1 e posterior</span><span class="sxs-lookup"><span data-stu-id="3a8b5-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="3a8b5-105">O **WaitForSome** recurso de configuração de estado pretendido (DSC) pode ser utilizado dentro de um bloco de nó num [configuração DSC](configurations.md) para especificar dependências em configurações nos outros nós.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="3a8b5-106">Este recurso é bem sucedida se se o recurso especificado pelo **ResourceName** se encontra no estado pretendido em quaisquer nós de destino definido na propriedade o **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="3a8b5-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a8b5-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="3a8b5-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3a8b5-108">Properties</span></span>

|  <span data-ttu-id="3a8b5-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="3a8b5-109">Property</span></span>  |  <span data-ttu-id="3a8b5-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a8b5-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="3a8b5-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="3a8b5-111">ResourceName</span></span>| <span data-ttu-id="3a8b5-112">O nome de recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="3a8b5-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="3a8b5-113">NodeName</span></span>| <span data-ttu-id="3a8b5-114">Os nós de destino do recurso dependem.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="3a8b5-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="3a8b5-115">RetryIntervalSec</span></span>| <span data-ttu-id="3a8b5-116">O número de segundos antes de repetir a operação.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-116">The number of seconds before retrying.</span></span> <span data-ttu-id="3a8b5-117">Mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="3a8b5-118">RetryCount</span><span class="sxs-lookup"><span data-stu-id="3a8b5-118">RetryCount</span></span>| <span data-ttu-id="3a8b5-119">O número máximo de vezes para tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="3a8b5-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="3a8b5-120">ThrottleLimit</span></span>| <span data-ttu-id="3a8b5-121">Número de máquinas para ligar em simultâneo.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="3a8b5-122">Predefinição é novo-cimsession predefinido.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="3a8b5-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="3a8b5-123">DependsOn</span></span> | <span data-ttu-id="3a8b5-124">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3a8b5-125">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="3a8b5-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a8b5-126">Example</span></span>

<span data-ttu-id="3a8b5-127">Para obter um exemplo de como utilizar este recurso, consulte [especificar dependências entre nós](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="3a8b5-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

