---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso ServiceSet de DSC
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076841"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="0bac7-103">Recurso ServiceSet de DSC</span><span class="sxs-lookup"><span data-stu-id="0bac7-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="0bac7-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0bac7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0bac7-105">O **ServiceSet** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir serviços no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="0bac7-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="0bac7-106">Este recurso é um [recursos compostos](../../../resources/authoringResourceComposite.md) que chama o [recursos de serviço](serviceResource.md) para cada serviço especificado no `Name` propriedade.</span><span class="sxs-lookup"><span data-stu-id="0bac7-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="0bac7-107">Utilize este recurso quando pretender configurar um número de serviços para o mesmo Estado.</span><span class="sxs-lookup"><span data-stu-id="0bac7-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="0bac7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bac7-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="0bac7-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0bac7-109">Properties</span></span>

|  <span data-ttu-id="0bac7-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0bac7-110">Property</span></span>  |  <span data-ttu-id="0bac7-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bac7-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="0bac7-112">Nome</span><span class="sxs-lookup"><span data-stu-id="0bac7-112">Name</span></span>| <span data-ttu-id="0bac7-113">Indica os nomes de serviço.</span><span class="sxs-lookup"><span data-stu-id="0bac7-113">Indicates the service names.</span></span> <span data-ttu-id="0bac7-114">Tenha em atenção que, às vezes, isso é diferente dos nomes a apresentar.</span><span class="sxs-lookup"><span data-stu-id="0bac7-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="0bac7-115">Pode obter uma lista de serviços e o respetivo estado atual com o [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0bac7-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="0bac7-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="0bac7-116">StartupType</span></span>| <span data-ttu-id="0bac7-117">Indica o tipo de arranque para o serviço.</span><span class="sxs-lookup"><span data-stu-id="0bac7-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="0bac7-118">Os valores permitidos para esta propriedade são: **Automática**, **desativada**, e **Manual**</span><span class="sxs-lookup"><span data-stu-id="0bac7-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="0bac7-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="0bac7-119">BuiltInAccount</span></span>| <span data-ttu-id="0bac7-120">Indica a conta de início de sessão para utilizar para os serviços.</span><span class="sxs-lookup"><span data-stu-id="0bac7-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="0bac7-121">Os valores permitidos para esta propriedade são: **LocalService**, **LocalSystem**, e **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="0bac7-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="0bac7-122">Estado</span><span class="sxs-lookup"><span data-stu-id="0bac7-122">State</span></span>| <span data-ttu-id="0bac7-123">Indica o estado a que se pretender certificar-se para os serviços: **Parado** ou **em execução**.</span><span class="sxs-lookup"><span data-stu-id="0bac7-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="0bac7-124">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="0bac7-124">Ensure</span></span>| <span data-ttu-id="0bac7-125">Indica se os serviços existem no sistema.</span><span class="sxs-lookup"><span data-stu-id="0bac7-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="0bac7-126">Defina esta propriedade como **ausente** para garantir que os serviços não existem.</span><span class="sxs-lookup"><span data-stu-id="0bac7-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="0bac7-127">Defini-la como **presente** (o valor predefinido) garante que os serviços de destino existem.</span><span class="sxs-lookup"><span data-stu-id="0bac7-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="0bac7-128">Credencial</span><span class="sxs-lookup"><span data-stu-id="0bac7-128">Credential</span></span>| <span data-ttu-id="0bac7-129">Indica as credenciais para a conta que o recurso de serviço será executado no.</span><span class="sxs-lookup"><span data-stu-id="0bac7-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="0bac7-130">Esta propriedade e o **BuiltinAccount** propriedade não pode ser utilizada em conjunto.</span><span class="sxs-lookup"><span data-stu-id="0bac7-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="0bac7-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0bac7-131">DependsOn</span></span>| <span data-ttu-id="0bac7-132">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="0bac7-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0bac7-133">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será *ResourceName* e seu tipo é *ResourceType*, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0bac7-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="0bac7-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bac7-134">Example</span></span>

<span data-ttu-id="0bac7-135">A seguinte configuração inicia os serviços "Áudio do Windows" e "Serviços de ambiente de trabalho remoto".</span><span class="sxs-lookup"><span data-stu-id="0bac7-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

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
