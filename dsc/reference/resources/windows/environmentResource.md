---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recursos de ambiente de DSC
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077539"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="dc400-103">Recursos de ambiente de DSC</span><span class="sxs-lookup"><span data-stu-id="dc400-103">DSC Environment Resource</span></span>

> <span data-ttu-id="dc400-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="dc400-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="dc400-105">O __ambiente__ recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir as variáveis de ambiente de sistema.</span><span class="sxs-lookup"><span data-stu-id="dc400-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="dc400-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc400-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="dc400-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="dc400-107">Properties</span></span>

|  <span data-ttu-id="dc400-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="dc400-108">Property</span></span>  |  <span data-ttu-id="dc400-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc400-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="dc400-110">Nome</span><span class="sxs-lookup"><span data-stu-id="dc400-110">Name</span></span>| <span data-ttu-id="dc400-111">Indica o nome da variável de ambiente para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="dc400-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="dc400-112">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="dc400-112">Ensure</span></span>| <span data-ttu-id="dc400-113">Indica se existe uma variável.</span><span class="sxs-lookup"><span data-stu-id="dc400-113">Indicates if a variable exists.</span></span> <span data-ttu-id="dc400-114">Definir esta propriedade para __presente__ para criar a variável de ambiente, se não existir ou para garantir que seu valor corresponde ao que é fornecido por meio do __valor__ propriedade se a variável já existe.</span><span class="sxs-lookup"><span data-stu-id="dc400-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="dc400-115">Defina-o como __ausente__ para eliminar a variável, se existir.</span><span class="sxs-lookup"><span data-stu-id="dc400-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="dc400-116">Caminho</span><span class="sxs-lookup"><span data-stu-id="dc400-116">Path</span></span>| <span data-ttu-id="dc400-117">Define a variável de ambiente que está a ser configurada.</span><span class="sxs-lookup"><span data-stu-id="dc400-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="dc400-118">Defina esta propriedade como __$true__ se a variável é o __caminho__ variável; caso contrário, defina-o como __$false__.</span><span class="sxs-lookup"><span data-stu-id="dc400-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="dc400-119">A predefinição é __$false__.</span><span class="sxs-lookup"><span data-stu-id="dc400-119">The default is __$false__.</span></span> <span data-ttu-id="dc400-120">Se a variável a ser configurada é a __caminho__ variável, o valor fornecido por meio do __valor__ propriedade será anexada ao valor existente.</span><span class="sxs-lookup"><span data-stu-id="dc400-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="dc400-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dc400-121">DependsOn</span></span> | <span data-ttu-id="dc400-122">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="dc400-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dc400-123">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="dc400-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="dc400-124">Valor</span><span class="sxs-lookup"><span data-stu-id="dc400-124">Value</span></span>| <span data-ttu-id="dc400-125">O valor a atribuir à variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="dc400-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="dc400-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc400-126">Example</span></span>

<span data-ttu-id="dc400-127">O exemplo seguinte garante que __TestEnvironmentVariable__ está presente e tem o valor __TestValue__.</span><span class="sxs-lookup"><span data-stu-id="dc400-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="dc400-128">Se não estiver presente, ele o cria.</span><span class="sxs-lookup"><span data-stu-id="dc400-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```