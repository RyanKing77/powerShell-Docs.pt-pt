---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 2016-12-12
title: instalar pswawebapplication
ms.technology: powershell
ms.openlocfilehash: a608a6272d3eae56ccf808b9d94525ca39df50cb
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="2b74e-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="2b74e-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="2b74e-104">RESUMO</span><span class="sxs-lookup"><span data-stu-id="2b74e-104">SYNOPSIS</span></span>

<span data-ttu-id="2b74e-105">Configura a aplicação web do Windows PowerShell® Web Access no IIS.</span><span class="sxs-lookup"><span data-stu-id="2b74e-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b74e-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="2b74e-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="2b74e-107">Predefinido</span><span class="sxs-lookup"><span data-stu-id="2b74e-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="2b74e-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="2b74e-108">DESCRIPTION</span></span>

<span data-ttu-id="2b74e-109">O **Install-PswaWebApplication** cmdlet configura aplicação web de acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b74e-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="2b74e-110">Este cmdlet instala a aplicação web, associa-o com um web site e, opcionalmente, cria um teste SSL certificado, utilizando o **useTestCertificate** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2b74e-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="2b74e-111">Segurança de administradores de web de motivos não devem utilizar um certificado de teste para ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="2b74e-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="2b74e-112">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="2b74e-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="2b74e-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="2b74e-113">-UseTestCertificate</span></span>

<span data-ttu-id="2b74e-114">Especifica que é criado um certificado de teste.</span><span class="sxs-lookup"><span data-stu-id="2b74e-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="2b74e-115">Se este parâmetro estiver definido como VERDADEIRO, então este cmdlet cria um certificado de teste e configura a aplicação web de acesso Web Windows PowerShell para utilizar o certificado para pedidos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2b74e-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="2b74e-116">Se este parâmetro estiver definido como FALSO, não é criado nenhum certificado ou o enlace.</span><span class="sxs-lookup"><span data-stu-id="2b74e-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="2b74e-117">Defina este valor como FALSO se outro certificado é utilizado para acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b74e-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||  
|-|-|
| <span data-ttu-id="2b74e-118">Aliases</span><span class="sxs-lookup"><span data-stu-id="2b74e-118">Aliases</span></span>                              | <span data-ttu-id="2b74e-119">nenhum</span><span class="sxs-lookup"><span data-stu-id="2b74e-119">none</span></span>                                 |
| <span data-ttu-id="2b74e-120">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="2b74e-120">Required?</span></span>                            | <span data-ttu-id="2b74e-121">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-121">false</span></span>                                |
| <span data-ttu-id="2b74e-122">Posição?</span><span class="sxs-lookup"><span data-stu-id="2b74e-122">Position?</span></span>                            | <span data-ttu-id="2b74e-123">com o nome</span><span class="sxs-lookup"><span data-stu-id="2b74e-123">named</span></span>                                |
| <span data-ttu-id="2b74e-124">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="2b74e-124">Default Value</span></span>                        | <span data-ttu-id="2b74e-125">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="2b74e-125">true</span></span>                                 |
| <span data-ttu-id="2b74e-126">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="2b74e-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2b74e-127">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-127">false</span></span>                                |
| <span data-ttu-id="2b74e-128">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="2b74e-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2b74e-129">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="2b74e-130">-WebApplicationName&lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="2b74e-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="2b74e-131">Especifica o nome da sua aplicação web.</span><span class="sxs-lookup"><span data-stu-id="2b74e-131">Specifies the name for your web application.</span></span> <span data-ttu-id="2b74e-132">Isto é apresentado como a última parte do URL de acesso Web do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b74e-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||  
|-|-|
| <span data-ttu-id="2b74e-133">Aliases</span><span class="sxs-lookup"><span data-stu-id="2b74e-133">Aliases</span></span>                              | <span data-ttu-id="2b74e-134">nenhum</span><span class="sxs-lookup"><span data-stu-id="2b74e-134">none</span></span>                                 |
| <span data-ttu-id="2b74e-135">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="2b74e-135">Required?</span></span>                            | <span data-ttu-id="2b74e-136">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-136">false</span></span>                                |
| <span data-ttu-id="2b74e-137">Posição?</span><span class="sxs-lookup"><span data-stu-id="2b74e-137">Position?</span></span>                            | <span data-ttu-id="2b74e-138">1</span><span class="sxs-lookup"><span data-stu-id="2b74e-138">1</span></span>                                    |
| <span data-ttu-id="2b74e-139">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="2b74e-139">Default Value</span></span>                        | <span data-ttu-id="2b74e-140">pswa</span><span class="sxs-lookup"><span data-stu-id="2b74e-140">pswa</span></span>                                 |
| <span data-ttu-id="2b74e-141">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="2b74e-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2b74e-142">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-142">false</span></span>                                |
| <span data-ttu-id="2b74e-143">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="2b74e-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2b74e-144">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="2b74e-145">-WebSiteName&lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="2b74e-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="2b74e-146">Especifica o nome do site do servidor Web (IIS) em que pretende instalar esta aplicação web do acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b74e-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||  
|-|-|
| <span data-ttu-id="2b74e-147">Aliases</span><span class="sxs-lookup"><span data-stu-id="2b74e-147">Aliases</span></span>                              | <span data-ttu-id="2b74e-148">nenhum</span><span class="sxs-lookup"><span data-stu-id="2b74e-148">none</span></span>                                 |
| <span data-ttu-id="2b74e-149">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="2b74e-149">Required?</span></span>                            | <span data-ttu-id="2b74e-150">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-150">false</span></span>                                |
| <span data-ttu-id="2b74e-151">Posição?</span><span class="sxs-lookup"><span data-stu-id="2b74e-151">Position?</span></span>                            | <span data-ttu-id="2b74e-152">com o nome</span><span class="sxs-lookup"><span data-stu-id="2b74e-152">named</span></span>                                |
| <span data-ttu-id="2b74e-153">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="2b74e-153">Default Value</span></span>                        | <span data-ttu-id="2b74e-154">Web Site predefinido</span><span class="sxs-lookup"><span data-stu-id="2b74e-154">Default Web Site</span></span>                     |
| <span data-ttu-id="2b74e-155">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="2b74e-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2b74e-156">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-156">false</span></span>                                |
| <span data-ttu-id="2b74e-157">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="2b74e-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2b74e-158">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="2b74e-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2b74e-159">-Confirm</span></span>

