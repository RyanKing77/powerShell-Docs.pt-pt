---
ms.topic: reference
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: Get-PswaAuthorizationRule
ms.openlocfilehash: d61dce18e87311d7d815a689ba675db44aaec3cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188913"
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="0522d-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0522d-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="0522d-104">RESUMO</span><span class="sxs-lookup"><span data-stu-id="0522d-104">SYNOPSIS</span></span>

<span data-ttu-id="0522d-105">Devolve um conjunto de regras de autorização de acesso de Web do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="0522d-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="0522d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0522d-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="0522d-107">ID</span><span class="sxs-lookup"><span data-stu-id="0522d-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="0522d-108">Nome</span><span class="sxs-lookup"><span data-stu-id="0522d-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="0522d-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="0522d-109">DESCRIPTION</span></span>

<span data-ttu-id="0522d-110">O **Get-PswaAuthorizationRule** cmdlet devolve um conjunto de regras de autorização de acesso de Web do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="0522d-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="0522d-111">Se nem o **Id** parâmetro nem o **RuleName** parâmetro for especificado, em seguida, este cmdlet apresenta uma lista de todas as regras.</span><span class="sxs-lookup"><span data-stu-id="0522d-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="0522d-112">O **Id** parâmetro pode ser utilizado para filtrar os resultados.</span><span class="sxs-lookup"><span data-stu-id="0522d-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="0522d-113">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="0522d-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="0522d-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="0522d-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="0522d-115">Especifica os identificadores (IDs), as regras que deve receber este cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0522d-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="0522d-116">Se não existem IDs forem especificados, este cmdlet devolve todas as regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="0522d-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="0522d-117">Aliases</span><span class="sxs-lookup"><span data-stu-id="0522d-117">Aliases</span></span>                              | <span data-ttu-id="0522d-118">nenhum</span><span class="sxs-lookup"><span data-stu-id="0522d-118">none</span></span>                                 |
| <span data-ttu-id="0522d-119">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="0522d-119">Required?</span></span>                            | <span data-ttu-id="0522d-120">falso</span><span class="sxs-lookup"><span data-stu-id="0522d-120">false</span></span>                                |
| <span data-ttu-id="0522d-121">Posição?</span><span class="sxs-lookup"><span data-stu-id="0522d-121">Position?</span></span>                            | <span data-ttu-id="0522d-122">2</span><span class="sxs-lookup"><span data-stu-id="0522d-122">2</span></span>                                    |
| <span data-ttu-id="0522d-123">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="0522d-123">Default Value</span></span>                        | <span data-ttu-id="0522d-124">nenhum</span><span class="sxs-lookup"><span data-stu-id="0522d-124">none</span></span>                                 |
| <span data-ttu-id="0522d-125">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="0522d-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0522d-126">VERDADEIRO (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0522d-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="0522d-127">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="0522d-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0522d-128">falso</span><span class="sxs-lookup"><span data-stu-id="0522d-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="0522d-129">-RuleName&lt;cadeia\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="0522d-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="0522d-130">Especifica os nomes das regras de autorização para obter.</span><span class="sxs-lookup"><span data-stu-id="0522d-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="0522d-131">Este parâmetro devolve quaisquer regras que correspondem exatamente os nomes de regra de cadeias nesta matriz.</span><span class="sxs-lookup"><span data-stu-id="0522d-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||
|-|-|
| <span data-ttu-id="0522d-132">Aliases</span><span class="sxs-lookup"><span data-stu-id="0522d-132">Aliases</span></span>                              | <span data-ttu-id="0522d-133">nenhum</span><span class="sxs-lookup"><span data-stu-id="0522d-133">none</span></span>                                 |
| <span data-ttu-id="0522d-134">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="0522d-134">Required?</span></span>                            | <span data-ttu-id="0522d-135">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="0522d-135">true</span></span>                                 |
| <span data-ttu-id="0522d-136">Posição?</span><span class="sxs-lookup"><span data-stu-id="0522d-136">Position?</span></span>                            | <span data-ttu-id="0522d-137">2</span><span class="sxs-lookup"><span data-stu-id="0522d-137">2</span></span>                                    |
| <span data-ttu-id="0522d-138">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="0522d-138">Default Value</span></span>                        | <span data-ttu-id="0522d-139">nenhum</span><span class="sxs-lookup"><span data-stu-id="0522d-139">none</span></span>                                 |
| <span data-ttu-id="0522d-140">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="0522d-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0522d-141">VERDADEIRO (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0522d-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="0522d-142">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="0522d-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0522d-143">falso</span><span class="sxs-lookup"><span data-stu-id="0522d-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="0522d-144">&lt;Parâmetroscomuns&gt;</span><span class="sxs-lookup"><span data-stu-id="0522d-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="0522d-145">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="0522d-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="0522d-146">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0522d-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="0522d-147">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="0522d-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="0522d-148">Int\[\]</span><span class="sxs-lookup"><span data-stu-id="0522d-148">int\[\]</span></span>

<span data-ttu-id="0522d-149">Este cmdlet aceita uma matriz de números inteiros ou uma matriz de valores de cadeia como entrada.</span><span class="sxs-lookup"><span data-stu-id="0522d-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="0522d-150">Cadeia\[\]</span><span class="sxs-lookup"><span data-stu-id="0522d-150">String\[\]</span></span>

<span data-ttu-id="0522d-151">Este cmdlet aceita uma matriz de números inteiros ou uma matriz de valores de cadeia como entrada.</span><span class="sxs-lookup"><span data-stu-id="0522d-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="0522d-152">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="0522d-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="0522d-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="0522d-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="0522d-154">Este cmdlet produz um objeto de PswaAuthorizationRule como saída.</span><span class="sxs-lookup"><span data-stu-id="0522d-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="0522d-155">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="0522d-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="0522d-156">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="0522d-156">EXAMPLE 1</span></span>

<span data-ttu-id="0522d-157">Neste exemplo obtém todas as regras.</span><span class="sxs-lookup"><span data-stu-id="0522d-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="0522d-158">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="0522d-158">EXAMPLE 2</span></span>

<span data-ttu-id="0522d-159">Neste exemplo obtém uma regra com um ID de *2*.</span><span class="sxs-lookup"><span data-stu-id="0522d-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="0522d-160">EXEMPLO 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="0522d-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="0522d-161">Este exemplo ilustra como o cmdlet aceita um valor do pipeline.</span><span class="sxs-lookup"><span data-stu-id="0522d-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="0522d-162">Um id de regra e um nome de regra são transmitidos este cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0522d-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="0522d-163">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="0522d-163">Related topics</span></span>

- [<span data-ttu-id="0522d-164">Adicionar-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0522d-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="0522d-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0522d-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="0522d-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0522d-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="0522d-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="0522d-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)