---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recursos do DSC WaitForAll
ms.openlocfilehash: c1125b7c5b68b9b520ed052800b6a2abf4e53b85
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726874"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="3e7d0-103">Recursos do DSC WaitForAll</span><span class="sxs-lookup"><span data-stu-id="3e7d0-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="3e7d0-104">Aplica-se a: Windows PowerShell 5.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="3e7d0-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="3e7d0-105">O **WaitForAll** recursos do Desired State Configuration (DSC) podem ser utilizado dentro de um bloco de nó num [configuração de DSC](../../../configurations/configurations.md) para especificar dependências em configurações nos outros nós.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="3e7d0-106">Este recurso é bem-sucedida se o recurso especificado pela **ResourceName** propriedade está no Estado desejado em todos os nós de destino definido no **NodeName** propriedade.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="3e7d0-107">**WaitForAll** recursos utilizam a gestão remota do Windows para verificar o estado de outros nós.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-107">**WaitForAll** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="3e7d0-108">Para obter mais informações sobre os requisitos de segurança e de porta para o WinRM, consulte [considerações de segurança de comunicação remota do PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="3e7d0-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="3e7d0-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e7d0-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="3e7d0-110">properties</span><span class="sxs-lookup"><span data-stu-id="3e7d0-110">Properties</span></span>

|  <span data-ttu-id="3e7d0-111">Propriedade</span><span class="sxs-lookup"><span data-stu-id="3e7d0-111">Property</span></span>  |  <span data-ttu-id="3e7d0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e7d0-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="3e7d0-113">ResourceName</span><span class="sxs-lookup"><span data-stu-id="3e7d0-113">ResourceName</span></span>| <span data-ttu-id="3e7d0-114">O nome de recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-114">The resource name to depend on.</span></span> <span data-ttu-id="3e7d0-115">Se este recurso pertence a uma configuração diferente, formatar o nome como "[__ResourceType__]__ResourceName__:: [__ConfigurationName__]:: [ __ConfigurationName__] "</span><span class="sxs-lookup"><span data-stu-id="3e7d0-115">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="3e7d0-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="3e7d0-116">NodeName</span></span>| <span data-ttu-id="3e7d0-117">Os nós de destino do recurso a dependem.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-117">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="3e7d0-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="3e7d0-118">RetryIntervalSec</span></span>| <span data-ttu-id="3e7d0-119">O número de segundos antes de tentar novamente.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-119">The number of seconds before retrying.</span></span> <span data-ttu-id="3e7d0-120">Mínimo é 1.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-120">Minimum is 1.</span></span>|
| <span data-ttu-id="3e7d0-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="3e7d0-121">RetryCount</span></span>| <span data-ttu-id="3e7d0-122">O número máximo de vezes a repetir.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="3e7d0-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="3e7d0-123">ThrottleLimit</span></span>| <span data-ttu-id="3e7d0-124">Número de máquinas para se conectar simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="3e7d0-125">A predefinição é padrão do novo-cimsession.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="3e7d0-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3e7d0-126">DependsOn</span></span> | <span data-ttu-id="3e7d0-127">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3e7d0-128">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3e7d0-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="3e7d0-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e7d0-129">Example</span></span>

<span data-ttu-id="3e7d0-130">Para obter um exemplo de como usar este recurso, consulte [especificar dependências entre nós](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="3e7d0-130">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
