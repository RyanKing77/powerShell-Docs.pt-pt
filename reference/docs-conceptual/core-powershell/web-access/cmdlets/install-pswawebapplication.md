---
ms.topic: reference
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268304"
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="844a2-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="844a2-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="844a2-104">SINOPSE</span><span class="sxs-lookup"><span data-stu-id="844a2-104">SYNOPSIS</span></span>

<span data-ttu-id="844a2-105">Configura o aplicativo web do Windows PowerShell Web Access no IIS.</span><span class="sxs-lookup"><span data-stu-id="844a2-105">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="844a2-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="844a2-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="844a2-107">Predefinido</span><span class="sxs-lookup"><span data-stu-id="844a2-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="844a2-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="844a2-108">DESCRIPTION</span></span>

<span data-ttu-id="844a2-109">O **Install-PswaWebApplication** cmdlet configura o aplicativo de web do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="844a2-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span>
<span data-ttu-id="844a2-110">Este cmdlet instala a aplicação web, associa-à um web site e, opcionalmente, cria um teste SSL certificado com o **useTestCertificate** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="844a2-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="844a2-111">Segurança de administradores da web motivos não devem utilizar um certificado de teste para ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="844a2-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="844a2-112">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="844a2-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="844a2-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="844a2-113">-UseTestCertificate</span></span>

<span data-ttu-id="844a2-114">Especifica que um certificado de teste é criado.</span><span class="sxs-lookup"><span data-stu-id="844a2-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="844a2-115">Se este parâmetro estiver definido como true, em seguida, este cmdlet cria um certificado de teste e configura o aplicativo web do Windows PowerShell Web Access para utilizar o certificado para pedidos HTTPS.</span><span class="sxs-lookup"><span data-stu-id="844a2-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="844a2-116">Se este parâmetro estiver definido como false, não é criada nenhum certificado ou a ligação.</span><span class="sxs-lookup"><span data-stu-id="844a2-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="844a2-117">Defina este valor como FALSO se outro certificado é utilizado para o Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="844a2-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="844a2-118">Aliases</span><span class="sxs-lookup"><span data-stu-id="844a2-118">Aliases</span></span>                              | <span data-ttu-id="844a2-119">nenhum</span><span class="sxs-lookup"><span data-stu-id="844a2-119">none</span></span>                                 |
| <span data-ttu-id="844a2-120">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="844a2-120">Required?</span></span>                            | <span data-ttu-id="844a2-121">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-121">false</span></span>                                |
| <span data-ttu-id="844a2-122">Posição?</span><span class="sxs-lookup"><span data-stu-id="844a2-122">Position?</span></span>                            | <span data-ttu-id="844a2-123">com o nome</span><span class="sxs-lookup"><span data-stu-id="844a2-123">named</span></span>                                |
| <span data-ttu-id="844a2-124">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="844a2-124">Default Value</span></span>                        | <span data-ttu-id="844a2-125">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="844a2-125">true</span></span>                                 |
| <span data-ttu-id="844a2-126">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="844a2-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="844a2-127">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-127">false</span></span>                                |
| <span data-ttu-id="844a2-128">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="844a2-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="844a2-129">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-129">false</span></span>                                |

### <a name="-webapplicationname"></a><span data-ttu-id="844a2-130">-WebApplicationName</span><span class="sxs-lookup"><span data-stu-id="844a2-130">-WebApplicationName</span></span>

<span data-ttu-id="844a2-131">Especifica o nome da sua aplicação web.</span><span class="sxs-lookup"><span data-stu-id="844a2-131">Specifies the name for your web application.</span></span> <span data-ttu-id="844a2-132">É apresentado como a última parte do URL do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="844a2-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="844a2-133">Aliases</span><span class="sxs-lookup"><span data-stu-id="844a2-133">Aliases</span></span>                              | <span data-ttu-id="844a2-134">nenhum</span><span class="sxs-lookup"><span data-stu-id="844a2-134">none</span></span>                                 |
| <span data-ttu-id="844a2-135">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="844a2-135">Required?</span></span>                            | <span data-ttu-id="844a2-136">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-136">false</span></span>                                |
| <span data-ttu-id="844a2-137">Posição?</span><span class="sxs-lookup"><span data-stu-id="844a2-137">Position?</span></span>                            | <span data-ttu-id="844a2-138">1</span><span class="sxs-lookup"><span data-stu-id="844a2-138">1</span></span>                                    |
| <span data-ttu-id="844a2-139">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="844a2-139">Default Value</span></span>                        | <span data-ttu-id="844a2-140">pswa</span><span class="sxs-lookup"><span data-stu-id="844a2-140">pswa</span></span>                                 |
| <span data-ttu-id="844a2-141">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="844a2-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="844a2-142">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-142">false</span></span>                                |
| <span data-ttu-id="844a2-143">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="844a2-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="844a2-144">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-144">false</span></span>                                |

### <a name="-websitename"></a><span data-ttu-id="844a2-145">-WebSiteName</span><span class="sxs-lookup"><span data-stu-id="844a2-145">-WebSiteName</span></span>

