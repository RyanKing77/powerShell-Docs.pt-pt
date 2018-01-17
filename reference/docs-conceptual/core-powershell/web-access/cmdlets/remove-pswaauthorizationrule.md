---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 2016-12-12
title: remover pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 4d039e7e00f87bc7aebb89217251edbbb5c3f5be
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="d4ced-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d4ced-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="d4ced-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d4ced-104">SYNOPSIS</span></span>

<span data-ttu-id="d4ced-105">Remove uma regra de autorização especificada do Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="d4ced-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4ced-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d4ced-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="d4ced-107">Id</span><span class="sxs-lookup"><span data-stu-id="d4ced-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="d4ced-108">Regra</span><span class="sxs-lookup"><span data-stu-id="d4ced-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="d4ced-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="d4ced-109">DESCRIPTION</span></span>

<span data-ttu-id="d4ced-110">Remove uma regra de autorização especificada do acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4ced-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="d4ced-111">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="d4ced-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="d4ced-112">-Force</span><span class="sxs-lookup"><span data-stu-id="d4ced-112">-Force</span></span>

<span data-ttu-id="d4ced-113">Executa o cmdlet sem pedir confirmação.</span><span class="sxs-lookup"><span data-stu-id="d4ced-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="d4ced-114">Por predefinição, o cmdlet pede-lhe confirmação antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d4ced-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="d4ced-115">Aliases</span><span class="sxs-lookup"><span data-stu-id="d4ced-115">Aliases</span></span>                              | <span data-ttu-id="d4ced-116">nenhum</span><span class="sxs-lookup"><span data-stu-id="d4ced-116">none</span></span>                                 |
| <span data-ttu-id="d4ced-117">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="d4ced-117">Required?</span></span>                            | <span data-ttu-id="d4ced-118">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-118">false</span></span>                                |
| <span data-ttu-id="d4ced-119">Posição?</span><span class="sxs-lookup"><span data-stu-id="d4ced-119">Position?</span></span>                            | <span data-ttu-id="d4ced-120">com o nome</span><span class="sxs-lookup"><span data-stu-id="d4ced-120">named</span></span>                                |
| <span data-ttu-id="d4ced-121">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="d4ced-121">Default Value</span></span>                        | <span data-ttu-id="d4ced-122">nenhum</span><span class="sxs-lookup"><span data-stu-id="d4ced-122">none</span></span>                                 |
| <span data-ttu-id="d4ced-123">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="d4ced-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="d4ced-124">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-124">false</span></span>                                |
| <span data-ttu-id="d4ced-125">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="d4ced-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="d4ced-126">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="d4ced-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="d4ced-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="d4ced-128">Especifica os identificadores (IDs) de uma ou mais regras para remover.</span><span class="sxs-lookup"><span data-stu-id="d4ced-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="d4ced-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="d4ced-129">Aliases</span></span>                              | <span data-ttu-id="d4ced-130">nenhum</span><span class="sxs-lookup"><span data-stu-id="d4ced-130">none</span></span>                                 |
| <span data-ttu-id="d4ced-131">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="d4ced-131">Required?</span></span>                            | <span data-ttu-id="d4ced-132">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="d4ced-132">true</span></span>                                 |
| <span data-ttu-id="d4ced-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="d4ced-133">Position?</span></span>                            | <span data-ttu-id="d4ced-134">2</span><span class="sxs-lookup"><span data-stu-id="d4ced-134">2</span></span>                                    |
| <span data-ttu-id="d4ced-135">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="d4ced-135">Default Value</span></span>                        | <span data-ttu-id="d4ced-136">nenhum</span><span class="sxs-lookup"><span data-stu-id="d4ced-136">none</span></span>                                 |
| <span data-ttu-id="d4ced-137">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="d4ced-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="d4ced-138">VERDADEIRO (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="d4ced-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="d4ced-139">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="d4ced-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="d4ced-140">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="d4ced-141">-Regras &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="d4ced-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="d4ced-142">Especifica regras para remover.</span><span class="sxs-lookup"><span data-stu-id="d4ced-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="d4ced-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="d4ced-143">Aliases</span></span>                              | <span data-ttu-id="d4ced-144">nenhum</span><span class="sxs-lookup"><span data-stu-id="d4ced-144">none</span></span>                                 |
| <span data-ttu-id="d4ced-145">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="d4ced-145">Required?</span></span>                            | <span data-ttu-id="d4ced-146">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="d4ced-146">true</span></span>                                 |
| <span data-ttu-id="d4ced-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="d4ced-147">Position?</span></span>                            | <span data-ttu-id="d4ced-148">2</span><span class="sxs-lookup"><span data-stu-id="d4ced-148">2</span></span>                                    |
| <span data-ttu-id="d4ced-149">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="d4ced-149">Default Value</span></span>                        | <span data-ttu-id="d4ced-150">nenhum</span><span class="sxs-lookup"><span data-stu-id="d4ced-150">none</span></span>                                 |
| <span data-ttu-id="d4ced-151">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="d4ced-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="d4ced-152">VERDADEIRO (ByValue)</span><span class="sxs-lookup"><span data-stu-id="d4ced-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="d4ced-153">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="d4ced-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="d4ced-154">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="d4ced-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d4ced-155">-Confirm</span></span>

