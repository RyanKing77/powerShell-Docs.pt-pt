---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 2016-12-12
title: obter pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: eb9f42ab4d9cec111e03a096b2f00740e97ee1b7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="4f9d0-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4f9d0-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="4f9d0-104">RESUMO</span><span class="sxs-lookup"><span data-stu-id="4f9d0-104">SYNOPSIS</span></span>

<span data-ttu-id="4f9d0-105">Devolve um conjunto de regras de autorização de acesso de Web do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="4f9d0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f9d0-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="4f9d0-107">ID</span><span class="sxs-lookup"><span data-stu-id="4f9d0-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="4f9d0-108">Nome</span><span class="sxs-lookup"><span data-stu-id="4f9d0-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="4f9d0-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="4f9d0-109">DESCRIPTION</span></span>

<span data-ttu-id="4f9d0-110">O **Get-PswaAuthorizationRule** cmdlet devolve um conjunto de regras de autorização de acesso de Web do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="4f9d0-111">Se nem o **Id** parâmetro nem o **RuleName** parâmetro for especificado, em seguida, este cmdlet apresenta uma lista de todas as regras.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="4f9d0-112">O **Id** parâmetro pode ser utilizado para filtrar os resultados.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="4f9d0-113">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="4f9d0-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="4f9d0-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="4f9d0-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="4f9d0-115">Especifica os identificadores (IDs), as regras que deve receber este cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="4f9d0-116">Se não existem IDs forem especificados, este cmdlet devolve todas as regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="4f9d0-117">Aliases</span><span class="sxs-lookup"><span data-stu-id="4f9d0-117">Aliases</span></span>                              | <span data-ttu-id="4f9d0-118">nenhum</span><span class="sxs-lookup"><span data-stu-id="4f9d0-118">none</span></span>                                 |
| <span data-ttu-id="4f9d0-119">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="4f9d0-119">Required?</span></span>                            | <span data-ttu-id="4f9d0-120">falso</span><span class="sxs-lookup"><span data-stu-id="4f9d0-120">false</span></span>                                |
| <span data-ttu-id="4f9d0-121">Posição?</span><span class="sxs-lookup"><span data-stu-id="4f9d0-121">Position?</span></span>                            | <span data-ttu-id="4f9d0-122">2</span><span class="sxs-lookup"><span data-stu-id="4f9d0-122">2</span></span>                                    |
| <span data-ttu-id="4f9d0-123">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="4f9d0-123">Default Value</span></span>                        | <span data-ttu-id="4f9d0-124">nenhum</span><span class="sxs-lookup"><span data-stu-id="4f9d0-124">none</span></span>                                 |
| <span data-ttu-id="4f9d0-125">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="4f9d0-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4f9d0-126">VERDADEIRO (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4f9d0-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="4f9d0-127">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="4f9d0-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4f9d0-128">falso</span><span class="sxs-lookup"><span data-stu-id="4f9d0-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="4f9d0-129">-RuleName&lt;cadeia\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="4f9d0-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="4f9d0-130">Especifica os nomes das regras de autorização para obter.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="4f9d0-131">Este parâmetro devolve quaisquer regras que correspondem exatamente os nomes de regra de cadeias nesta matriz.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||  
|-|-|
| <span data-ttu-id="4f9d0-132">Aliases</span><span class="sxs-lookup"><span data-stu-id="4f9d0-132">Aliases</span></span>                              | <span data-ttu-id="4f9d0-133">nenhum</span><span class="sxs-lookup"><span data-stu-id="4f9d0-133">none</span></span>                                 |
| <span data-ttu-id="4f9d0-134">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="4f9d0-134">Required?</span></span>                            | <span data-ttu-id="4f9d0-135">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="4f9d0-135">true</span></span>                                 |
| <span data-ttu-id="4f9d0-136">Posição?</span><span class="sxs-lookup"><span data-stu-id="4f9d0-136">Position?</span></span>                            | <span data-ttu-id="4f9d0-137">2</span><span class="sxs-lookup"><span data-stu-id="4f9d0-137">2</span></span>                                    |
| <span data-ttu-id="4f9d0-138">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="4f9d0-138">Default Value</span></span>                        | <span data-ttu-id="4f9d0-139">nenhum</span><span class="sxs-lookup"><span data-stu-id="4f9d0-139">none</span></span>                                 |
| <span data-ttu-id="4f9d0-140">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="4f9d0-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4f9d0-141">VERDADEIRO (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="4f9d0-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="4f9d0-142">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="4f9d0-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4f9d0-143">falso</span><span class="sxs-lookup"><span data-stu-id="4f9d0-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="4f9d0-144">&lt;Parâmetroscomuns&gt;</span><span class="sxs-lookup"><span data-stu-id="4f9d0-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="4f9d0-145">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="4f9d0-146">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4f9d0-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="4f9d0-147">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="4f9d0-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="4f9d0-148">Int\[\]</span><span class="sxs-lookup"><span data-stu-id="4f9d0-148">int\[\]</span></span>

<span data-ttu-id="4f9d0-149">Este cmdlet aceita uma matriz de números inteiros ou uma matriz de valores de cadeia como entrada.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="4f9d0-150">Cadeia\[\]</span><span class="sxs-lookup"><span data-stu-id="4f9d0-150">String\[\]</span></span>

<span data-ttu-id="4f9d0-151">Este cmdlet aceita uma matriz de números inteiros ou uma matriz de valores de cadeia como entrada.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="4f9d0-152">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="4f9d0-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="4f9d0-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="4f9d0-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="4f9d0-154">Este cmdlet produz um objeto de PswaAuthorizationRule como saída.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="4f9d0-155">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="4f9d0-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="4f9d0-156">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="4f9d0-156">EXAMPLE 1</span></span>

<span data-ttu-id="4f9d0-157">Neste exemplo obtém todas as regras.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="4f9d0-158">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="4f9d0-158">EXAMPLE 2</span></span>

<span data-ttu-id="4f9d0-159">Neste exemplo obtém uma regra com um ID de *2*.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="4f9d0-160">EXEMPLO 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="4f9d0-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="4f9d0-161">Este exemplo ilustra como o cmdlet aceita um valor do pipeline.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="4f9d0-162">Um id de regra e um nome de regra são transmitidos este cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f9d0-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="4f9d0-163">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="4f9d0-163">Related topics</span></span>

- [<span data-ttu-id="4f9d0-164">Adicionar-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4f9d0-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="4f9d0-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4f9d0-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="4f9d0-166">Teste-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4f9d0-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="4f9d0-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="4f9d0-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