<span data-ttu-id="844a2-146">Especifica o nome do site do servidor Web (IIS) em que pretende instalar esta aplicação web do Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="844a2-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="844a2-147">Aliases</span><span class="sxs-lookup"><span data-stu-id="844a2-147">Aliases</span></span>                              | <span data-ttu-id="844a2-148">nenhum</span><span class="sxs-lookup"><span data-stu-id="844a2-148">none</span></span>                                 |
| <span data-ttu-id="844a2-149">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="844a2-149">Required?</span></span>                            | <span data-ttu-id="844a2-150">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-150">false</span></span>                                |
| <span data-ttu-id="844a2-151">Posição?</span><span class="sxs-lookup"><span data-stu-id="844a2-151">Position?</span></span>                            | <span data-ttu-id="844a2-152">com o nome</span><span class="sxs-lookup"><span data-stu-id="844a2-152">named</span></span>                                |
| <span data-ttu-id="844a2-153">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="844a2-153">Default Value</span></span>                        | <span data-ttu-id="844a2-154">Web Site predefinido</span><span class="sxs-lookup"><span data-stu-id="844a2-154">Default Web Site</span></span>                     |
| <span data-ttu-id="844a2-155">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="844a2-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="844a2-156">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-156">false</span></span>                                |
| <span data-ttu-id="844a2-157">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="844a2-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="844a2-158">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="844a2-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="844a2-159">-Confirm</span></span>

<span data-ttu-id="844a2-160">Solicita a sua confirmação antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="844a2-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="844a2-161">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="844a2-161">Required?</span></span>                            | <span data-ttu-id="844a2-162">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-162">false</span></span>                                |
| <span data-ttu-id="844a2-163">Posição?</span><span class="sxs-lookup"><span data-stu-id="844a2-163">Position?</span></span>                            | <span data-ttu-id="844a2-164">com o nome</span><span class="sxs-lookup"><span data-stu-id="844a2-164">named</span></span>                                |
| <span data-ttu-id="844a2-165">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="844a2-165">Default Value</span></span>                        | <span data-ttu-id="844a2-166">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-166">false</span></span>                                |
| <span data-ttu-id="844a2-167">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="844a2-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="844a2-168">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-168">false</span></span>                                |
| <span data-ttu-id="844a2-169">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="844a2-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="844a2-170">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="844a2-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="844a2-171">-WhatIf</span></span>

<span data-ttu-id="844a2-172">Apresenta o que aconteceria mediante a execução do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="844a2-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="844a2-173">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="844a2-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="844a2-174">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="844a2-174">Required?</span></span>                            | <span data-ttu-id="844a2-175">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-175">false</span></span>                                |
| <span data-ttu-id="844a2-176">Posição?</span><span class="sxs-lookup"><span data-stu-id="844a2-176">Position?</span></span>                            | <span data-ttu-id="844a2-177">com o nome</span><span class="sxs-lookup"><span data-stu-id="844a2-177">named</span></span>                                |
| <span data-ttu-id="844a2-178">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="844a2-178">Default Value</span></span>                        | <span data-ttu-id="844a2-179">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-179">false</span></span>                                |
| <span data-ttu-id="844a2-180">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="844a2-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="844a2-181">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-181">false</span></span>                                |
| <span data-ttu-id="844a2-182">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="844a2-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="844a2-183">falso</span><span class="sxs-lookup"><span data-stu-id="844a2-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="844a2-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="844a2-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="844a2-185">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="844a2-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span> <span data-ttu-id="844a2-186">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="844a2-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="844a2-187">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="844a2-187">INPUTS</span></span>

<span data-ttu-id="844a2-188">Este cmdlet não precisa de entrada.</span><span class="sxs-lookup"><span data-stu-id="844a2-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="844a2-189">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="844a2-189">OUTPUTS</span></span>

<span data-ttu-id="844a2-190">Este cmdlet não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="844a2-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="844a2-191">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="844a2-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="844a2-192">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="844a2-192">EXAMPLE 1</span></span>

<span data-ttu-id="844a2-193">Este exemplo instala a aplicação de web PSWA utilizando os valores predefinidos para o **WebApplicationName** (*pswa*) e **WebSiteName** (*Web Site predefinido* ) parâmetros.</span><span class="sxs-lookup"><span data-stu-id="844a2-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="844a2-194">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="844a2-194">EXAMPLE 2</span></span>

<span data-ttu-id="844a2-195">Este exemplo instala o aplicativo da web PSWA com um certificado de teste e utilizar os valores predefinidos para o **WebApplicationName** e **WebSiteName** parâmetros.</span><span class="sxs-lookup"><span data-stu-id="844a2-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="844a2-196">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="844a2-196">Related topics</span></span>

- [<span data-ttu-id="844a2-197">Adicionar-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="844a2-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="844a2-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="844a2-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="844a2-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="844a2-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="844a2-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="844a2-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)