---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso de serviço de DSC
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048376"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="3e9da-103">Recurso de serviço de DSC</span><span class="sxs-lookup"><span data-stu-id="3e9da-103">DSC Service Resource</span></span>

> <span data-ttu-id="3e9da-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3e9da-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="3e9da-105">O **serviço** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir serviços no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="3e9da-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e9da-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e9da-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="3e9da-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3e9da-107">Properties</span></span>

|  <span data-ttu-id="3e9da-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="3e9da-108">Property</span></span>  |  <span data-ttu-id="3e9da-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e9da-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="3e9da-110">Nome</span><span class="sxs-lookup"><span data-stu-id="3e9da-110">Name</span></span>| <span data-ttu-id="3e9da-111">Indica o nome do serviço.</span><span class="sxs-lookup"><span data-stu-id="3e9da-111">Indicates the service name.</span></span> <span data-ttu-id="3e9da-112">Observe que, às vezes, isso é diferente do nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="3e9da-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="3e9da-113">Pode obter uma lista de serviços e o respetivo estado atual com o cmdlet Get-Service.</span><span class="sxs-lookup"><span data-stu-id="3e9da-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="3e9da-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="3e9da-114">BuiltInAccount</span></span>| <span data-ttu-id="3e9da-115">Indica a conta de início de sessão para utilizar para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3e9da-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="3e9da-116">Os valores permitidos para esta propriedade são: **LocalService**, **LocalSystem**, e **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="3e9da-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="3e9da-117">Credencial</span><span class="sxs-lookup"><span data-stu-id="3e9da-117">Credential</span></span>| <span data-ttu-id="3e9da-118">Indica as credenciais para a conta que o serviço será executado em.</span><span class="sxs-lookup"><span data-stu-id="3e9da-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="3e9da-119">Esta propriedade e o __BuiltinAccount__ propriedade não pode ser utilizada em conjunto.</span><span class="sxs-lookup"><span data-stu-id="3e9da-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="3e9da-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3e9da-120">DependsOn</span></span>| <span data-ttu-id="3e9da-121">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="3e9da-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3e9da-122">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3e9da-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="3e9da-123">Startuptype do</span><span class="sxs-lookup"><span data-stu-id="3e9da-123">StartupType</span></span>| <span data-ttu-id="3e9da-124">Indica o tipo de arranque para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3e9da-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="3e9da-125">Os valores permitidos para esta propriedade são: **Automática**, **desativada**, e **Manual**</span><span class="sxs-lookup"><span data-stu-id="3e9da-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="3e9da-126">Estado</span><span class="sxs-lookup"><span data-stu-id="3e9da-126">State</span></span>| <span data-ttu-id="3e9da-127">Indica o estado que pretender certificar-se para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3e9da-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="3e9da-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e9da-128">Description</span></span> | <span data-ttu-id="3e9da-129">Indica a descrição do serviço de destino.</span><span class="sxs-lookup"><span data-stu-id="3e9da-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="3e9da-130">NomeaApresentar</span><span class="sxs-lookup"><span data-stu-id="3e9da-130">DisplayName</span></span> | <span data-ttu-id="3e9da-131">Indica o nome a apresentar do serviço de destino.</span><span class="sxs-lookup"><span data-stu-id="3e9da-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="3e9da-132">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="3e9da-132">Ensure</span></span> | <span data-ttu-id="3e9da-133">Indica se o serviço de destino existe no sistema.</span><span class="sxs-lookup"><span data-stu-id="3e9da-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="3e9da-134">Defina esta propriedade como **ausente** para se certificar de que o serviço de destino não existe.</span><span class="sxs-lookup"><span data-stu-id="3e9da-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="3e9da-135">Defini-la como **presente** (o valor predefinido) garante que o serviço de destino existe.</span><span class="sxs-lookup"><span data-stu-id="3e9da-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="3e9da-136">Caminho</span><span class="sxs-lookup"><span data-stu-id="3e9da-136">Path</span></span> | <span data-ttu-id="3e9da-137">Indique o caminho para o ficheiro binário para um novo serviço.</span><span class="sxs-lookup"><span data-stu-id="3e9da-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="3e9da-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e9da-138">Example</span></span>

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