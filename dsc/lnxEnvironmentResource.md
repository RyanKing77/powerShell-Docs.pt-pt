---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxEnvironment recursos
ms.openlocfilehash: 6d1d5e578e9a7ddda0e70063f86867de2e87a52e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="76d11-103">DSC de Linux nxEnvironment recursos</span><span class="sxs-lookup"><span data-stu-id="76d11-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="76d11-104">O **nxEnvironment** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir as variáveis de ambiente de sistema num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="76d11-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="76d11-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76d11-105">Syntax</span></span>

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="76d11-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="76d11-106">Properties</span></span>

|  <span data-ttu-id="76d11-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="76d11-107">Property</span></span> |  <span data-ttu-id="76d11-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="76d11-108">Description</span></span> |
|---|---|
| <span data-ttu-id="76d11-109">Nome</span><span class="sxs-lookup"><span data-stu-id="76d11-109">Name</span></span>| <span data-ttu-id="76d11-110">Indica o nome da variável de ambiente para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="76d11-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="76d11-111">Valor</span><span class="sxs-lookup"><span data-stu-id="76d11-111">Value</span></span>| <span data-ttu-id="76d11-112">O valor a atribuir à variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="76d11-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="76d11-113">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="76d11-113">Ensure</span></span>| <span data-ttu-id="76d11-114">Determina se deve verificar se existe a variável.</span><span class="sxs-lookup"><span data-stu-id="76d11-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="76d11-115">Defina esta propriedade para "Presente" para garantir que existe a variável.</span><span class="sxs-lookup"><span data-stu-id="76d11-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="76d11-116">Defina-o para "Ausente", certifique-se de que a variável não existe.</span><span class="sxs-lookup"><span data-stu-id="76d11-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="76d11-117">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="76d11-117">The default value is "Present".</span></span>|
| <span data-ttu-id="76d11-118">Caminho</span><span class="sxs-lookup"><span data-stu-id="76d11-118">Path</span></span>| <span data-ttu-id="76d11-119">Define a variável de ambiente que está a ser configurada.</span><span class="sxs-lookup"><span data-stu-id="76d11-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="76d11-120">Defina esta propriedade como **$true** se a variável é o **caminho** variável; caso contrário, defina-o como **$false**.</span><span class="sxs-lookup"><span data-stu-id="76d11-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="76d11-121">A predefinição é **$false**.</span><span class="sxs-lookup"><span data-stu-id="76d11-121">The default is **$false**.</span></span> <span data-ttu-id="76d11-122">Se a variável que está a ser configurada é o **caminho** variável, o valor fornecido através de **valor** propriedade será anexada ao valor existente.</span><span class="sxs-lookup"><span data-stu-id="76d11-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="76d11-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="76d11-123">DependsOn</span></span> | <span data-ttu-id="76d11-124">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="76d11-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="76d11-125">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="76d11-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="76d11-126">Informações Adicionais</span><span class="sxs-lookup"><span data-stu-id="76d11-126">Additional Information</span></span>

* <span data-ttu-id="76d11-127">Se **caminho** não existe ou defina para **$false**, variáveis de ambiente são geridas na `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="76d11-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="76d11-128">Os programas ou scripts poderão requerer configuração à origem de `/etc/environment` ficheiro para aceder as variáveis de ambiente gerido.</span><span class="sxs-lookup"><span data-stu-id="76d11-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="76d11-129">Se **caminho** está definido como **$true**, a variável de ambiente é gerida no ficheiro `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="76d11-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="76d11-130">Este ficheiro será criado se não existir.</span><span class="sxs-lookup"><span data-stu-id="76d11-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="76d11-131">Se **Certifique-se** está definido para "Ausente" e **caminho** está definido como **$true**, uma variável de ambiente existente, apenas será removida do `/etc/profile.d/DSCenvironment.sh` e não a partir de outros ficheiros.</span><span class="sxs-lookup"><span data-stu-id="76d11-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="76d11-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76d11-132">Example</span></span>

<span data-ttu-id="76d11-133">O exemplo seguinte mostra como utilizar o **nxEnvironment** recursos para garantir que **TestEnvironmentVariable** está presente e tem o valor de "Teste-Value".</span><span class="sxs-lookup"><span data-stu-id="76d11-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="76d11-134">Se **TestEnvironmentVariable** é não existir, será criado.</span><span class="sxs-lookup"><span data-stu-id="76d11-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```