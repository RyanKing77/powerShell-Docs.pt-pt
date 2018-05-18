---
ms.topic: reference
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="019bc-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="019bc-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="019bc-104">RESUMO</span><span class="sxs-lookup"><span data-stu-id="019bc-104">SYNOPSIS</span></span>

<span data-ttu-id="019bc-105">Remove uma regra de autorização especificada do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="019bc-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="019bc-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="019bc-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="019bc-107">Id</span><span class="sxs-lookup"><span data-stu-id="019bc-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="019bc-108">Regra</span><span class="sxs-lookup"><span data-stu-id="019bc-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="019bc-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="019bc-109">DESCRIPTION</span></span>

<span data-ttu-id="019bc-110">Remove uma regra de autorização especificada do acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="019bc-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="019bc-111">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="019bc-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="019bc-112">-Force</span><span class="sxs-lookup"><span data-stu-id="019bc-112">-Force</span></span>

<span data-ttu-id="019bc-113">Executa o cmdlet sem pedir confirmação.</span><span class="sxs-lookup"><span data-stu-id="019bc-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="019bc-114">Por predefinição, o cmdlet pede-lhe confirmação antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="019bc-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||
|-|-|
| <span data-ttu-id="019bc-115">Aliases</span><span class="sxs-lookup"><span data-stu-id="019bc-115">Aliases</span></span>                              | <span data-ttu-id="019bc-116">nenhum</span><span class="sxs-lookup"><span data-stu-id="019bc-116">none</span></span>                                 |
| <span data-ttu-id="019bc-117">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="019bc-117">Required?</span></span>                            | <span data-ttu-id="019bc-118">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-118">false</span></span>                                |
| <span data-ttu-id="019bc-119">Posição?</span><span class="sxs-lookup"><span data-stu-id="019bc-119">Position?</span></span>                            | <span data-ttu-id="019bc-120">com o nome</span><span class="sxs-lookup"><span data-stu-id="019bc-120">named</span></span>                                |
| <span data-ttu-id="019bc-121">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="019bc-121">Default Value</span></span>                        | <span data-ttu-id="019bc-122">nenhum</span><span class="sxs-lookup"><span data-stu-id="019bc-122">none</span></span>                                 |
| <span data-ttu-id="019bc-123">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="019bc-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="019bc-124">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-124">false</span></span>                                |
| <span data-ttu-id="019bc-125">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="019bc-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="019bc-126">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="019bc-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="019bc-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="019bc-128">Especifica os identificadores (IDs) de uma ou mais regras para remover.</span><span class="sxs-lookup"><span data-stu-id="019bc-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="019bc-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="019bc-129">Aliases</span></span>                              | <span data-ttu-id="019bc-130">nenhum</span><span class="sxs-lookup"><span data-stu-id="019bc-130">none</span></span>                                 |
| <span data-ttu-id="019bc-131">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="019bc-131">Required?</span></span>                            | <span data-ttu-id="019bc-132">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="019bc-132">true</span></span>                                 |
| <span data-ttu-id="019bc-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="019bc-133">Position?</span></span>                            | <span data-ttu-id="019bc-134">2</span><span class="sxs-lookup"><span data-stu-id="019bc-134">2</span></span>                                    |
| <span data-ttu-id="019bc-135">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="019bc-135">Default Value</span></span>                        | <span data-ttu-id="019bc-136">nenhum</span><span class="sxs-lookup"><span data-stu-id="019bc-136">none</span></span>                                 |
| <span data-ttu-id="019bc-137">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="019bc-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="019bc-138">VERDADEIRO (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="019bc-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="019bc-139">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="019bc-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="019bc-140">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="019bc-141">-Regras &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="019bc-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="019bc-142">Especifica regras para remover.</span><span class="sxs-lookup"><span data-stu-id="019bc-142">Specifies the rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="019bc-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="019bc-143">Aliases</span></span>                              | <span data-ttu-id="019bc-144">nenhum</span><span class="sxs-lookup"><span data-stu-id="019bc-144">none</span></span>                                 |
| <span data-ttu-id="019bc-145">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="019bc-145">Required?</span></span>                            | <span data-ttu-id="019bc-146">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="019bc-146">true</span></span>                                 |
| <span data-ttu-id="019bc-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="019bc-147">Position?</span></span>                            | <span data-ttu-id="019bc-148">2</span><span class="sxs-lookup"><span data-stu-id="019bc-148">2</span></span>                                    |
| <span data-ttu-id="019bc-149">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="019bc-149">Default Value</span></span>                        | <span data-ttu-id="019bc-150">nenhum</span><span class="sxs-lookup"><span data-stu-id="019bc-150">none</span></span>                                 |
| <span data-ttu-id="019bc-151">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="019bc-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="019bc-152">VERDADEIRO (ByValue)</span><span class="sxs-lookup"><span data-stu-id="019bc-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="019bc-153">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="019bc-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="019bc-154">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="019bc-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="019bc-155">-Confirm</span></span>