<span data-ttu-id="2b74e-160">Solicita a sua confirmação antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b74e-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="2b74e-161">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="2b74e-161">Required?</span></span>                            | <span data-ttu-id="2b74e-162">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-162">false</span></span>                                |
| <span data-ttu-id="2b74e-163">Posição?</span><span class="sxs-lookup"><span data-stu-id="2b74e-163">Position?</span></span>                            | <span data-ttu-id="2b74e-164">com o nome</span><span class="sxs-lookup"><span data-stu-id="2b74e-164">named</span></span>                                |
| <span data-ttu-id="2b74e-165">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="2b74e-165">Default Value</span></span>                        | <span data-ttu-id="2b74e-166">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-166">false</span></span>                                |
| <span data-ttu-id="2b74e-167">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="2b74e-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2b74e-168">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-168">false</span></span>                                |
| <span data-ttu-id="2b74e-169">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="2b74e-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2b74e-170">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="2b74e-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2b74e-171">-WhatIf</span></span>

<span data-ttu-id="2b74e-172">Apresenta o que aconteceria mediante a execução do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b74e-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2b74e-173">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="2b74e-173">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="2b74e-174">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="2b74e-174">Required?</span></span>                            | <span data-ttu-id="2b74e-175">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-175">false</span></span>                                |
| <span data-ttu-id="2b74e-176">Posição?</span><span class="sxs-lookup"><span data-stu-id="2b74e-176">Position?</span></span>                            | <span data-ttu-id="2b74e-177">com o nome</span><span class="sxs-lookup"><span data-stu-id="2b74e-177">named</span></span>                                |
| <span data-ttu-id="2b74e-178">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="2b74e-178">Default Value</span></span>                        | <span data-ttu-id="2b74e-179">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-179">false</span></span>                                |
| <span data-ttu-id="2b74e-180">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="2b74e-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2b74e-181">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-181">false</span></span>                                |
| <span data-ttu-id="2b74e-182">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="2b74e-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2b74e-183">falso</span><span class="sxs-lookup"><span data-stu-id="2b74e-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="2b74e-184">&lt;Parâmetroscomuns&gt;</span><span class="sxs-lookup"><span data-stu-id="2b74e-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="2b74e-185">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="2b74e-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="2b74e-186">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2b74e-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="2b74e-187">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="2b74e-187">INPUTS</span></span>

<span data-ttu-id="2b74e-188">Este cmdlet não aceita nenhuma entrada.</span><span class="sxs-lookup"><span data-stu-id="2b74e-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="2b74e-189">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="2b74e-189">OUTPUTS</span></span>

<span data-ttu-id="2b74e-190">Este cmdlet não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="2b74e-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="2b74e-191">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="2b74e-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="2b74e-192">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="2b74e-192">EXAMPLE 1</span></span>

<span data-ttu-id="2b74e-193">Este exemplo instala a aplicação de web PSWA utilizando os valores predefinidos para o **WebApplicationName** (*pswa*) e **WebSiteName** (*Default Web Site* ) parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2b74e-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="2b74e-194">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="2b74e-194">EXAMPLE 2</span></span>

<span data-ttu-id="2b74e-195">Este exemplo instala a aplicação de web PSWA com um certificado de teste e utilizando os valores predefinidos para o **WebApplicationName** e **WebSiteName** parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2b74e-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="2b74e-196">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="2b74e-196">Related topics</span></span>

- [<span data-ttu-id="2b74e-197">Adicionar-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2b74e-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="2b74e-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2b74e-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="2b74e-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2b74e-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="2b74e-200">Teste-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2b74e-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
