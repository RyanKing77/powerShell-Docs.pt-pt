---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recursos do DSC WaitForSome
ms.openlocfilehash: 906375a8fcf9b87d4b7487e63e6fae3f05b86d0d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048380"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="b8fa8-103">Recursos do DSC WaitForSome</span><span class="sxs-lookup"><span data-stu-id="b8fa8-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="b8fa8-104">Aplica-se a: Windows PowerShell 5.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="b8fa8-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="b8fa8-105">O **WaitForAny** recursos do Desired State Configuration (DSC) podem ser utilizado dentro de um bloco de nó num [configuração de DSC](../../../configurations/configurations.md) para especificar dependências em configurações nos outros nós.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="b8fa8-106">Este recurso é bem-sucedida se o recurso especificado pela **ResourceName** propriedade está no Estado desejado num número mínimo de nós (especificado pelo **NodeCount**) definidos pelo **NodeName**  propriedade.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="b8fa8-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8fa8-107">Syntax</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a><span data-ttu-id="b8fa8-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b8fa8-108">Properties</span></span>

|  <span data-ttu-id="b8fa8-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b8fa8-109">Property</span></span>  |  <span data-ttu-id="b8fa8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8fa8-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="b8fa8-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="b8fa8-111">NodeCount</span></span>| <span data-ttu-id="b8fa8-112">O número mínimo de nós que tem de estar no estado pretendido para este recurso tenha êxito.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="b8fa8-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="b8fa8-113">NodeName</span></span>| <span data-ttu-id="b8fa8-114">Os nós de destino do recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-114">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="b8fa8-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="b8fa8-115">ResourceName</span></span>| <span data-ttu-id="b8fa8-116">O nome de recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-116">The resource name to depend on.</span></span> <span data-ttu-id="b8fa8-117">Se este recurso pertence a uma configuração diferente, formatar o nome como "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="b8fa8-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="b8fa8-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="b8fa8-118">RetryIntervalSec</span></span>| <span data-ttu-id="b8fa8-119">O número de segundos antes de tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-119">The number of seconds before retrying.</span></span> <span data-ttu-id="b8fa8-120">Mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-120">Minimum is 1.</span></span>|
| <span data-ttu-id="b8fa8-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="b8fa8-121">RetryCount</span></span>| <span data-ttu-id="b8fa8-122">O número máximo de vezes a repetir.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="b8fa8-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b8fa8-123">ThrottleLimit</span></span>| <span data-ttu-id="b8fa8-124">Número de máquinas para se conectar simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="b8fa8-125">A predefinição é padrão do novo-cimsession.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="b8fa8-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b8fa8-126">DependsOn</span></span> | <span data-ttu-id="b8fa8-127">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b8fa8-128">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b8fa8-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="b8fa8-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b8fa8-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="b8fa8-130">Consulte [com DSC com as credenciais de utilizador](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="b8fa8-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="b8fa8-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8fa8-131">Example</span></span>

<span data-ttu-id="b8fa8-132">Para obter um exemplo de como usar este recurso, consulte [especificar dependências entre nós](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="b8fa8-132">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>