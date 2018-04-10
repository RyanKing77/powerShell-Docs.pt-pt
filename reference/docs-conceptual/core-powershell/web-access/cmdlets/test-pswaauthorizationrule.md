---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: teste pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: ed6d56b2f3c4ee4ac410cdaadda312bffe506ee9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="f65da-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f65da-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="f65da-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f65da-104">SYNOPSIS</span></span>

<span data-ttu-id="f65da-105">Verifica se existe uma regra para um utilizador especificado, o computador ou o ponto final.</span><span class="sxs-lookup"><span data-stu-id="f65da-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="f65da-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f65da-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="f65da-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="f65da-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="f65da-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="f65da-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="f65da-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="f65da-109">DESCRIPTION</span></span>

<span data-ttu-id="f65da-110">O **Test-PswaAuthorizationRule** cmdlet verifica se existe uma regra para um utilizador especificado, o computador ou o ponto final.</span><span class="sxs-lookup"><span data-stu-id="f65da-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="f65da-111">Este cmdlet também pode ser utilizado para testar as regras de autorização, para validar que um pedido de acesso de utilizador, computador ou ponto final específico está autorizado.</span><span class="sxs-lookup"><span data-stu-id="f65da-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="f65da-112">Por predefinição, este cmdlet avalia todas as regras no ficheiro de autorização.</span><span class="sxs-lookup"><span data-stu-id="f65da-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="f65da-113">No entanto, pode especificar um subconjunto de regras para testar.</span><span class="sxs-lookup"><span data-stu-id="f65da-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="f65da-114">Pode utilizar este cmdlet para ajudar a resolver problemas de falhas de autenticação.</span><span class="sxs-lookup"><span data-stu-id="f65da-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="f65da-115">Os parâmetros para este cmdlet correspondem aos campos da página de início de sessão o acesso Web do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="f65da-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="f65da-116">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="f65da-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="f65da-117">-ComputerName &lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="f65da-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="f65da-118">Especifica o nome do computador para testar.</span><span class="sxs-lookup"><span data-stu-id="f65da-118">Specifies the name of the computer to test.</span></span>

|||
|-|-|
| <span data-ttu-id="f65da-119">Aliases</span><span class="sxs-lookup"><span data-stu-id="f65da-119">Aliases</span></span>                              | <span data-ttu-id="f65da-120">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-120">none</span></span>                                 |
| <span data-ttu-id="f65da-121">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="f65da-121">Required?</span></span>                            | <span data-ttu-id="f65da-122">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="f65da-122">true</span></span>                                 |
| <span data-ttu-id="f65da-123">Posição?</span><span class="sxs-lookup"><span data-stu-id="f65da-123">Position?</span></span>                            | <span data-ttu-id="f65da-124">2</span><span class="sxs-lookup"><span data-stu-id="f65da-124">2</span></span>                                    |
| <span data-ttu-id="f65da-125">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="f65da-125">Default Value</span></span>                        | <span data-ttu-id="f65da-126">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-126">none</span></span>                                 |
| <span data-ttu-id="f65da-127">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="f65da-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f65da-128">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-128">false</span></span>                                |
| <span data-ttu-id="f65da-129">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="f65da-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f65da-130">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="f65da-131">-ConfigurationName &lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="f65da-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="f65da-132">Especifica o nome da configuração de sessão do Windows PowerShell, também conhecido como o ponto final ou o espaço de execução, para testar.</span><span class="sxs-lookup"><span data-stu-id="f65da-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||
|-|-|
| <span data-ttu-id="f65da-133">Aliases</span><span class="sxs-lookup"><span data-stu-id="f65da-133">Aliases</span></span>                              | <span data-ttu-id="f65da-134">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-134">none</span></span>                                 |
| <span data-ttu-id="f65da-135">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="f65da-135">Required?</span></span>                            | <span data-ttu-id="f65da-136">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-136">false</span></span>                                |
| <span data-ttu-id="f65da-137">Posição?</span><span class="sxs-lookup"><span data-stu-id="f65da-137">Position?</span></span>                            | <span data-ttu-id="f65da-138">3</span><span class="sxs-lookup"><span data-stu-id="f65da-138">3</span></span>                                    |
| <span data-ttu-id="f65da-139">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="f65da-139">Default Value</span></span>                        | <span data-ttu-id="f65da-140">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-140">none</span></span>                                 |
| <span data-ttu-id="f65da-141">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="f65da-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f65da-142">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-142">false</span></span>                                |
| <span data-ttu-id="f65da-143">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="f65da-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f65da-144">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="f65da-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="f65da-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="f65da-146">Especifica a ligação de URI para testar.</span><span class="sxs-lookup"><span data-stu-id="f65da-146">Specifies the connection URI to test.</span></span>

