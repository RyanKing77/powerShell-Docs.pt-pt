---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 2016-12-12
title: teste pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="24bb2-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="24bb2-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="24bb2-104">RESUMO</span><span class="sxs-lookup"><span data-stu-id="24bb2-104">SYNOPSIS</span></span>

<span data-ttu-id="24bb2-105">Verifica se existe uma regra para um utilizador especificado, o computador ou o ponto final.</span><span class="sxs-lookup"><span data-stu-id="24bb2-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="24bb2-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="24bb2-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="24bb2-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="24bb2-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="24bb2-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="24bb2-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="24bb2-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="24bb2-109">DESCRIPTION</span></span>

<span data-ttu-id="24bb2-110">O **Test-PswaAuthorizationRule** cmdlet verifica se existe uma regra para um utilizador especificado, o computador ou o ponto final.</span><span class="sxs-lookup"><span data-stu-id="24bb2-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="24bb2-111">Este cmdlet também pode ser utilizado para testar as regras de autorização, para validar que um pedido de acesso de utilizador, computador ou ponto final específico está autorizado.</span><span class="sxs-lookup"><span data-stu-id="24bb2-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="24bb2-112">Por predefinição, este cmdlet avalia todas as regras no ficheiro de autorização.</span><span class="sxs-lookup"><span data-stu-id="24bb2-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="24bb2-113">No entanto, pode especificar um subconjunto de regras para testar.</span><span class="sxs-lookup"><span data-stu-id="24bb2-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="24bb2-114">Pode utilizar este cmdlet para ajudar a resolver problemas de falhas de autenticação.</span><span class="sxs-lookup"><span data-stu-id="24bb2-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="24bb2-115">Os parâmetros para este cmdlet correspondem aos campos da página de início de sessão o acesso Web do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="24bb2-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="24bb2-116">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="24bb2-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="24bb2-117">-ComputerName &lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="24bb2-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="24bb2-118">Especifica o nome do computador para testar.</span><span class="sxs-lookup"><span data-stu-id="24bb2-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="24bb2-119">Aliases</span><span class="sxs-lookup"><span data-stu-id="24bb2-119">Aliases</span></span>                              | <span data-ttu-id="24bb2-120">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-120">none</span></span>                                 |
| <span data-ttu-id="24bb2-121">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="24bb2-121">Required?</span></span>                            | <span data-ttu-id="24bb2-122">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="24bb2-122">true</span></span>                                 |
| <span data-ttu-id="24bb2-123">Posição?</span><span class="sxs-lookup"><span data-stu-id="24bb2-123">Position?</span></span>                            | <span data-ttu-id="24bb2-124">2</span><span class="sxs-lookup"><span data-stu-id="24bb2-124">2</span></span>                                    |
| <span data-ttu-id="24bb2-125">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="24bb2-125">Default Value</span></span>                        | <span data-ttu-id="24bb2-126">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-126">none</span></span>                                 |
| <span data-ttu-id="24bb2-127">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="24bb2-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="24bb2-128">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-128">false</span></span>                                |
| <span data-ttu-id="24bb2-129">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="24bb2-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="24bb2-130">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="24bb2-131">-ConfigurationName &lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="24bb2-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="24bb2-132">Especifica o nome da configuração de sessão do Windows PowerShell, também conhecido como o ponto final ou o espaço de execução, para testar.</span><span class="sxs-lookup"><span data-stu-id="24bb2-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="24bb2-133">Aliases</span><span class="sxs-lookup"><span data-stu-id="24bb2-133">Aliases</span></span>                              | <span data-ttu-id="24bb2-134">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-134">none</span></span>                                 |
| <span data-ttu-id="24bb2-135">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="24bb2-135">Required?</span></span>                            | <span data-ttu-id="24bb2-136">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-136">false</span></span>                                |
| <span data-ttu-id="24bb2-137">Posição?</span><span class="sxs-lookup"><span data-stu-id="24bb2-137">Position?</span></span>                            | <span data-ttu-id="24bb2-138">3</span><span class="sxs-lookup"><span data-stu-id="24bb2-138">3</span></span>                                    |
| <span data-ttu-id="24bb2-139">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="24bb2-139">Default Value</span></span>                        | <span data-ttu-id="24bb2-140">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-140">none</span></span>                                 |
| <span data-ttu-id="24bb2-141">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="24bb2-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="24bb2-142">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-142">false</span></span>                                |
| <span data-ttu-id="24bb2-143">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="24bb2-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="24bb2-144">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="24bb2-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="24bb2-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="24bb2-146">Especifica a ligação de URI para testar.</span><span class="sxs-lookup"><span data-stu-id="24bb2-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="24bb2-147">Aliases</span><span class="sxs-lookup"><span data-stu-id="24bb2-147">Aliases</span></span>                              | <span data-ttu-id="24bb2-148">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-148">none</span></span>                                 |
| <span data-ttu-id="24bb2-149">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="24bb2-149">Required?</span></span>                            | <span data-ttu-id="24bb2-150">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="24bb2-150">true</span></span>                                 |
| <span data-ttu-id="24bb2-151">Posição?</span><span class="sxs-lookup"><span data-stu-id="24bb2-151">Position?</span></span>                            | <span data-ttu-id="24bb2-152">2</span><span class="sxs-lookup"><span data-stu-id="24bb2-152">2</span></span>                                    |
| <span data-ttu-id="24bb2-153">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="24bb2-153">Default Value</span></span>                        | <span data-ttu-id="24bb2-154">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-154">none</span></span>                                 |
| <span data-ttu-id="24bb2-155">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="24bb2-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="24bb2-156">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-156">false</span></span>                                |
| <span data-ttu-id="24bb2-157">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="24bb2-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="24bb2-158">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="24bb2-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="24bb2-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="24bb2-160">Especifica um **PSCredential** objeto para uma conta de utilizador que pretende utilizar para testar as regras de autorização de acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24bb2-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="24bb2-161">Se não adicionar este parâmetro, o cmdlet utiliza a conta de utilizador atualmente com sessão iniciada.</span><span class="sxs-lookup"><span data-stu-id="24bb2-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="24bb2-162">Para obter um **PSCredential** objeto, que é necessário para testar as regras de autorização remotamente, execute o [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24bb2-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="24bb2-163">Aliases</span><span class="sxs-lookup"><span data-stu-id="24bb2-163">Aliases</span></span>                              | <span data-ttu-id="24bb2-164">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-164">none</span></span>                                 |
| <span data-ttu-id="24bb2-165">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="24bb2-165">Required?</span></span>                            | <span data-ttu-id="24bb2-166">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-166">false</span></span>                                |
| <span data-ttu-id="24bb2-167">Posição?</span><span class="sxs-lookup"><span data-stu-id="24bb2-167">Position?</span></span>                            | <span data-ttu-id="24bb2-168">com o nome</span><span class="sxs-lookup"><span data-stu-id="24bb2-168">named</span></span>                                |
| <span data-ttu-id="24bb2-169">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="24bb2-169">Default Value</span></span>                        | <span data-ttu-id="24bb2-170">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-170">none</span></span>                                 |
| <span data-ttu-id="24bb2-171">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="24bb2-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="24bb2-172">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-172">false</span></span>                                |
| <span data-ttu-id="24bb2-173">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="24bb2-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="24bb2-174">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="24bb2-175">-Regras &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="24bb2-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="24bb2-176">Especifica um subconjunto de regras para testar.</span><span class="sxs-lookup"><span data-stu-id="24bb2-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="24bb2-177">Se este parâmetro não for especificado, este cmdlet testes relativamente a todas as regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="24bb2-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="24bb2-178">Aliases</span><span class="sxs-lookup"><span data-stu-id="24bb2-178">Aliases</span></span>                              | <span data-ttu-id="24bb2-179">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-179">none</span></span>                                 |
| <span data-ttu-id="24bb2-180">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="24bb2-180">Required?</span></span>                            | <span data-ttu-id="24bb2-181">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-181">false</span></span>                                |
| <span data-ttu-id="24bb2-182">Posição?</span><span class="sxs-lookup"><span data-stu-id="24bb2-182">Position?</span></span>                            | <span data-ttu-id="24bb2-183">com o nome</span><span class="sxs-lookup"><span data-stu-id="24bb2-183">named</span></span>                                |
| <span data-ttu-id="24bb2-184">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="24bb2-184">Default Value</span></span>                        | <span data-ttu-id="24bb2-185">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-185">none</span></span>                                 |
| <span data-ttu-id="24bb2-186">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="24bb2-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="24bb2-187">VERDADEIRO (ByValue)</span><span class="sxs-lookup"><span data-stu-id="24bb2-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="24bb2-188">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="24bb2-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="24bb2-189">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="24bb2-190">-UserName &lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="24bb2-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="24bb2-191">Especifica o nome do utilizador para testar.</span><span class="sxs-lookup"><span data-stu-id="24bb2-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="24bb2-192">Aliases</span><span class="sxs-lookup"><span data-stu-id="24bb2-192">Aliases</span></span>                              | <span data-ttu-id="24bb2-193">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-193">none</span></span>                                 |
| <span data-ttu-id="24bb2-194">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="24bb2-194">Required?</span></span>                            | <span data-ttu-id="24bb2-195">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="24bb2-195">true</span></span>                                 |
| <span data-ttu-id="24bb2-196">Posição?</span><span class="sxs-lookup"><span data-stu-id="24bb2-196">Position?</span></span>                            | <span data-ttu-id="24bb2-197">1</span><span class="sxs-lookup"><span data-stu-id="24bb2-197">1</span></span>                                    |
| <span data-ttu-id="24bb2-198">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="24bb2-198">Default Value</span></span>                        | <span data-ttu-id="24bb2-199">nenhum</span><span class="sxs-lookup"><span data-stu-id="24bb2-199">none</span></span>                                 |
| <span data-ttu-id="24bb2-200">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="24bb2-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="24bb2-201">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-201">false</span></span>                                |
| <span data-ttu-id="24bb2-202">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="24bb2-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="24bb2-203">falso</span><span class="sxs-lookup"><span data-stu-id="24bb2-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="24bb2-204">&lt;Parâmetroscomuns&gt;</span><span class="sxs-lookup"><span data-stu-id="24bb2-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="24bb2-205">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="24bb2-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="24bb2-206">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="24bb2-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="24bb2-207">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="24bb2-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="24bb2-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="24bb2-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="24bb2-209">Este cmdlet aceita uma matriz de objetos de PswaAuthorizationRule como entrada.</span><span class="sxs-lookup"><span data-stu-id="24bb2-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="24bb2-210">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="24bb2-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="24bb2-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="24bb2-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="24bb2-212">Este cmdlet produz uma matriz de objetos de PswaAuthorizationRule como saída.</span><span class="sxs-lookup"><span data-stu-id="24bb2-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="24bb2-213">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="24bb2-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="24bb2-214">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="24bb2-214">EXAMPLE 1</span></span>

<span data-ttu-id="24bb2-215">Neste exemplo testa todas as regras de autorização para apresentar todas as regras que permitem ao utilizador *contoso\\mhanson* para ligar ao computador *srv2* e utilize uma sessão do Windows PowerShell configuração com o nome *testar*.</span><span class="sxs-lookup"><span data-stu-id="24bb2-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="24bb2-216">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="24bb2-216">EXAMPLE 2</span></span>

<span data-ttu-id="24bb2-217">Este testes de exemplo todas as regras de autorização para verificar as regras de autorização aplicam ao utilizador *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="24bb2-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="24bb2-218">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="24bb2-218">Related topics</span></span>

- [<span data-ttu-id="24bb2-219">Adicionar-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="24bb2-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="24bb2-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="24bb2-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="24bb2-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="24bb2-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="24bb2-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="24bb2-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
