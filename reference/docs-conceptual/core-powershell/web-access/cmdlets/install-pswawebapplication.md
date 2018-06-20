---
ms.topic: reference
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 68455d9490f7d5c33c1a928ac262a76a78ad7128
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189606"
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="e9350-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="e9350-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="e9350-104">RESUMO</span><span class="sxs-lookup"><span data-stu-id="e9350-104">SYNOPSIS</span></span>

<span data-ttu-id="e9350-105">Configura a aplicação web do Windows PowerShell® Web Access no IIS.</span><span class="sxs-lookup"><span data-stu-id="e9350-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="e9350-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="e9350-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="e9350-107">Predefinido</span><span class="sxs-lookup"><span data-stu-id="e9350-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="e9350-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="e9350-108">DESCRIPTION</span></span>

<span data-ttu-id="e9350-109">O **Install-PswaWebApplication** cmdlet configura aplicação web de acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9350-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="e9350-110">Este cmdlet instala a aplicação web, associa-o com um web site e, opcionalmente, cria um teste SSL certificado, utilizando o **useTestCertificate** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e9350-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="e9350-111">Segurança de administradores de web de motivos não devem utilizar um certificado de teste para ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="e9350-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="e9350-112">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="e9350-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="e9350-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="e9350-113">-UseTestCertificate</span></span>

<span data-ttu-id="e9350-114">Especifica que é criado um certificado de teste.</span><span class="sxs-lookup"><span data-stu-id="e9350-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="e9350-115">Se este parâmetro estiver definido como VERDADEIRO, então este cmdlet cria um certificado de teste e configura a aplicação web de acesso Web Windows PowerShell para utilizar o certificado para pedidos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e9350-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="e9350-116">Se este parâmetro estiver definido como FALSO, não é criado nenhum certificado ou o enlace.</span><span class="sxs-lookup"><span data-stu-id="e9350-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="e9350-117">Defina este valor como FALSO se outro certificado é utilizado para acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9350-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="e9350-118">Aliases</span><span class="sxs-lookup"><span data-stu-id="e9350-118">Aliases</span></span>                              | <span data-ttu-id="e9350-119">nenhum</span><span class="sxs-lookup"><span data-stu-id="e9350-119">none</span></span>                                 |
| <span data-ttu-id="e9350-120">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="e9350-120">Required?</span></span>                            | <span data-ttu-id="e9350-121">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-121">false</span></span>                                |
| <span data-ttu-id="e9350-122">Posição?</span><span class="sxs-lookup"><span data-stu-id="e9350-122">Position?</span></span>                            | <span data-ttu-id="e9350-123">com o nome</span><span class="sxs-lookup"><span data-stu-id="e9350-123">named</span></span>                                |
| <span data-ttu-id="e9350-124">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="e9350-124">Default Value</span></span>                        | <span data-ttu-id="e9350-125">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="e9350-125">true</span></span>                                 |
| <span data-ttu-id="e9350-126">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="e9350-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e9350-127">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-127">false</span></span>                                |
| <span data-ttu-id="e9350-128">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="e9350-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e9350-129">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="e9350-130">-WebApplicationName&lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="e9350-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="e9350-131">Especifica o nome da sua aplicação web.</span><span class="sxs-lookup"><span data-stu-id="e9350-131">Specifies the name for your web application.</span></span> <span data-ttu-id="e9350-132">Isto é apresentado como a última parte do URL de acesso Web do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9350-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="e9350-133">Aliases</span><span class="sxs-lookup"><span data-stu-id="e9350-133">Aliases</span></span>                              | <span data-ttu-id="e9350-134">nenhum</span><span class="sxs-lookup"><span data-stu-id="e9350-134">none</span></span>                                 |
| <span data-ttu-id="e9350-135">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="e9350-135">Required?</span></span>                            | <span data-ttu-id="e9350-136">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-136">false</span></span>                                |
| <span data-ttu-id="e9350-137">Posição?</span><span class="sxs-lookup"><span data-stu-id="e9350-137">Position?</span></span>                            | <span data-ttu-id="e9350-138">1</span><span class="sxs-lookup"><span data-stu-id="e9350-138">1</span></span>                                    |
| <span data-ttu-id="e9350-139">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="e9350-139">Default Value</span></span>                        | <span data-ttu-id="e9350-140">pswa</span><span class="sxs-lookup"><span data-stu-id="e9350-140">pswa</span></span>                                 |
| <span data-ttu-id="e9350-141">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="e9350-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e9350-142">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-142">false</span></span>                                |
| <span data-ttu-id="e9350-143">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="e9350-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e9350-144">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="e9350-145">-WebSiteName&lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="e9350-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="e9350-146">Especifica o nome do site do servidor Web (IIS) em que pretende instalar esta aplicação web do acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9350-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="e9350-147">Aliases</span><span class="sxs-lookup"><span data-stu-id="e9350-147">Aliases</span></span>                              | <span data-ttu-id="e9350-148">nenhum</span><span class="sxs-lookup"><span data-stu-id="e9350-148">none</span></span>                                 |
| <span data-ttu-id="e9350-149">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="e9350-149">Required?</span></span>                            | <span data-ttu-id="e9350-150">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-150">false</span></span>                                |
| <span data-ttu-id="e9350-151">Posição?</span><span class="sxs-lookup"><span data-stu-id="e9350-151">Position?</span></span>                            | <span data-ttu-id="e9350-152">com o nome</span><span class="sxs-lookup"><span data-stu-id="e9350-152">named</span></span>                                |
| <span data-ttu-id="e9350-153">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="e9350-153">Default Value</span></span>                        | <span data-ttu-id="e9350-154">Web Site predefinido</span><span class="sxs-lookup"><span data-stu-id="e9350-154">Default Web Site</span></span>                     |
| <span data-ttu-id="e9350-155">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="e9350-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e9350-156">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-156">false</span></span>                                |
| <span data-ttu-id="e9350-157">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="e9350-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e9350-158">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="e9350-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e9350-159">-Confirm</span></span>

