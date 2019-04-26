---
title: Define o parâmetro de cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068521"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="24de2-102">Cmdlet Parameter Sets (Conjuntos de Parâmetros de Cmdlets)</span><span class="sxs-lookup"><span data-stu-id="24de2-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="24de2-103">Windows PowerShell utiliza conjuntos de parâmetros que lhe permite escrever um único cmdlet que pode realizar ações diferentes para diferentes cenários.</span><span class="sxs-lookup"><span data-stu-id="24de2-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="24de2-104">Conjuntos de parâmetros permitem expor diferentes parâmetros para o usuário e retorne informações distintas com base nos parâmetros especificados pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="24de2-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="24de2-105">Exemplos de conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="24de2-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="24de2-106">Por exemplo, o `Get-EventLog` cmdlet (fornecido pelo Windows PowerShell) retorna informações diferentes, dependendo se o utilizador Especifica os `List` ou `LogName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="24de2-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="24de2-107">Se o `List` parâmetro for especificado, o cmdlet retorna informações sobre os ficheiros de registo próprios, mas não as informações de eventos que contêm.</span><span class="sxs-lookup"><span data-stu-id="24de2-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="24de2-108">Se o `LogName` parâmetro for especificado, o cmdlet retorna informações sobre os eventos no registo de eventos específico.</span><span class="sxs-lookup"><span data-stu-id="24de2-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="24de2-109">O `List` e `LogName` parâmetros identificam dois conjuntos de parâmetros separados.</span><span class="sxs-lookup"><span data-stu-id="24de2-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="24de2-110">Parâmetro exclusivo</span><span class="sxs-lookup"><span data-stu-id="24de2-110">Unique Parameter</span></span>

<span data-ttu-id="24de2-111">Cada conjunto de parâmetros tem de ter um parâmetro único que o tempo de execução do Windows PowerShell pode utilizar para expor o conjunto de parâmetros adequada.</span><span class="sxs-lookup"><span data-stu-id="24de2-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="24de2-112">Se possível, o único parâmetro deve ser um parâmetro obrigatório.</span><span class="sxs-lookup"><span data-stu-id="24de2-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="24de2-113">Quando um parâmetro for obrigatório, o utilizador é forçado a especificar o parâmetro e o tempo de execução do Windows PowerShell pode usar esse parâmetro para identificar o parâmetro definido para utilizar.</span><span class="sxs-lookup"><span data-stu-id="24de2-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="24de2-114">O único parâmetro não pode ser obrigatório se o seu cmdlet foi concebido para ser executado sem especificar quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="24de2-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="24de2-115">Vários conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="24de2-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="24de2-116">Na ilustração seguinte, a coluna da esquerda mostra três conjuntos de parâmetros válido.</span><span class="sxs-lookup"><span data-stu-id="24de2-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="24de2-117">O parâmetro A é exclusivo para o primeiro conjunto de parâmetros, parâmetro B é exclusivo para o segundo conjunto de parâmetros e parâmetro C é exclusivo para o terceiro conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="24de2-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="24de2-118">No entanto, na coluna da direita, os conjuntos de parâmetros não tem um parâmetro exclusivo.</span><span class="sxs-lookup"><span data-stu-id="24de2-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="24de2-120">Requisitos do conjunto de parâmetros</span><span class="sxs-lookup"><span data-stu-id="24de2-120">Parameter Set Requirements</span></span>

<span data-ttu-id="24de2-121">Os seguintes requisitos se aplicam a todos os conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="24de2-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="24de2-122">Cada conjunto de parâmetros tem de ter, pelo menos, um parâmetro exclusivo.</span><span class="sxs-lookup"><span data-stu-id="24de2-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="24de2-123">Se possível, fazer este parâmetro um parâmetro obrigatório.</span><span class="sxs-lookup"><span data-stu-id="24de2-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="24de2-124">Um conjunto de parâmetros que contém vários parâmetros posicionais tem de definir as posições exclusivas para cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="24de2-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="24de2-125">Não existem dois parâmetros posicionais podem especificar a mesma posição.</span><span class="sxs-lookup"><span data-stu-id="24de2-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="24de2-126">Apenas um parâmetro de um conjunto pode declarar o `ValueFromPipeline` palavra-chave com um valor de `true`.</span><span class="sxs-lookup"><span data-stu-id="24de2-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="24de2-127">Podem definir vários parâmetros a `ValueFromPipelineByPropertyName` palavra-chave com um valor de `true`.</span><span class="sxs-lookup"><span data-stu-id="24de2-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="24de2-128">Se não for especificado nenhum conjunto de parâmetros para um parâmetro, o parâmetro pertence a todos os conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="24de2-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="24de2-129">Conjuntos de parâmetros padrão</span><span class="sxs-lookup"><span data-stu-id="24de2-129">Default Parameter Sets</span></span>

<span data-ttu-id="24de2-130">Quando vários conjuntos de parâmetros são definidos, pode utilizar o `DefaultParameterSetName` palavra-chave do atributo Cmdlet para especificar o conjunto de parâmetros padrão.</span><span class="sxs-lookup"><span data-stu-id="24de2-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="24de2-131">Windows PowerShell utiliza o parâmetro de padrão definido se ele não é possível determinar o parâmetro definido para utilizar com base nas informações fornecidas pelo comando.</span><span class="sxs-lookup"><span data-stu-id="24de2-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="24de2-132">Para obter mais informações sobre o atributo de Cmdlet, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="24de2-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="24de2-133">Declaração de conjuntos de parâmetros</span><span class="sxs-lookup"><span data-stu-id="24de2-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="24de2-134">Para criar um conjunto de parâmetros, tem de especificar o `ParameterSetName` palavra-chave quando declara o atributo de parâmetro para cada parâmetro no conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="24de2-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="24de2-135">Para os parâmetros que pertencem a vários conjuntos de parâmetros, adicione um atributo de parâmetro para cada conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="24de2-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="24de2-136">Isto permite-lhe definir o parâmetro de forma diferente para cada conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="24de2-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="24de2-137">Por exemplo, pode definir um parâmetro como obrigatórios num conjunto e opcionais em outro.</span><span class="sxs-lookup"><span data-stu-id="24de2-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="24de2-138">No entanto, cada conjunto de parâmetros tem de conter um parâmetro exclusivo.</span><span class="sxs-lookup"><span data-stu-id="24de2-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="24de2-139">No exemplo a seguir, o `UserName` parâmetro é o único parâmetro de conjunto de parâmetros Test01 e o `ComputerName` parâmetro é o parâmetro único do conjunto de parâmetros Test02.</span><span class="sxs-lookup"><span data-stu-id="24de2-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="24de2-140">O `SharedParam` parâmetro pertence a ambos os conjuntos e é obrigatório para o parâmetro de Test01 definido, mas é opcional para o conjunto de parâmetros Test02.</span><span class="sxs-lookup"><span data-stu-id="24de2-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

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
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```