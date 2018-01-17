---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 2016-12-12
title: instalar pswawebapplication
ms.technology: powershell
ms.openlocfilehash: ce4d01fbe8a83924e7023d792c68c903a32e07d4
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="8daad-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="8daad-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="8daad-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="8daad-104">SYNOPSIS</span></span>

<span data-ttu-id="8daad-105">Configura a aplicação web do Windows PowerShell® Web Access no IIS.</span><span class="sxs-lookup"><span data-stu-id="8daad-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="8daad-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8daad-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="8daad-107">Predefinido</span><span class="sxs-lookup"><span data-stu-id="8daad-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="8daad-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="8daad-108">DESCRIPTION</span></span>

<span data-ttu-id="8daad-109">O **Install-PswaWebApplication** cmdlet configura aplicação web de acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8daad-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="8daad-110">Este cmdlet instala a aplicação web, associa-o com um web site e, opcionalmente, cria um teste SSL certificado, utilizando o **useTestCertificate** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8daad-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="8daad-111">Segurança de administradores de web de motivos não devem utilizar um certificado de teste para ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="8daad-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="8daad-112">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="8daad-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="8daad-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="8daad-113">-UseTestCertificate</span></span>

<span data-ttu-id="8daad-114">Especifica que é criado um certificado de teste.</span><span class="sxs-lookup"><span data-stu-id="8daad-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="8daad-115">Se este parâmetro estiver definido como VERDADEIRO, então este cmdlet cria um certificado de teste e configura a aplicação web de acesso Web Windows PowerShell para utilizar o certificado para pedidos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8daad-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="8daad-116">Se este parâmetro estiver definido como FALSO, não é criado nenhum certificado ou o enlace.</span><span class="sxs-lookup"><span data-stu-id="8daad-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="8daad-117">Defina este valor como FALSO se outro certificado é utilizado para acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8daad-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||  
|-|-|
| <span data-ttu-id="8daad-118">Aliases</span><span class="sxs-lookup"><span data-stu-id="8daad-118">Aliases</span></span>                              | <span data-ttu-id="8daad-119">nenhum</span><span class="sxs-lookup"><span data-stu-id="8daad-119">none</span></span>                                 |
| <span data-ttu-id="8daad-120">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="8daad-120">Required?</span></span>                            | <span data-ttu-id="8daad-121">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-121">false</span></span>                                |
| <span data-ttu-id="8daad-122">Posição?</span><span class="sxs-lookup"><span data-stu-id="8daad-122">Position?</span></span>                            | <span data-ttu-id="8daad-123">com o nome</span><span class="sxs-lookup"><span data-stu-id="8daad-123">named</span></span>                                |
| <span data-ttu-id="8daad-124">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="8daad-124">Default Value</span></span>                        | <span data-ttu-id="8daad-125">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="8daad-125">true</span></span>                                 |
| <span data-ttu-id="8daad-126">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="8daad-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8daad-127">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-127">false</span></span>                                |
| <span data-ttu-id="8daad-128">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="8daad-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8daad-129">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="8daad-130">-WebApplicationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="8daad-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="8daad-131">Especifica o nome da sua aplicação web.</span><span class="sxs-lookup"><span data-stu-id="8daad-131">Specifies the name for your web application.</span></span> <span data-ttu-id="8daad-132">Isto é apresentado como a última parte do URL de acesso Web do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8daad-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||  
|-|-|
| <span data-ttu-id="8daad-133">Aliases</span><span class="sxs-lookup"><span data-stu-id="8daad-133">Aliases</span></span>                              | <span data-ttu-id="8daad-134">nenhum</span><span class="sxs-lookup"><span data-stu-id="8daad-134">none</span></span>                                 |
| <span data-ttu-id="8daad-135">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="8daad-135">Required?</span></span>                            | <span data-ttu-id="8daad-136">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-136">false</span></span>                                |
| <span data-ttu-id="8daad-137">Posição?</span><span class="sxs-lookup"><span data-stu-id="8daad-137">Position?</span></span>                            | <span data-ttu-id="8daad-138">1</span><span class="sxs-lookup"><span data-stu-id="8daad-138">1</span></span>                                    |
| <span data-ttu-id="8daad-139">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="8daad-139">Default Value</span></span>                        | <span data-ttu-id="8daad-140">pswa</span><span class="sxs-lookup"><span data-stu-id="8daad-140">pswa</span></span>                                 |
| <span data-ttu-id="8daad-141">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="8daad-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8daad-142">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-142">false</span></span>                                |
| <span data-ttu-id="8daad-143">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="8daad-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8daad-144">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="8daad-145">-WebSiteName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="8daad-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="8daad-146">Especifica o nome do site do servidor Web (IIS) em que pretende instalar esta aplicação web do acesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8daad-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||  
|-|-|
| <span data-ttu-id="8daad-147">Aliases</span><span class="sxs-lookup"><span data-stu-id="8daad-147">Aliases</span></span>                              | <span data-ttu-id="8daad-148">nenhum</span><span class="sxs-lookup"><span data-stu-id="8daad-148">none</span></span>                                 |
| <span data-ttu-id="8daad-149">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="8daad-149">Required?</span></span>                            | <span data-ttu-id="8daad-150">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-150">false</span></span>                                |
| <span data-ttu-id="8daad-151">Posição?</span><span class="sxs-lookup"><span data-stu-id="8daad-151">Position?</span></span>                            | <span data-ttu-id="8daad-152">com o nome</span><span class="sxs-lookup"><span data-stu-id="8daad-152">named</span></span>                                |
| <span data-ttu-id="8daad-153">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="8daad-153">Default Value</span></span>                        | <span data-ttu-id="8daad-154">Web Site predefinido</span><span class="sxs-lookup"><span data-stu-id="8daad-154">Default Web Site</span></span>                     |
| <span data-ttu-id="8daad-155">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="8daad-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8daad-156">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-156">false</span></span>                                |
| <span data-ttu-id="8daad-157">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="8daad-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8daad-158">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="8daad-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8daad-159">-Confirm</span></span>

