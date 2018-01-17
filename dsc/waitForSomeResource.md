---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WaitForSome
ms.openlocfilehash: cbe16c543f0eeb62dbe1fb439af2f9147f1bc210
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="361bf-103">Recursos do DSC WaitForSome</span><span class="sxs-lookup"><span data-stu-id="361bf-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="361bf-104">Aplica-se a: Windows PowerShell 5.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="361bf-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="361bf-105">O **WaitForAny** recurso de configuração de estado pretendido (DSC) pode ser utilizado dentro de um bloco de nó num [configuração DSC](configurations.md) para especificar dependências em configurações nos outros nós.</span><span class="sxs-lookup"><span data-stu-id="361bf-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="361bf-106">Este recurso é bem sucedida se o recurso especificado pelo **ResourceName** propriedade está no estado pretendido num número mínimo de nós (especificada por **NodeCount**) definidos pelo **NodeName**  propriedade.</span><span class="sxs-lookup"><span data-stu-id="361bf-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="361bf-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="361bf-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="361bf-108">Propriedades</span><span class="sxs-lookup"><span data-stu-id="361bf-108">Properties</span></span>

|  <span data-ttu-id="361bf-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="361bf-109">Property</span></span>  |  <span data-ttu-id="361bf-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="361bf-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="361bf-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="361bf-111">NodeCount</span></span>| <span data-ttu-id="361bf-112">O número mínimo de nós que têm de estar no estado pretendido para este recurso com êxito.</span><span class="sxs-lookup"><span data-stu-id="361bf-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="361bf-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="361bf-113">NodeName</span></span>| <span data-ttu-id="361bf-114">Os nós de destino do recurso dependem.</span><span class="sxs-lookup"><span data-stu-id="361bf-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="361bf-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="361bf-115">ResourceName</span></span>| <span data-ttu-id="361bf-116">O nome de recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="361bf-116">The resource name to depend on.</span></span>| 
| <span data-ttu-id="361bf-117">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="361bf-117">RetryIntervalSec</span></span>| <span data-ttu-id="361bf-118">O número de segundos antes de repetir a operação.</span><span class="sxs-lookup"><span data-stu-id="361bf-118">The number of seconds before retrying.</span></span> <span data-ttu-id="361bf-119">Mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="361bf-119">Minimum is 1.</span></span>| 
| <span data-ttu-id="361bf-120">RetryCount</span><span class="sxs-lookup"><span data-stu-id="361bf-120">RetryCount</span></span>| <span data-ttu-id="361bf-121">O número máximo de vezes para tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="361bf-121">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="361bf-122">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="361bf-122">ThrottleLimit</span></span>| <span data-ttu-id="361bf-123">Número de máquinas para ligar em simultâneo.</span><span class="sxs-lookup"><span data-stu-id="361bf-123">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="361bf-124">Predefinição é novo-cimsession predefinido.</span><span class="sxs-lookup"><span data-stu-id="361bf-124">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="361bf-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="361bf-125">DependsOn</span></span> | <span data-ttu-id="361bf-126">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="361bf-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="361bf-127">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="361bf-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="361bf-128">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="361bf-128">PsDscRunAsCredential</span></span> | <span data-ttu-id="361bf-129">Consulte [através de DSC com credenciais de utilizador](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="361bf-129">See [Using DSC with User Credentials](https://docs.microsoft.com/en-us/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="361bf-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="361bf-130">Example</span></span>

<span data-ttu-id="361bf-131">Para obter um exemplo de como utilizar este recurso, consulte [especificar dependências entre nós](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="361bf-131">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

