---
title: Conjuntos de parâmetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936191"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="9867a-102">Conjuntos de parâmetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="9867a-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="9867a-103">O PowerShell usa conjuntos de parâmetros para permitir que você escreva um único cmdlet que possa realizar ações diferentes para cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="9867a-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="9867a-104">Os conjuntos de parâmetros permitem que você exponha parâmetros diferentes para o usuário.</span><span class="sxs-lookup"><span data-stu-id="9867a-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="9867a-105">E, para retornar informações diferentes com base nos parâmetros especificados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="9867a-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="9867a-106">Exemplos de conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="9867a-106">Examples of parameter sets</span></span>

<span data-ttu-id="9867a-107">Por exemplo, o cmdlet `Get-EventLog` do PowerShell retorna informações diferentes dependendo se o usuário especifica a **lista** ou o parâmetro **LogName** .</span><span class="sxs-lookup"><span data-stu-id="9867a-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="9867a-108">Se o parâmetro **list** for especificado, o cmdlet retornará informações sobre os próprios arquivos de log, mas não as informações de evento que eles contêm.</span><span class="sxs-lookup"><span data-stu-id="9867a-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="9867a-109">Se o parâmetro **LogName** for especificado, o cmdlet retornará informações sobre os eventos em um log de eventos específico.</span><span class="sxs-lookup"><span data-stu-id="9867a-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="9867a-110">Os parâmetros **list** e **LogName** identificam dois conjuntos de parâmetros separados.</span><span class="sxs-lookup"><span data-stu-id="9867a-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="9867a-111">Parâmetro exclusivo</span><span class="sxs-lookup"><span data-stu-id="9867a-111">Unique parameter</span></span>

<span data-ttu-id="9867a-112">Cada conjunto de parâmetros deve ter um parâmetro exclusivo que o tempo de execução do PowerShell usa para expor o conjunto de parâmetros apropriado.</span><span class="sxs-lookup"><span data-stu-id="9867a-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="9867a-113">Se possível, o parâmetro exclusivo deve ser um parâmetro obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9867a-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="9867a-114">Quando um parâmetro é obrigatório, o usuário deve especificar o parâmetro e o tempo de execução do PowerShell usa esse parâmetro para identificar o conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9867a-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="9867a-115">O parâmetro exclusivo não poderá ser obrigatório se o cmdlet for projetado para ser executado sem especificar parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9867a-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="9867a-116">Vários conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="9867a-116">Multiple parameter sets</span></span>

<span data-ttu-id="9867a-117">Na ilustração a seguir, a coluna à esquerda mostra três conjuntos de parâmetros válidos.</span><span class="sxs-lookup"><span data-stu-id="9867a-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="9867a-118">O **parâmetro A** é exclusivo para o primeiro conjunto de parâmetros, o **parâmetro B** é exclusivo para o segundo conjunto de parâmetros, e o **parâmetro C** é exclusivo para o terceiro conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9867a-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="9867a-119">Na coluna à direita, os conjuntos de parâmetros não têm um parâmetro exclusivo.</span><span class="sxs-lookup"><span data-stu-id="9867a-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="9867a-121">Requisitos do conjunto de parâmetros</span><span class="sxs-lookup"><span data-stu-id="9867a-121">Parameter set requirements</span></span>

<span data-ttu-id="9867a-122">Os requisitos a seguir se aplicam a todos os conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9867a-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="9867a-123">Cada conjunto de parâmetros deve ter pelo menos um parâmetro exclusivo.</span><span class="sxs-lookup"><span data-stu-id="9867a-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="9867a-124">Se possível, torne esse parâmetro um parâmetro obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9867a-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="9867a-125">Um conjunto de parâmetros que contém vários parâmetros posicionais deve definir posições exclusivas para cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9867a-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="9867a-126">Dois parâmetros posicionais não podem especificar a mesma posição.</span><span class="sxs-lookup"><span data-stu-id="9867a-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="9867a-127">Somente um parâmetro em um conjunto pode declarar a `ValueFromPipeline` palavra-chave com um `true`valor de.</span><span class="sxs-lookup"><span data-stu-id="9867a-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="9867a-128">Vários parâmetros podem definir a `ValueFromPipelineByPropertyName` palavra-chave com um `true`valor de.</span><span class="sxs-lookup"><span data-stu-id="9867a-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="9867a-129">Se nenhum conjunto de parâmetros for especificado para um parâmetro, o parâmetro pertencerá a todos os conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9867a-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="9867a-130">Para um cmdlet ou uma função, há um limite de conjuntos de parâmetros 32.</span><span class="sxs-lookup"><span data-stu-id="9867a-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="9867a-131">Conjuntos de parâmetros padrão</span><span class="sxs-lookup"><span data-stu-id="9867a-131">Default parameter sets</span></span>

<span data-ttu-id="9867a-132">Quando vários conjuntos de parâmetros são definidos, você pode usar `DefaultParameterSetName` a palavra-chave do atributo **cmdlet** para especificar o conjunto de parâmetros padrão.</span><span class="sxs-lookup"><span data-stu-id="9867a-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="9867a-133">O PowerShell usará o conjunto de parâmetros padrão se não puder determinar o conjunto de parâmetros a ser usado com base nas informações fornecidas pelo comando.</span><span class="sxs-lookup"><span data-stu-id="9867a-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="9867a-134">Para obter mais informações sobre o atributo **cmdlet** , consulte [declaração de atributo de cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9867a-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="9867a-135">Declarando conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="9867a-135">Declaring parameter sets</span></span>

<span data-ttu-id="9867a-136">Para criar um conjunto de parâmetros, você deve especificar `ParameterSetName` a palavra-chave ao declarar o atributo de **parâmetro** para cada parâmetro no conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9867a-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="9867a-137">Para parâmetros que pertencem a vários conjuntos de parâmetros, adicione um atributo de **parâmetro** para cada conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9867a-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="9867a-138">Esse atributo permite que você defina o parâmetro de forma diferente para cada conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9867a-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="9867a-139">Por exemplo, você pode definir um parâmetro como obrigatório em um conjunto e opcional em outro.</span><span class="sxs-lookup"><span data-stu-id="9867a-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="9867a-140">No entanto, cada conjunto de parâmetros deve conter um parâmetro exclusivo.</span><span class="sxs-lookup"><span data-stu-id="9867a-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="9867a-141">Para obter mais informações, consulte [declaração de atributo de parâmetro](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9867a-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="9867a-142">No exemplo a seguir, o parâmetro **username** é o parâmetro exclusivo do conjunto `Test01` de parâmetros e o parâmetro **ComputerName** `Test02` é o parâmetro exclusivo do conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9867a-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="9867a-143">O parâmetro **SharedParam** pertence a ambos os conjuntos e é obrigatório para `Test01` o conjunto de parâmetros, mas `Test02` opcional para o conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9867a-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;
```