<span data-ttu-id="8daad-160">Solicita a sua confirmação antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8daad-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="8daad-161">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="8daad-161">Required?</span></span>                            | <span data-ttu-id="8daad-162">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-162">false</span></span>                                |
| <span data-ttu-id="8daad-163">Posição?</span><span class="sxs-lookup"><span data-stu-id="8daad-163">Position?</span></span>                            | <span data-ttu-id="8daad-164">com o nome</span><span class="sxs-lookup"><span data-stu-id="8daad-164">named</span></span>                                |
| <span data-ttu-id="8daad-165">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="8daad-165">Default Value</span></span>                        | <span data-ttu-id="8daad-166">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-166">false</span></span>                                |
| <span data-ttu-id="8daad-167">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="8daad-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8daad-168">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-168">false</span></span>                                |
| <span data-ttu-id="8daad-169">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="8daad-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8daad-170">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="8daad-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8daad-171">-WhatIf</span></span>

<span data-ttu-id="8daad-172">Apresenta o que aconteceria mediante a execução do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8daad-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8daad-173">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="8daad-173">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="8daad-174">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="8daad-174">Required?</span></span>                            | <span data-ttu-id="8daad-175">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-175">false</span></span>                                |
| <span data-ttu-id="8daad-176">Posição?</span><span class="sxs-lookup"><span data-stu-id="8daad-176">Position?</span></span>                            | <span data-ttu-id="8daad-177">com o nome</span><span class="sxs-lookup"><span data-stu-id="8daad-177">named</span></span>                                |
| <span data-ttu-id="8daad-178">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="8daad-178">Default Value</span></span>                        | <span data-ttu-id="8daad-179">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-179">false</span></span>                                |
| <span data-ttu-id="8daad-180">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="8daad-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8daad-181">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-181">false</span></span>                                |
| <span data-ttu-id="8daad-182">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="8daad-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8daad-183">falso</span><span class="sxs-lookup"><span data-stu-id="8daad-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="8daad-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="8daad-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="8daad-185">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="8daad-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="8daad-186">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8daad-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="8daad-187">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="8daad-187">INPUTS</span></span>

<span data-ttu-id="8daad-188">Este cmdlet não aceita nenhuma entrada.</span><span class="sxs-lookup"><span data-stu-id="8daad-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="8daad-189">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="8daad-189">OUTPUTS</span></span>

<span data-ttu-id="8daad-190">Este cmdlet não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="8daad-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="8daad-191">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="8daad-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="8daad-192">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="8daad-192">EXAMPLE 1</span></span>

<span data-ttu-id="8daad-193">Este exemplo instala a aplicação de web PSWA utilizando os valores predefinidos para o **WebApplicationName** (*pswa*) e **WebSiteName** (*Default Web Site* ) parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8daad-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="8daad-194">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="8daad-194">EXAMPLE 2</span></span>

<span data-ttu-id="8daad-195">Este exemplo instala a aplicação de web PSWA com um certificado de teste e utilizando os valores predefinidos para o **WebApplicationName** e **WebSiteName** parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8daad-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="8daad-196">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="8daad-196">Related topics</span></span>

- [<span data-ttu-id="8daad-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8daad-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="8daad-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8daad-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="8daad-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8daad-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="8daad-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8daad-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