<span data-ttu-id="019bc-156">Solicita a sua confirmação antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="019bc-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="019bc-157">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="019bc-157">Required?</span></span>                            | <span data-ttu-id="019bc-158">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-158">false</span></span>                                |
| <span data-ttu-id="019bc-159">Posição?</span><span class="sxs-lookup"><span data-stu-id="019bc-159">Position?</span></span>                            | <span data-ttu-id="019bc-160">com o nome</span><span class="sxs-lookup"><span data-stu-id="019bc-160">named</span></span>                                |
| <span data-ttu-id="019bc-161">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="019bc-161">Default Value</span></span>                        | <span data-ttu-id="019bc-162">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-162">false</span></span>                                |
| <span data-ttu-id="019bc-163">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="019bc-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="019bc-164">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-164">false</span></span>                                |
| <span data-ttu-id="019bc-165">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="019bc-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="019bc-166">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="019bc-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="019bc-167">-WhatIf</span></span>

<span data-ttu-id="019bc-168">Apresenta o que aconteceria mediante a execução do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="019bc-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="019bc-169">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="019bc-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="019bc-170">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="019bc-170">Required?</span></span>                            | <span data-ttu-id="019bc-171">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-171">false</span></span>                                |
| <span data-ttu-id="019bc-172">Posição?</span><span class="sxs-lookup"><span data-stu-id="019bc-172">Position?</span></span>                            | <span data-ttu-id="019bc-173">com o nome</span><span class="sxs-lookup"><span data-stu-id="019bc-173">named</span></span>                                |
| <span data-ttu-id="019bc-174">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="019bc-174">Default Value</span></span>                        | <span data-ttu-id="019bc-175">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-175">false</span></span>                                |
| <span data-ttu-id="019bc-176">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="019bc-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="019bc-177">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-177">false</span></span>                                |
| <span data-ttu-id="019bc-178">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="019bc-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="019bc-179">falso</span><span class="sxs-lookup"><span data-stu-id="019bc-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="019bc-180">&lt;Parâmetroscomuns&gt;</span><span class="sxs-lookup"><span data-stu-id="019bc-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="019bc-181">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="019bc-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="019bc-182">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="019bc-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="019bc-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="019bc-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="019bc-184">Int\[\]</span><span class="sxs-lookup"><span data-stu-id="019bc-184">int\[\]</span></span>

<span data-ttu-id="019bc-185">Este cmdlet aceita uma matriz de números inteiros ou uma matriz de objetos de PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="019bc-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="019bc-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="019bc-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="019bc-187">Este cmdlet aceita uma matriz de números inteiros ou uma matriz de objetos de PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="019bc-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="019bc-188">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="019bc-188">OUTPUTS</span></span>

<span data-ttu-id="019bc-189">Este cmdlet não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="019bc-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="019bc-190">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="019bc-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="019bc-191">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="019bc-191">EXAMPLE 1</span></span>

<span data-ttu-id="019bc-192">Neste exemplo remove a regra de autorização com o ID de *2*.</span><span class="sxs-lookup"><span data-stu-id="019bc-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="019bc-193">EXEMPLO 2 {.subHeading #example-2}</span><span class="sxs-lookup"><span data-stu-id="019bc-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="019bc-194">Neste exemplo remove todas as regras de autorização e é também necessária confirmação pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="019bc-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="019bc-195">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="019bc-195">Related topics</span></span>

- [<span data-ttu-id="019bc-196">Adicionar-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="019bc-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="019bc-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="019bc-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="019bc-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="019bc-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="019bc-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="019bc-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)