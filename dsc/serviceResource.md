---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Recurso de serviço de DSC"
ms.openlocfilehash: 611729e5d971ebaf15ac947454cffadc6797927b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-service-resource"></a><span data-ttu-id="0d1d3-103">Recurso de serviço de DSC</span><span class="sxs-lookup"><span data-stu-id="0d1d3-103">DSC Service Resource</span></span>

> <span data-ttu-id="0d1d3-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0d1d3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="0d1d3-105">O **serviço** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir serviços no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d1d3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d1d3-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="0d1d3-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0d1d3-107">Properties</span></span>

|  <span data-ttu-id="0d1d3-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0d1d3-108">Property</span></span>  |  <span data-ttu-id="0d1d3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d1d3-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="0d1d3-110">Nome</span><span class="sxs-lookup"><span data-stu-id="0d1d3-110">Name</span></span>| <span data-ttu-id="0d1d3-111">Indica o nome do serviço.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-111">Indicates the service name.</span></span> <span data-ttu-id="0d1d3-112">Tenha em atenção que, por vezes, isto é diferente do nome de apresentação.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="0d1d3-113">Pode obter uma lista de serviços e o respetivo estado atual com o cmdlet Get-Service.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>| 
| <span data-ttu-id="0d1d3-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="0d1d3-114">BuiltInAccount</span></span>| <span data-ttu-id="0d1d3-115">Indica a conta de início de sessão a utilizar para o serviço.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="0d1d3-116">Os valores que são permitidos para esta propriedade são: **LocalService**, **LocalSystem**, e **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>| 
| <span data-ttu-id="0d1d3-117">credencial</span><span class="sxs-lookup"><span data-stu-id="0d1d3-117">Credential</span></span>| <span data-ttu-id="0d1d3-118">Indica as credenciais para a conta que o serviço irá ser executado.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="0d1d3-119">Esta propriedade e o __BuiltinAccount__ propriedade não pode ser utilizada em conjunto.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>| 
| <span data-ttu-id="0d1d3-120">dependsOn</span><span class="sxs-lookup"><span data-stu-id="0d1d3-120">DependsOn</span></span>| <span data-ttu-id="0d1d3-121">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0d1d3-122">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="0d1d3-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="0d1d3-123">StartupType</span></span>| <span data-ttu-id="0d1d3-124">Indica o tipo de arranque para o serviço.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="0d1d3-125">Os valores que são permitidos para esta propriedade são: **automática**, **desativado**, e **Manual**</span><span class="sxs-lookup"><span data-stu-id="0d1d3-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>| 
| <span data-ttu-id="0d1d3-126">Estado</span><span class="sxs-lookup"><span data-stu-id="0d1d3-126">State</span></span>| <span data-ttu-id="0d1d3-127">Indica o estado que pretender certificar-se para o serviço.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-127">Indicates the state you want to ensure for the service.</span></span>| 
| <span data-ttu-id="0d1d3-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d1d3-128">Description</span></span> | <span data-ttu-id="0d1d3-129">Indica a descrição do serviço de destino.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-129">Indicates the description of the target service.</span></span>| 
| <span data-ttu-id="0d1d3-130">NomeaApresentar</span><span class="sxs-lookup"><span data-stu-id="0d1d3-130">DisplayName</span></span> | <span data-ttu-id="0d1d3-131">Indica o nome a apresentar do serviço de destino.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-131">Indicates the display name of the target service.</span></span>| 
| <span data-ttu-id="0d1d3-132">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="0d1d3-132">Ensure</span></span> | <span data-ttu-id="0d1d3-133">Indica se o serviço de destino existe no sistema.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="0d1d3-134">Defina esta propriedade como **ausente** para se certificar de que o serviço de destino não existe.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="0d1d3-135">Defini-la como **presente** (o valor predefinido) assegura que o serviço de destino existe.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="0d1d3-136">Caminho</span><span class="sxs-lookup"><span data-stu-id="0d1d3-136">Path</span></span> | <span data-ttu-id="0d1d3-137">Indica o caminho para o ficheiro binário para um novo serviço.</span><span class="sxs-lookup"><span data-stu-id="0d1d3-137">Indicates the path to the binary file for a new service.</span></span>| 

## <a name="example"></a><span data-ttu-id="0d1d3-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d1d3-138">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

