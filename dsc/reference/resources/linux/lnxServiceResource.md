---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxService recursos
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077698"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="b405d-103">DSC para Linux nxService recursos</span><span class="sxs-lookup"><span data-stu-id="b405d-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="b405d-104">O **nxService** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir os serviços num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="b405d-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b405d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b405d-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="b405d-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b405d-106">Properties</span></span>

| <span data-ttu-id="b405d-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b405d-107">Property</span></span> | <span data-ttu-id="b405d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b405d-108">Description</span></span> |
|---|---|
| <span data-ttu-id="b405d-109">Nome</span><span class="sxs-lookup"><span data-stu-id="b405d-109">Name</span></span>| <span data-ttu-id="b405d-110">O nome do serviço/daemon para configurar.</span><span class="sxs-lookup"><span data-stu-id="b405d-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="b405d-111">controlador</span><span class="sxs-lookup"><span data-stu-id="b405d-111">Controller</span></span>| <span data-ttu-id="b405d-112">O tipo de controlador de serviço a utilizar quando configurar o serviço.</span><span class="sxs-lookup"><span data-stu-id="b405d-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="b405d-113">Ativado</span><span class="sxs-lookup"><span data-stu-id="b405d-113">Enabled</span></span>| <span data-ttu-id="b405d-114">Indica se o serviço é iniciado no arranque.</span><span class="sxs-lookup"><span data-stu-id="b405d-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="b405d-115">Estado</span><span class="sxs-lookup"><span data-stu-id="b405d-115">State</span></span>| <span data-ttu-id="b405d-116">Indica se o serviço está em execução.</span><span class="sxs-lookup"><span data-stu-id="b405d-116">Indicates whether the service is running.</span></span> <span data-ttu-id="b405d-117">Defina esta propriedade a "Stopped" para se certificar de que o serviço não está em execução.</span><span class="sxs-lookup"><span data-stu-id="b405d-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="b405d-118">Defini-lo como "Em execução" para se certificar de que o serviço não está em execução.</span><span class="sxs-lookup"><span data-stu-id="b405d-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="b405d-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b405d-119">DependsOn</span></span> | <span data-ttu-id="b405d-120">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="b405d-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b405d-121">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b405d-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="b405d-122">Informações Adicionais</span><span class="sxs-lookup"><span data-stu-id="b405d-122">Additional Information</span></span>

<span data-ttu-id="b405d-123">O **nxService** recursos não criará uma definição de serviço ou um script para o serviço se não existir.</span><span class="sxs-lookup"><span data-stu-id="b405d-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="b405d-124">Pode usar o do PowerShell Desired State Configuration **nxFile** recursos de recursos para gerir a existência ou o conteúdo do ficheiro de definição de serviço ou script.</span><span class="sxs-lookup"><span data-stu-id="b405d-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="b405d-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b405d-125">Example</span></span>

<span data-ttu-id="b405d-126">O exemplo seguinte mostra a configuração do serviço "httpd" (para o Apache HTTP Server), registrada com o **SystemD** controlador de serviço.</span><span class="sxs-lookup"><span data-stu-id="b405d-126">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```