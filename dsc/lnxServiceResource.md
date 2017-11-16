---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: DSC de Linux nxService recursos
ms.openlocfilehash: be9f1f090eacc38bcdb77e53020d559bab72c156
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="f676c-103">DSC de Linux nxService recursos</span><span class="sxs-lookup"><span data-stu-id="f676c-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="f676c-104">O **nxService** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir serviços num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="f676c-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f676c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f676c-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="f676c-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f676c-106">Properties</span></span>
|  <span data-ttu-id="f676c-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f676c-107">Property</span></span> |  <span data-ttu-id="f676c-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="f676c-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="f676c-109">Nome</span><span class="sxs-lookup"><span data-stu-id="f676c-109">Name</span></span>| <span data-ttu-id="f676c-110">O nome do serviço daemon para configurar.</span><span class="sxs-lookup"><span data-stu-id="f676c-110">The name of the service/daemon to configure.</span></span>| 
| <span data-ttu-id="f676c-111">Controlador</span><span class="sxs-lookup"><span data-stu-id="f676c-111">Controller</span></span>| <span data-ttu-id="f676c-112">O tipo de controlador de serviço para utilizar quando configurar o serviço.</span><span class="sxs-lookup"><span data-stu-id="f676c-112">The type of service controller to use when configuring the service.</span></span>| 
| <span data-ttu-id="f676c-113">Ativado</span><span class="sxs-lookup"><span data-stu-id="f676c-113">Enabled</span></span>| <span data-ttu-id="f676c-114">Indica se o serviço for iniciado no arranque.</span><span class="sxs-lookup"><span data-stu-id="f676c-114">Indicates whether the service starts on boot.</span></span>| 
| <span data-ttu-id="f676c-115">Estado</span><span class="sxs-lookup"><span data-stu-id="f676c-115">State</span></span>| <span data-ttu-id="f676c-116">Indica se o serviço está em execução.</span><span class="sxs-lookup"><span data-stu-id="f676c-116">Indicates whether the service is running.</span></span> <span data-ttu-id="f676c-117">Defina esta propriedade para "Stopped" para se certificar de que o serviço não está em execução.</span><span class="sxs-lookup"><span data-stu-id="f676c-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="f676c-118">Defina-o para "Em execução" para se certificar de que o serviço não está em execução.</span><span class="sxs-lookup"><span data-stu-id="f676c-118">Set it to "Running" to ensure that the service is not running.</span></span>| 
| <span data-ttu-id="f676c-119">dependsOn</span><span class="sxs-lookup"><span data-stu-id="f676c-119">DependsOn</span></span> | <span data-ttu-id="f676c-120">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="f676c-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f676c-121">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f676c-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 


## <a name="additional-information"></a><span data-ttu-id="f676c-122">Informações Adicionais</span><span class="sxs-lookup"><span data-stu-id="f676c-122">Additional Information</span></span>

<span data-ttu-id="f676c-123">O **nxService** recursos não irão criar uma definição de serviço ou script para o serviço se não existir.</span><span class="sxs-lookup"><span data-stu-id="f676c-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="f676c-124">Pode utilizar a configuração de estado pretendido do PowerShell **nxFile** recursos de recursos para gerir a existência de ou o conteúdo do ficheiro de definição de serviço ou script.</span><span class="sxs-lookup"><span data-stu-id="f676c-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="f676c-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f676c-125">Example</span></span>

<span data-ttu-id="f676c-126">O exemplo seguinte mostra a configuração do serviço "httpd" (para Apache HTTP Server), registada com o **SystemD** controlador do serviço.</span><span class="sxs-lookup"><span data-stu-id="f676c-126">The following example shows configuration of the “httpd” service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```