<span data-ttu-id="d4ced-156">Solicita a sua confirmação antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d4ced-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="d4ced-157">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="d4ced-157">Required?</span></span>                            | <span data-ttu-id="d4ced-158">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-158">false</span></span>                                |
| <span data-ttu-id="d4ced-159">Posição?</span><span class="sxs-lookup"><span data-stu-id="d4ced-159">Position?</span></span>                            | <span data-ttu-id="d4ced-160">com o nome</span><span class="sxs-lookup"><span data-stu-id="d4ced-160">named</span></span>                                |
| <span data-ttu-id="d4ced-161">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="d4ced-161">Default Value</span></span>                        | <span data-ttu-id="d4ced-162">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-162">false</span></span>                                |
| <span data-ttu-id="d4ced-163">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="d4ced-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="d4ced-164">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-164">false</span></span>                                |
| <span data-ttu-id="d4ced-165">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="d4ced-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="d4ced-166">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="d4ced-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d4ced-167">-WhatIf</span></span>

<span data-ttu-id="d4ced-168">Apresenta o que aconteceria mediante a execução do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d4ced-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d4ced-169">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="d4ced-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="d4ced-170">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="d4ced-170">Required?</span></span>                            | <span data-ttu-id="d4ced-171">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-171">false</span></span>                                |
| <span data-ttu-id="d4ced-172">Posição?</span><span class="sxs-lookup"><span data-stu-id="d4ced-172">Position?</span></span>                            | <span data-ttu-id="d4ced-173">com o nome</span><span class="sxs-lookup"><span data-stu-id="d4ced-173">named</span></span>                                |
| <span data-ttu-id="d4ced-174">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="d4ced-174">Default Value</span></span>                        | <span data-ttu-id="d4ced-175">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-175">false</span></span>                                |
| <span data-ttu-id="d4ced-176">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="d4ced-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="d4ced-177">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-177">false</span></span>                                |
| <span data-ttu-id="d4ced-178">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="d4ced-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="d4ced-179">falso</span><span class="sxs-lookup"><span data-stu-id="d4ced-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="d4ced-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="d4ced-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="d4ced-181">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="d4ced-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="d4ced-182">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d4ced-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="d4ced-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="d4ced-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="d4ced-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="d4ced-184">int\[\]</span></span>

<span data-ttu-id="d4ced-185">Este cmdlet aceita uma matriz de números inteiros ou uma matriz de objetos de PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="d4ced-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="d4ced-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="d4ced-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="d4ced-187">Este cmdlet aceita uma matriz de números inteiros ou uma matriz de objetos de PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="d4ced-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="d4ced-188">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="d4ced-188">OUTPUTS</span></span>

<span data-ttu-id="d4ced-189">Este cmdlet não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="d4ced-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="d4ced-190">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="d4ced-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="d4ced-191">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="d4ced-191">EXAMPLE 1</span></span>

<span data-ttu-id="d4ced-192">Neste exemplo remove a regra de autorização com o ID de *2*.</span><span class="sxs-lookup"><span data-stu-id="d4ced-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="d4ced-193">EXEMPLO 2 {.subHeading #example-2}</span><span class="sxs-lookup"><span data-stu-id="d4ced-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="d4ced-194">Neste exemplo remove todas as regras de autorização e é também necessária confirmação pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="d4ced-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="d4ced-195">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="d4ced-195">Related topics</span></span>

- [<span data-ttu-id="d4ced-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d4ced-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="d4ced-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d4ced-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="d4ced-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="d4ced-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="d4ced-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d4ced-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