|||
|-|-|
| <span data-ttu-id="f65da-147">Aliases</span><span class="sxs-lookup"><span data-stu-id="f65da-147">Aliases</span></span>                              | <span data-ttu-id="f65da-148">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-148">none</span></span>                                 |
| <span data-ttu-id="f65da-149">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="f65da-149">Required?</span></span>                            | <span data-ttu-id="f65da-150">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="f65da-150">true</span></span>                                 |
| <span data-ttu-id="f65da-151">Posição?</span><span class="sxs-lookup"><span data-stu-id="f65da-151">Position?</span></span>                            | <span data-ttu-id="f65da-152">2</span><span class="sxs-lookup"><span data-stu-id="f65da-152">2</span></span>                                    |
| <span data-ttu-id="f65da-153">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="f65da-153">Default Value</span></span>                        | <span data-ttu-id="f65da-154">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-154">none</span></span>                                 |
| <span data-ttu-id="f65da-155">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="f65da-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f65da-156">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-156">false</span></span>                                |
| <span data-ttu-id="f65da-157">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="f65da-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f65da-158">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="f65da-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="f65da-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="f65da-160">Especifica um **PSCredential** objeto para uma conta de utilizador que pretende utilizar para testar as regras de autorização de acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f65da-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="f65da-161">Se não adicionar este parâmetro, o cmdlet utiliza a conta de utilizador atualmente com sessão iniciada.</span><span class="sxs-lookup"><span data-stu-id="f65da-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="f65da-162">Para obter um **PSCredential** objeto, que é necessário para testar as regras de autorização remotamente, execute o [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f65da-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="f65da-163">Aliases</span><span class="sxs-lookup"><span data-stu-id="f65da-163">Aliases</span></span>                              | <span data-ttu-id="f65da-164">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-164">none</span></span>                                 |
| <span data-ttu-id="f65da-165">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="f65da-165">Required?</span></span>                            | <span data-ttu-id="f65da-166">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-166">false</span></span>                                |
| <span data-ttu-id="f65da-167">Posição?</span><span class="sxs-lookup"><span data-stu-id="f65da-167">Position?</span></span>                            | <span data-ttu-id="f65da-168">com o nome</span><span class="sxs-lookup"><span data-stu-id="f65da-168">named</span></span>                                |
| <span data-ttu-id="f65da-169">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="f65da-169">Default Value</span></span>                        | <span data-ttu-id="f65da-170">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-170">none</span></span>                                 |
| <span data-ttu-id="f65da-171">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="f65da-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f65da-172">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-172">false</span></span>                                |
| <span data-ttu-id="f65da-173">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="f65da-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f65da-174">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="f65da-175">-Regras &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="f65da-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="f65da-176">Especifica um subconjunto de regras para testar.</span><span class="sxs-lookup"><span data-stu-id="f65da-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="f65da-177">Se este parâmetro não for especificado, este cmdlet testes relativamente a todas as regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="f65da-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="f65da-178">Aliases</span><span class="sxs-lookup"><span data-stu-id="f65da-178">Aliases</span></span>                              | <span data-ttu-id="f65da-179">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-179">none</span></span>                                 |
| <span data-ttu-id="f65da-180">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="f65da-180">Required?</span></span>                            | <span data-ttu-id="f65da-181">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-181">false</span></span>                                |
| <span data-ttu-id="f65da-182">Posição?</span><span class="sxs-lookup"><span data-stu-id="f65da-182">Position?</span></span>                            | <span data-ttu-id="f65da-183">com o nome</span><span class="sxs-lookup"><span data-stu-id="f65da-183">named</span></span>                                |
| <span data-ttu-id="f65da-184">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="f65da-184">Default Value</span></span>                        | <span data-ttu-id="f65da-185">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-185">none</span></span>                                 |
| <span data-ttu-id="f65da-186">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="f65da-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f65da-187">VERDADEIRO (ByValue)</span><span class="sxs-lookup"><span data-stu-id="f65da-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="f65da-188">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="f65da-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f65da-189">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="f65da-190">-UserName &lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="f65da-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="f65da-191">Especifica o nome do utilizador para testar.</span><span class="sxs-lookup"><span data-stu-id="f65da-191">Specifies the name of the user to test.</span></span>