<span data-ttu-id="e9350-160">Solicita a sua confirmação antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e9350-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="e9350-161">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="e9350-161">Required?</span></span>                            | <span data-ttu-id="e9350-162">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-162">false</span></span>                                |
| <span data-ttu-id="e9350-163">Posição?</span><span class="sxs-lookup"><span data-stu-id="e9350-163">Position?</span></span>                            | <span data-ttu-id="e9350-164">com o nome</span><span class="sxs-lookup"><span data-stu-id="e9350-164">named</span></span>                                |
| <span data-ttu-id="e9350-165">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="e9350-165">Default Value</span></span>                        | <span data-ttu-id="e9350-166">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-166">false</span></span>                                |
| <span data-ttu-id="e9350-167">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="e9350-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e9350-168">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-168">false</span></span>                                |
| <span data-ttu-id="e9350-169">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="e9350-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e9350-170">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="e9350-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e9350-171">-WhatIf</span></span>

<span data-ttu-id="e9350-172">Apresenta o que aconteceria mediante a execução do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e9350-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e9350-173">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="e9350-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="e9350-174">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="e9350-174">Required?</span></span>                            | <span data-ttu-id="e9350-175">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-175">false</span></span>                                |
| <span data-ttu-id="e9350-176">Posição?</span><span class="sxs-lookup"><span data-stu-id="e9350-176">Position?</span></span>                            | <span data-ttu-id="e9350-177">com o nome</span><span class="sxs-lookup"><span data-stu-id="e9350-177">named</span></span>                                |
| <span data-ttu-id="e9350-178">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="e9350-178">Default Value</span></span>                        | <span data-ttu-id="e9350-179">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-179">false</span></span>                                |
| <span data-ttu-id="e9350-180">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="e9350-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e9350-181">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-181">false</span></span>                                |
| <span data-ttu-id="e9350-182">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="e9350-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e9350-183">falso</span><span class="sxs-lookup"><span data-stu-id="e9350-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="e9350-184">&lt;Parâmetroscomuns&gt;</span><span class="sxs-lookup"><span data-stu-id="e9350-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="e9350-185">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="e9350-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="e9350-186">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e9350-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="e9350-187">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="e9350-187">INPUTS</span></span>

<span data-ttu-id="e9350-188">Este cmdlet não aceita nenhuma entrada.</span><span class="sxs-lookup"><span data-stu-id="e9350-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="e9350-189">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="e9350-189">OUTPUTS</span></span>

<span data-ttu-id="e9350-190">Este cmdlet não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="e9350-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="e9350-191">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="e9350-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="e9350-192">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="e9350-192">EXAMPLE 1</span></span>

<span data-ttu-id="e9350-193">Este exemplo instala a aplicação de web PSWA utilizando os valores predefinidos para o **WebApplicationName** (*pswa*) e **WebSiteName** (*Default Web Site* ) parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e9350-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="e9350-194">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="e9350-194">EXAMPLE 2</span></span>

<span data-ttu-id="e9350-195">Este exemplo instala a aplicação de web PSWA com um certificado de teste e utilizando os valores predefinidos para o **WebApplicationName** e **WebSiteName** parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e9350-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="e9350-196">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="e9350-196">Related topics</span></span>

- [<span data-ttu-id="e9350-197">Adicionar-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e9350-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="e9350-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e9350-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="e9350-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e9350-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="e9350-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e9350-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)