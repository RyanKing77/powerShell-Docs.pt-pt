---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos do DSC ServiceSet
ms.openlocfilehash: a7516120f0c4bc1c91031adc8aabf6a59b845246
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="10fc3-103">Recursos do DSC ServiceSet</span><span class="sxs-lookup"><span data-stu-id="10fc3-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="10fc3-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="10fc3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="10fc3-105">O **ServiceSet** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir serviços no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="10fc3-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="10fc3-106">Este recurso é um [recursos composto](authoringResourceComposite.md) que chama o [Service recursos](serviceResource.md) para cada serviço especificado no `Name` propriedade.</span><span class="sxs-lookup"><span data-stu-id="10fc3-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="10fc3-107">Utilize este recurso quando pretender configurar um número de serviços para o estado do mesmo.</span><span class="sxs-lookup"><span data-stu-id="10fc3-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="10fc3-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10fc3-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="10fc3-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="10fc3-109">Properties</span></span>

|  <span data-ttu-id="10fc3-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="10fc3-110">Property</span></span>  |  <span data-ttu-id="10fc3-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="10fc3-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="10fc3-112">Nome</span><span class="sxs-lookup"><span data-stu-id="10fc3-112">Name</span></span>| <span data-ttu-id="10fc3-113">Indica os nomes de serviço.</span><span class="sxs-lookup"><span data-stu-id="10fc3-113">Indicates the service names.</span></span> <span data-ttu-id="10fc3-114">Tenha em atenção que, por vezes, isto é diferente dos nomes a apresentar.</span><span class="sxs-lookup"><span data-stu-id="10fc3-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="10fc3-115">Pode obter uma lista de serviços e o respetivo estado atual com o [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="10fc3-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="10fc3-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="10fc3-116">StartupType</span></span>| <span data-ttu-id="10fc3-117">Indica o tipo de arranque para o serviço.</span><span class="sxs-lookup"><span data-stu-id="10fc3-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="10fc3-118">Os valores que são permitidos para esta propriedade são: **automática**, **desativado**, e **Manual**</span><span class="sxs-lookup"><span data-stu-id="10fc3-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="10fc3-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="10fc3-119">BuiltInAccount</span></span>| <span data-ttu-id="10fc3-120">Indica a conta de início de sessão a utilizar para os serviços.</span><span class="sxs-lookup"><span data-stu-id="10fc3-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="10fc3-121">Os valores que são permitidos para esta propriedade são: **LocalService**, **LocalSystem**, e **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="10fc3-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="10fc3-122">Estado</span><span class="sxs-lookup"><span data-stu-id="10fc3-122">State</span></span>| <span data-ttu-id="10fc3-123">Indica o estado pretender certificar-se para os serviços: **parado** ou **executar**.</span><span class="sxs-lookup"><span data-stu-id="10fc3-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="10fc3-124">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="10fc3-124">Ensure</span></span>| <span data-ttu-id="10fc3-125">Indica se os serviços de existirem no sistema.</span><span class="sxs-lookup"><span data-stu-id="10fc3-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="10fc3-126">Defina esta propriedade como **ausente** para se certificar de que os serviços não existe.</span><span class="sxs-lookup"><span data-stu-id="10fc3-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="10fc3-127">Defini-la como **presente** (o valor predefinido) assegura que os serviços de destino existem.</span><span class="sxs-lookup"><span data-stu-id="10fc3-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="10fc3-128">credencial</span><span class="sxs-lookup"><span data-stu-id="10fc3-128">Credential</span></span>| <span data-ttu-id="10fc3-129">Indica as credenciais para a conta que o recurso de serviço irá ser executado.</span><span class="sxs-lookup"><span data-stu-id="10fc3-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="10fc3-130">Esta propriedade e o **BuiltinAccount** propriedade não pode ser utilizada em conjunto.</span><span class="sxs-lookup"><span data-stu-id="10fc3-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="10fc3-131">dependsOn</span><span class="sxs-lookup"><span data-stu-id="10fc3-131">DependsOn</span></span>| <span data-ttu-id="10fc3-132">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="10fc3-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="10fc3-133">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é *ResourceName* e o respetivo tipo é *ResourceType*, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="10fc3-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="10fc3-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10fc3-134">Example</span></span>

<span data-ttu-id="10fc3-135">A seguinte configuração de inicia os serviços de "Windows áudio" e "Serviços de ambiente de trabalho remoto".</span><span class="sxs-lookup"><span data-stu-id="10fc3-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```