|||
|-|-|
| <span data-ttu-id="f65da-192">Aliases</span><span class="sxs-lookup"><span data-stu-id="f65da-192">Aliases</span></span>                              | <span data-ttu-id="f65da-193">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-193">none</span></span>                                 |
| <span data-ttu-id="f65da-194">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="f65da-194">Required?</span></span>                            | <span data-ttu-id="f65da-195">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="f65da-195">true</span></span>                                 |
| <span data-ttu-id="f65da-196">Posição?</span><span class="sxs-lookup"><span data-stu-id="f65da-196">Position?</span></span>                            | <span data-ttu-id="f65da-197">1</span><span class="sxs-lookup"><span data-stu-id="f65da-197">1</span></span>                                    |
| <span data-ttu-id="f65da-198">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="f65da-198">Default Value</span></span>                        | <span data-ttu-id="f65da-199">nenhum</span><span class="sxs-lookup"><span data-stu-id="f65da-199">none</span></span>                                 |
| <span data-ttu-id="f65da-200">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="f65da-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f65da-201">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-201">false</span></span>                                |
| <span data-ttu-id="f65da-202">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="f65da-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f65da-203">falso</span><span class="sxs-lookup"><span data-stu-id="f65da-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="f65da-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="f65da-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="f65da-205">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="f65da-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="f65da-206">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f65da-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="f65da-207">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="f65da-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="f65da-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="f65da-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="f65da-209">Este cmdlet aceita uma matriz de objetos de PswaAuthorizationRule como entrada.</span><span class="sxs-lookup"><span data-stu-id="f65da-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="f65da-210">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="f65da-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="f65da-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="f65da-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="f65da-212">Este cmdlet produz uma matriz de objetos de PswaAuthorizationRule como saída.</span><span class="sxs-lookup"><span data-stu-id="f65da-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="f65da-213">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="f65da-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="f65da-214">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="f65da-214">EXAMPLE 1</span></span>

<span data-ttu-id="f65da-215">Neste exemplo testa todas as regras de autorização para apresentar todas as regras que permitem ao utilizador *contoso\\mhanson* para ligar ao computador *srv2* e utilize uma sessão do Windows PowerShell configuração com o nome *testar*.</span><span class="sxs-lookup"><span data-stu-id="f65da-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="f65da-216">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="f65da-216">EXAMPLE 2</span></span>

<span data-ttu-id="f65da-217">Este testes de exemplo todas as regras de autorização para verificar as regras de autorização aplicam ao utilizador *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="f65da-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="f65da-218">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="f65da-218">Related topics</span></span>

- [<span data-ttu-id="f65da-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f65da-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="f65da-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f65da-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="f65da-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="f65da-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="f65da-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f65da-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)