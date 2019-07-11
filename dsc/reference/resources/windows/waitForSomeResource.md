---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recursos do DSC WaitForSome
ms.openlocfilehash: 2260f37002171154a6f2c3996b2af1bd9120039d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726777"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="7f052-103">Recursos do DSC WaitForSome</span><span class="sxs-lookup"><span data-stu-id="7f052-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="7f052-104">Aplica-se a: Windows PowerShell 5.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="7f052-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="7f052-105">O **WaitForSome** recursos do Desired State Configuration (DSC) podem ser utilizado dentro de um bloco de nó num [configuração de DSC](../../../configurations/configurations.md) para especificar dependências em configurações nos outros nós.</span><span class="sxs-lookup"><span data-stu-id="7f052-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="7f052-106">Este recurso é bem-sucedida se o recurso especificado pela **ResourceName** propriedade está no Estado desejado num número mínimo de nós (especificado pelo **NodeCount**) definidos pelo **NodeName**  propriedade.</span><span class="sxs-lookup"><span data-stu-id="7f052-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="7f052-107">**WaitForSome** recursos utilizam a gestão remota do Windows para verificar o estado de outros nós.</span><span class="sxs-lookup"><span data-stu-id="7f052-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="7f052-108">Para obter mais informações sobre os requisitos de segurança e de porta para o WinRM, consulte [considerações de segurança de comunicação remota do PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="7f052-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="7f052-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f052-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="7f052-110">properties</span><span class="sxs-lookup"><span data-stu-id="7f052-110">Properties</span></span>

|  <span data-ttu-id="7f052-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="7f052-111">Property</span></span>  |  <span data-ttu-id="7f052-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f052-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="7f052-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="7f052-113">NodeCount</span></span>| <span data-ttu-id="7f052-114">O número mínimo de nós que tem de estar no estado pretendido para este recurso tenha êxito.</span><span class="sxs-lookup"><span data-stu-id="7f052-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="7f052-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="7f052-115">NodeName</span></span>| <span data-ttu-id="7f052-116">Os nós de destino do recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="7f052-116">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="7f052-117">ResourceName</span><span class="sxs-lookup"><span data-stu-id="7f052-117">ResourceName</span></span>| <span data-ttu-id="7f052-118">O nome de recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="7f052-118">The resource name to depend on.</span></span> <span data-ttu-id="7f052-119">Se este recurso pertence a uma configuração diferente, formatar o nome como "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="7f052-119">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="7f052-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="7f052-120">RetryIntervalSec</span></span>| <span data-ttu-id="7f052-121">O número de segundos antes de tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="7f052-121">The number of seconds before retrying.</span></span> <span data-ttu-id="7f052-122">Mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="7f052-122">Minimum is 1.</span></span>|
| <span data-ttu-id="7f052-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="7f052-123">RetryCount</span></span>| <span data-ttu-id="7f052-124">O número máximo de vezes a repetir.</span><span class="sxs-lookup"><span data-stu-id="7f052-124">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="7f052-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="7f052-125">ThrottleLimit</span></span>| <span data-ttu-id="7f052-126">Número de máquinas para se conectar simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="7f052-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="7f052-127">A predefinição é padrão do novo-cimsession.</span><span class="sxs-lookup"><span data-stu-id="7f052-127">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="7f052-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7f052-128">DependsOn</span></span> | <span data-ttu-id="7f052-129">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="7f052-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7f052-130">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7f052-130">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="7f052-131">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7f052-131">PsDscRunAsCredential</span></span> | <span data-ttu-id="7f052-132">Consulte [com DSC com as credenciais de utilizador](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="7f052-132">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="7f052-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f052-133">Example</span></span>

<span data-ttu-id="7f052-134">Para obter um exemplo de como usar este recurso, consulte [especificar dependências entre nós](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="7f052-134">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
