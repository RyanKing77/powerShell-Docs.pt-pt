---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recurso de ambiente de DSC
ms.openlocfilehash: 7c98798fa0e8fc865798ea30530e41ac87b2dadc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="17d6a-103">Recurso de ambiente de DSC</span><span class="sxs-lookup"><span data-stu-id="17d6a-103">DSC Environment Resource</span></span>

> <span data-ttu-id="17d6a-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="17d6a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="17d6a-105">O __ambiente__ recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir as variáveis de ambiente de sistema.</span><span class="sxs-lookup"><span data-stu-id="17d6a-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="17d6a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17d6a-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="17d6a-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="17d6a-107">Properties</span></span>

|  <span data-ttu-id="17d6a-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="17d6a-108">Property</span></span>  |  <span data-ttu-id="17d6a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="17d6a-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="17d6a-110">Nome</span><span class="sxs-lookup"><span data-stu-id="17d6a-110">Name</span></span>| <span data-ttu-id="17d6a-111">Indica o nome da variável de ambiente para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="17d6a-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="17d6a-112">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="17d6a-112">Ensure</span></span>| <span data-ttu-id="17d6a-113">Indica se existe uma variável.</span><span class="sxs-lookup"><span data-stu-id="17d6a-113">Indicates if a variable exists.</span></span> <span data-ttu-id="17d6a-114">Defina esta propriedade como __presente__ para criar a variável de ambiente, se não existir ou certifique-se de que corresponde ao respetivo valor que é fornecido através de __valor__ propriedade se a variável já existe.</span><span class="sxs-lookup"><span data-stu-id="17d6a-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="17d6a-115">Defina-o como __ausente__ para eliminar a variável, se existir.</span><span class="sxs-lookup"><span data-stu-id="17d6a-115">Set it to __Absent__ to delete the variable if it exists.</span></span>| 
| <span data-ttu-id="17d6a-116">Caminho</span><span class="sxs-lookup"><span data-stu-id="17d6a-116">Path</span></span>| <span data-ttu-id="17d6a-117">Define a variável de ambiente que está a ser configurada.</span><span class="sxs-lookup"><span data-stu-id="17d6a-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="17d6a-118">Defina esta propriedade como __$true__ se a variável é o __caminho__ variável; caso contrário, defina-o como __$false__.</span><span class="sxs-lookup"><span data-stu-id="17d6a-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="17d6a-119">A predefinição é __$false__.</span><span class="sxs-lookup"><span data-stu-id="17d6a-119">The default is __$false__.</span></span> <span data-ttu-id="17d6a-120">Se a variável que está a ser configurada é o __caminho__ variável, o valor fornecido através de __valor__ propriedade será anexada ao valor existente.</span><span class="sxs-lookup"><span data-stu-id="17d6a-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>| 
| <span data-ttu-id="17d6a-121">dependsOn</span><span class="sxs-lookup"><span data-stu-id="17d6a-121">DependsOn</span></span> | <span data-ttu-id="17d6a-122">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="17d6a-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="17d6a-123">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="17d6a-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="17d6a-124">Valor</span><span class="sxs-lookup"><span data-stu-id="17d6a-124">Value</span></span>| <span data-ttu-id="17d6a-125">O valor a atribuir à variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="17d6a-125">The value to assign to the environment variable.</span></span>| 

## <a name="example"></a><span data-ttu-id="17d6a-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17d6a-126">Example</span></span>

<span data-ttu-id="17d6a-127">O exemplo seguinte garante que __TestEnvironmentVariable__ está presente e tem o valor __TestValue__.</span><span class="sxs-lookup"><span data-stu-id="17d6a-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="17d6a-128">Se não estiver presente, criá-lo.</span><span class="sxs-lookup"><span data-stu-id="17d6a-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```

