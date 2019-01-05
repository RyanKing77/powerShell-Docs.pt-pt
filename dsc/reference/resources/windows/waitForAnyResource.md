---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recursos do DSC WaitForAny
ms.openlocfilehash: 39e90f0df3459b8891ed46e02ae82c45a285e7f5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048437"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="a26a5-103">Recursos do DSC WaitForAny</span><span class="sxs-lookup"><span data-stu-id="a26a5-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="a26a5-104">Aplica-se a: Windows PowerShell 5.1 e versões posterior</span><span class="sxs-lookup"><span data-stu-id="a26a5-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="a26a5-105">O **WaitForSome** recursos do Desired State Configuration (DSC) podem ser utilizado dentro de um bloco de nó num [configuração de DSC](../../../configurations/configurations.md) para especificar dependências em configurações nos outros nós.</span><span class="sxs-lookup"><span data-stu-id="a26a5-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="a26a5-106">Este recurso é bem-sucedida se o recurso especificado pela **ResourceName** propriedade está no Estado desejado em quaisquer nós de destino definido no **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="a26a5-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="a26a5-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a26a5-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="a26a5-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a26a5-108">Properties</span></span>

|  <span data-ttu-id="a26a5-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a26a5-109">Property</span></span>  |  <span data-ttu-id="a26a5-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a26a5-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="a26a5-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="a26a5-111">ResourceName</span></span>| <span data-ttu-id="a26a5-112">O nome de recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="a26a5-112">The resource name to depend on.</span></span> <span data-ttu-id="a26a5-113">Se este recurso pertence a uma configuração diferente, formatar o nome como "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="a26a5-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="a26a5-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="a26a5-114">NodeName</span></span>| <span data-ttu-id="a26a5-115">Os nós de destino do recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="a26a5-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="a26a5-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="a26a5-116">RetryIntervalSec</span></span>| <span data-ttu-id="a26a5-117">O número de segundos antes de tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="a26a5-117">The number of seconds before retrying.</span></span> <span data-ttu-id="a26a5-118">Mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="a26a5-118">Minimum is 1.</span></span>|
| <span data-ttu-id="a26a5-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="a26a5-119">RetryCount</span></span>| <span data-ttu-id="a26a5-120">O número máximo de vezes a repetir.</span><span class="sxs-lookup"><span data-stu-id="a26a5-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="a26a5-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="a26a5-121">ThrottleLimit</span></span>| <span data-ttu-id="a26a5-122">Número de máquinas para se conectar simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="a26a5-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="a26a5-123">A predefinição é padrão do novo-cimsession.</span><span class="sxs-lookup"><span data-stu-id="a26a5-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="a26a5-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a26a5-124">DependsOn</span></span> | <span data-ttu-id="a26a5-125">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="a26a5-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a26a5-126">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a26a5-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="a26a5-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a26a5-127">Example</span></span>

<span data-ttu-id="a26a5-128">Para obter um exemplo de como usar este recurso, consulte [especificar dependências entre nós](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="a26a5-128">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
