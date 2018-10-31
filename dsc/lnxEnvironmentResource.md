---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxEnvironment recursos
ms.openlocfilehash: 763ec560faa6adaf42aef3c21c9045be95f780bc
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225986"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="d8bb0-103">DSC para Linux nxEnvironment recursos</span><span class="sxs-lookup"><span data-stu-id="d8bb0-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="d8bb0-104">O **nxEnvironment** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir as variáveis de ambiente de sistema num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8bb0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8bb0-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="d8bb0-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d8bb0-106">Properties</span></span>

|  <span data-ttu-id="d8bb0-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d8bb0-107">Property</span></span> |  <span data-ttu-id="d8bb0-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8bb0-108">Description</span></span> |
|---|---|
| <span data-ttu-id="d8bb0-109">Nome</span><span class="sxs-lookup"><span data-stu-id="d8bb0-109">Name</span></span>| <span data-ttu-id="d8bb0-110">Indica o nome da variável de ambiente para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="d8bb0-111">Valor</span><span class="sxs-lookup"><span data-stu-id="d8bb0-111">Value</span></span>| <span data-ttu-id="d8bb0-112">O valor a atribuir à variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="d8bb0-113">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="d8bb0-113">Ensure</span></span>| <span data-ttu-id="d8bb0-114">Determina se deve verificar se a variável existe.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="d8bb0-115">Defina esta propriedade para "Presente" para garantir que a variável existe.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="d8bb0-116">Defini-lo como "Ausente", certifique-se de que a variável não existe.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="d8bb0-117">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="d8bb0-117">The default value is "Present".</span></span>|
| <span data-ttu-id="d8bb0-118">Caminho</span><span class="sxs-lookup"><span data-stu-id="d8bb0-118">Path</span></span>| <span data-ttu-id="d8bb0-119">Define a variável de ambiente que está a ser configurada.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="d8bb0-120">Defina esta propriedade como **$true** se a variável é o **caminho** variável; caso contrário, defina-o como **$false**.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="d8bb0-121">A predefinição é **$false**.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-121">The default is **$false**.</span></span> <span data-ttu-id="d8bb0-122">Se a variável a ser configurada é a **caminho** variável, o valor fornecido por meio do **valor** propriedade será anexada ao valor existente.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="d8bb0-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d8bb0-123">DependsOn</span></span> | <span data-ttu-id="d8bb0-124">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d8bb0-125">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="d8bb0-126">Informações Adicionais</span><span class="sxs-lookup"><span data-stu-id="d8bb0-126">Additional Information</span></span>

* <span data-ttu-id="d8bb0-127">Se **caminho** é não existe ou definido como **$false**, as variáveis de ambiente são gerenciadas no `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="d8bb0-128">Seus programas ou scripts poderão exigir configuração para origem a `/etc/environment` ficheiros para aceder as variáveis de ambiente gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="d8bb0-129">Se **caminho** está definida como **$true**, a variável de ambiente é gerenciada no ficheiro `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="d8bb0-130">Esse arquivo será criado se não existir.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="d8bb0-131">Se **Certifique-se** está definido para "Ausente" e **caminho** está definida como **$true**, uma variável de ambiente existente, apenas será removida do `/etc/profile.d/DSCenvironment.sh` e não a partir de outros ficheiros.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="d8bb0-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8bb0-132">Example</span></span>

<span data-ttu-id="d8bb0-133">O exemplo seguinte mostra como utilizar o **nxEnvironment** recurso para se certificar de que **TestEnvironmentVariable** está presente e tem o valor "Valor de teste".</span><span class="sxs-lookup"><span data-stu-id="d8bb0-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="d8bb0-134">Se **TestEnvironmentVariable** é não existir, será criada.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```