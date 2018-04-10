---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: remover pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 28dbfe84827d6ccb99dce1ebb520cae66dc8c50e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="1ab09-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1ab09-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="1ab09-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1ab09-104">SYNOPSIS</span></span>

<span data-ttu-id="1ab09-105">Remove uma regra de autorização especificada do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="1ab09-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ab09-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1ab09-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="1ab09-107">Id</span><span class="sxs-lookup"><span data-stu-id="1ab09-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="1ab09-108">Regra</span><span class="sxs-lookup"><span data-stu-id="1ab09-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="1ab09-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="1ab09-109">DESCRIPTION</span></span>

<span data-ttu-id="1ab09-110">Remove uma regra de autorização especificada do acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ab09-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="1ab09-111">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="1ab09-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="1ab09-112">-Force</span><span class="sxs-lookup"><span data-stu-id="1ab09-112">-Force</span></span>

<span data-ttu-id="1ab09-113">Executa o cmdlet sem pedir confirmação.</span><span class="sxs-lookup"><span data-stu-id="1ab09-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="1ab09-114">Por predefinição, o cmdlet pede-lhe confirmação antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1ab09-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||
|-|-|
| <span data-ttu-id="1ab09-115">Aliases</span><span class="sxs-lookup"><span data-stu-id="1ab09-115">Aliases</span></span>                              | <span data-ttu-id="1ab09-116">nenhum</span><span class="sxs-lookup"><span data-stu-id="1ab09-116">none</span></span>                                 |
| <span data-ttu-id="1ab09-117">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="1ab09-117">Required?</span></span>                            | <span data-ttu-id="1ab09-118">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-118">false</span></span>                                |
| <span data-ttu-id="1ab09-119">Posição?</span><span class="sxs-lookup"><span data-stu-id="1ab09-119">Position?</span></span>                            | <span data-ttu-id="1ab09-120">com o nome</span><span class="sxs-lookup"><span data-stu-id="1ab09-120">named</span></span>                                |
| <span data-ttu-id="1ab09-121">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="1ab09-121">Default Value</span></span>                        | <span data-ttu-id="1ab09-122">nenhum</span><span class="sxs-lookup"><span data-stu-id="1ab09-122">none</span></span>                                 |
| <span data-ttu-id="1ab09-123">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="1ab09-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ab09-124">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-124">false</span></span>                                |
| <span data-ttu-id="1ab09-125">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="1ab09-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ab09-126">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="1ab09-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="1ab09-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="1ab09-128">Especifica os identificadores (IDs) de uma ou mais regras para remover.</span><span class="sxs-lookup"><span data-stu-id="1ab09-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="1ab09-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="1ab09-129">Aliases</span></span>                              | <span data-ttu-id="1ab09-130">nenhum</span><span class="sxs-lookup"><span data-stu-id="1ab09-130">none</span></span>                                 |
| <span data-ttu-id="1ab09-131">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="1ab09-131">Required?</span></span>                            | <span data-ttu-id="1ab09-132">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="1ab09-132">true</span></span>                                 |
| <span data-ttu-id="1ab09-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="1ab09-133">Position?</span></span>                            | <span data-ttu-id="1ab09-134">2</span><span class="sxs-lookup"><span data-stu-id="1ab09-134">2</span></span>                                    |
| <span data-ttu-id="1ab09-135">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="1ab09-135">Default Value</span></span>                        | <span data-ttu-id="1ab09-136">nenhum</span><span class="sxs-lookup"><span data-stu-id="1ab09-136">none</span></span>                                 |
| <span data-ttu-id="1ab09-137">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="1ab09-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ab09-138">VERDADEIRO (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="1ab09-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="1ab09-139">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="1ab09-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ab09-140">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="1ab09-141">-Regras &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="1ab09-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="1ab09-142">Especifica regras para remover.</span><span class="sxs-lookup"><span data-stu-id="1ab09-142">Specifies the rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="1ab09-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="1ab09-143">Aliases</span></span>                              | <span data-ttu-id="1ab09-144">nenhum</span><span class="sxs-lookup"><span data-stu-id="1ab09-144">none</span></span>                                 |
| <span data-ttu-id="1ab09-145">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="1ab09-145">Required?</span></span>                            | <span data-ttu-id="1ab09-146">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="1ab09-146">true</span></span>                                 |
| <span data-ttu-id="1ab09-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="1ab09-147">Position?</span></span>                            | <span data-ttu-id="1ab09-148">2</span><span class="sxs-lookup"><span data-stu-id="1ab09-148">2</span></span>                                    |
| <span data-ttu-id="1ab09-149">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="1ab09-149">Default Value</span></span>                        | <span data-ttu-id="1ab09-150">nenhum</span><span class="sxs-lookup"><span data-stu-id="1ab09-150">none</span></span>                                 |
| <span data-ttu-id="1ab09-151">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="1ab09-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ab09-152">VERDADEIRO (ByValue)</span><span class="sxs-lookup"><span data-stu-id="1ab09-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="1ab09-153">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="1ab09-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ab09-154">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="1ab09-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1ab09-155">-Confirm</span></span>

<span data-ttu-id="1ab09-156">Solicita a sua confirmação antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1ab09-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="1ab09-157">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="1ab09-157">Required?</span></span>                            | <span data-ttu-id="1ab09-158">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-158">false</span></span>                                |
| <span data-ttu-id="1ab09-159">Posição?</span><span class="sxs-lookup"><span data-stu-id="1ab09-159">Position?</span></span>                            | <span data-ttu-id="1ab09-160">com o nome</span><span class="sxs-lookup"><span data-stu-id="1ab09-160">named</span></span>                                |
| <span data-ttu-id="1ab09-161">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="1ab09-161">Default Value</span></span>                        | <span data-ttu-id="1ab09-162">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-162">false</span></span>                                |
| <span data-ttu-id="1ab09-163">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="1ab09-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ab09-164">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-164">false</span></span>                                |
| <span data-ttu-id="1ab09-165">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="1ab09-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ab09-166">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="1ab09-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1ab09-167">-WhatIf</span></span>

<span data-ttu-id="1ab09-168">Apresenta o que aconteceria mediante a execução do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1ab09-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1ab09-169">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="1ab09-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="1ab09-170">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="1ab09-170">Required?</span></span>                            | <span data-ttu-id="1ab09-171">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-171">false</span></span>                                |
| <span data-ttu-id="1ab09-172">Posição?</span><span class="sxs-lookup"><span data-stu-id="1ab09-172">Position?</span></span>                            | <span data-ttu-id="1ab09-173">com o nome</span><span class="sxs-lookup"><span data-stu-id="1ab09-173">named</span></span>                                |
| <span data-ttu-id="1ab09-174">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="1ab09-174">Default Value</span></span>                        | <span data-ttu-id="1ab09-175">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-175">false</span></span>                                |
| <span data-ttu-id="1ab09-176">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="1ab09-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1ab09-177">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-177">false</span></span>                                |
| <span data-ttu-id="1ab09-178">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="1ab09-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1ab09-179">falso</span><span class="sxs-lookup"><span data-stu-id="1ab09-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="1ab09-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="1ab09-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="1ab09-181">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="1ab09-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="1ab09-182">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1ab09-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="1ab09-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="1ab09-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="1ab09-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="1ab09-184">int\[\]</span></span>

<span data-ttu-id="1ab09-185">Este cmdlet aceita uma matriz de números inteiros ou uma matriz de objetos de PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="1ab09-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="1ab09-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="1ab09-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="1ab09-187">Este cmdlet aceita uma matriz de números inteiros ou uma matriz de objetos de PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="1ab09-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="1ab09-188">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="1ab09-188">OUTPUTS</span></span>

<span data-ttu-id="1ab09-189">Este cmdlet não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="1ab09-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="1ab09-190">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="1ab09-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="1ab09-191">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="1ab09-191">EXAMPLE 1</span></span>

<span data-ttu-id="1ab09-192">Neste exemplo remove a regra de autorização com o ID de *2*.</span><span class="sxs-lookup"><span data-stu-id="1ab09-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="1ab09-193">EXEMPLO 2 {.subHeading #example-2}</span><span class="sxs-lookup"><span data-stu-id="1ab09-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="1ab09-194">Neste exemplo remove todas as regras de autorização e é também necessária confirmação pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="1ab09-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="1ab09-195">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="1ab09-195">Related topics</span></span>

- [<span data-ttu-id="1ab09-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1ab09-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="1ab09-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1ab09-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="1ab09-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="1ab09-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="1ab09-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1ab09-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)