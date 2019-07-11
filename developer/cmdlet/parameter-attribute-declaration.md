---
title: Declaração de atributo de parâmetro | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735129"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="1c550-102">Parameter Attribute Declaration (Declaração do Atributo Parameter)</span><span class="sxs-lookup"><span data-stu-id="1c550-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="1c550-103">O atributo de parâmetro identifica uma propriedade pública da classe cmdlet como um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c550-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c550-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c550-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="1c550-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c550-105">Parameters</span></span>

<span data-ttu-id="1c550-106">`Mandatory` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter.</span><span class="sxs-lookup"><span data-stu-id="1c550-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="1c550-107">`True` indica que o parâmetro de cmdlet é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="1c550-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="1c550-108">Se não for fornecido um parâmetro necessário quando o cmdlet é invocado, o Windows PowerShell pede ao utilizador para um valor de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1c550-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="1c550-109">A predefinição é `false`.</span><span class="sxs-lookup"><span data-stu-id="1c550-109">The default is `false`.</span></span>

<span data-ttu-id="1c550-110">`ParameterSetName` ([System. String](/dotnet/api/System.String)) opcional chamado de parameter.</span><span class="sxs-lookup"><span data-stu-id="1c550-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="1c550-111">Especifica que o parâmetro definido que pertence este parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c550-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="1c550-112">Se não for especificado nenhum conjunto de parâmetros, o parâmetro pertence a todos os conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1c550-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="1c550-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) opcional chamado de parameter.</span><span class="sxs-lookup"><span data-stu-id="1c550-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="1c550-114">Especifica a posição do parâmetro dentro de um comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c550-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="1c550-115">`ValueFromPipeline` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter.</span><span class="sxs-lookup"><span data-stu-id="1c550-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="1c550-116">`True` indica que o parâmetro de cmdlet assume o valor de um objeto de pipeline.</span><span class="sxs-lookup"><span data-stu-id="1c550-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="1c550-117">Especifique essa palavra-chave, se o cmdlet acessa o completa de objeto, não apenas uma propriedade do objeto.</span><span class="sxs-lookup"><span data-stu-id="1c550-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="1c550-118">A predefinição é `false`.</span><span class="sxs-lookup"><span data-stu-id="1c550-118">The default is `false`.</span></span>

<span data-ttu-id="1c550-119">`ValueFromPipelineByPropertyName` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter.</span><span class="sxs-lookup"><span data-stu-id="1c550-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="1c550-120">`True` indica que o parâmetro de cmdlet assume o valor de uma propriedade de um objeto de pipeline que tenha o mesmo nome ou o alias do mesmo como este parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1c550-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="1c550-121">Por exemplo, se o cmdlet tem um `Name` parâmetro e o objeto de pipeline também tem uma `Name` propriedade, o valor da `Name` propriedade é atribuída ao `Name` parâmetro do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c550-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="1c550-122">A predefinição é `false`.</span><span class="sxs-lookup"><span data-stu-id="1c550-122">The default is `false`.</span></span>

<span data-ttu-id="1c550-123">`ValueFromRemainingArguments` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter.</span><span class="sxs-lookup"><span data-stu-id="1c550-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="1c550-124">`True` indica que o parâmetro de cmdlet aceita todos os argumentos restantes que são transmitidos ao cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c550-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="1c550-125">A predefinição é `false`.</span><span class="sxs-lookup"><span data-stu-id="1c550-125">The default is `false`.</span></span>

<span data-ttu-id="1c550-126">`HelpMessage` Opcional chamado de parameter.</span><span class="sxs-lookup"><span data-stu-id="1c550-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="1c550-127">Especifica uma breve descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1c550-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="1c550-128">Windows PowerShell apresenta esta mensagem quando um cmdlet é executado e não for especificado um parâmetro obrigatório.</span><span class="sxs-lookup"><span data-stu-id="1c550-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="1c550-129">`HelpMessageBaseName` Opcional chamado de parameter. Especifica a localização onde residem os identificadores de recurso.</span><span class="sxs-lookup"><span data-stu-id="1c550-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="1c550-130">Por exemplo, este parâmetro pode especificar um assembly de recurso que contém mensagens de ajuda que pretende localizar.</span><span class="sxs-lookup"><span data-stu-id="1c550-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="1c550-131">`HelpMessageResourceId` Opcional chamado de parameter. Especifica o identificador de recurso para uma mensagem de ajuda.</span><span class="sxs-lookup"><span data-stu-id="1c550-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c550-132">Observações</span><span class="sxs-lookup"><span data-stu-id="1c550-132">Remarks</span></span>

- <span data-ttu-id="1c550-133">Para obter mais informações sobre como declarar este atributo, consulte [como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1c550-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="1c550-134">Um cmdlet pode ter qualquer número de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1c550-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="1c550-135">No entanto, para uma melhor experiência de utilizador, limite o número de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1c550-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="1c550-136">Parâmetros devem ser declarados em campos de nestatické públicos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="1c550-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="1c550-137">Os parâmetros devem ser declarados em propriedades.</span><span class="sxs-lookup"><span data-stu-id="1c550-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="1c550-138">A propriedade tem de ter um acessador do conjunto público e se o `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` palavra-chave for especificada, a propriedade tem de ter um acessador get público.</span><span class="sxs-lookup"><span data-stu-id="1c550-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="1c550-139">Quando especificar parâmetros posicionais, limite o número de parâmetros posicionais, num parâmetro definido para menos de cinco.</span><span class="sxs-lookup"><span data-stu-id="1c550-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="1c550-140">E, parâmetros posicionais não tem de ser contíguo.</span><span class="sxs-lookup"><span data-stu-id="1c550-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="1c550-141">Posições 5, 100 e 250 funcionam da mesma como posições 0, 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="1c550-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="1c550-142">Quando o `Position` palavra-chave não for especificado, o parâmetro de cmdlet deve ser referenciado pelo respetivo nome.</span><span class="sxs-lookup"><span data-stu-id="1c550-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="1c550-143">Quando utiliza conjuntos de parâmetros, tenha em atenção o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1c550-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="1c550-144">Cada conjunto de parâmetros tem de ter, pelo menos, um parâmetro exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1c550-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="1c550-145">Cmdlet bom design indica que este parâmetro exclusivo também deve ser obrigatório se for possível.</span><span class="sxs-lookup"><span data-stu-id="1c550-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="1c550-146">Se seu cmdlet foi concebido para ser executado sem parâmetros, o único parâmetro não pode ser obrigatório.</span><span class="sxs-lookup"><span data-stu-id="1c550-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="1c550-147">Nenhum conjunto de parâmetros deve conter mais de um parâmetro posicional com a mesma posição.</span><span class="sxs-lookup"><span data-stu-id="1c550-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="1c550-148">Apenas um parâmetro num conjunto de parâmetros deve declarar `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="1c550-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="1c550-149">Podem definir vários parâmetros `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="1c550-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="1c550-150">Podem definir vários parâmetros `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="1c550-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="1c550-151">Para obter mais informações sobre as diretrizes para os nomes de parâmetros, consulte [nomes de parâmetros de Cmdlet](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="1c550-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="1c550-152">O atributo de parâmetro é definido pela [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="1c550-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c550-153">Veja Também</span><span class="sxs-lookup"><span data-stu-id="1c550-153">See Also</span></span>

[<span data-ttu-id="1c550-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="1c550-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="1c550-155">Nomes dos parâmetros do cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c550-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="1c550-156">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c550-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
