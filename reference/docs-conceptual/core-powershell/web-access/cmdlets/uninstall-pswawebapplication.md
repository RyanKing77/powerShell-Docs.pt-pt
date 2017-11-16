---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 2016-12-12
title: desinstalar pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 5fe608b3bfbb90f842f16c1f5a8c51879589cf6d
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="f3588-103">Desinstalar-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="f3588-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="f3588-104">RESUMO</span><span class="sxs-lookup"><span data-stu-id="f3588-104">SYNOPSIS</span></span>

<span data-ttu-id="f3588-105">Desinstala a aplicação de web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="f3588-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3588-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="f3588-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="f3588-107">Predefinido</span><span class="sxs-lookup"><span data-stu-id="f3588-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="f3588-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="f3588-108">DESCRIPTION</span></span>

<span data-ttu-id="f3588-109">O **Uninstall-PswaWebApplication** cmdlet desinstala a aplicação web do Windows PowerShell e remove o Web site do IIS.</span><span class="sxs-lookup"><span data-stu-id="f3588-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="f3588-110">O cmdlet não desinstala IIS nem outras funcionalidades instaladas porque estavam necessárias para o Windows PowerShell executar.</span><span class="sxs-lookup"><span data-stu-id="f3588-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="f3588-111">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="f3588-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="f3588-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="f3588-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="f3588-113">Indica que os certificados de teste criado o **instalar\_PswaWebApplication** cmdlet (com o **UseTestCertificate** parâmetro) é eliminado.</span><span class="sxs-lookup"><span data-stu-id="f3588-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="f3588-114">Apenas o certificado de teste com o mesmo nome que criados pelo **Install-PswaWebApplication** cmdlet é removido.</span><span class="sxs-lookup"><span data-stu-id="f3588-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="f3588-115">Aliases</span><span class="sxs-lookup"><span data-stu-id="f3588-115">Aliases</span></span>                              | <span data-ttu-id="f3588-116">nenhum</span><span class="sxs-lookup"><span data-stu-id="f3588-116">none</span></span>                                 |
| <span data-ttu-id="f3588-117">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="f3588-117">Required?</span></span>                            | <span data-ttu-id="f3588-118">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-118">false</span></span>                                |
| <span data-ttu-id="f3588-119">Posição?</span><span class="sxs-lookup"><span data-stu-id="f3588-119">Position?</span></span>                            | <span data-ttu-id="f3588-120">com o nome</span><span class="sxs-lookup"><span data-stu-id="f3588-120">named</span></span>                                |
| <span data-ttu-id="f3588-121">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="f3588-121">Default Value</span></span>                        | <span data-ttu-id="f3588-122">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="f3588-122">true</span></span>                                 |
| <span data-ttu-id="f3588-123">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="f3588-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f3588-124">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-124">false</span></span>                                |
| <span data-ttu-id="f3588-125">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="f3588-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f3588-126">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="f3588-127">-WebApplicationName &lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="f3588-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="f3588-128">Especifica o nome da aplicação web para desinstalar.</span><span class="sxs-lookup"><span data-stu-id="f3588-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="f3588-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="f3588-129">Aliases</span></span>                              | <span data-ttu-id="f3588-130">nenhum</span><span class="sxs-lookup"><span data-stu-id="f3588-130">none</span></span>                                 |
| <span data-ttu-id="f3588-131">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="f3588-131">Required?</span></span>                            | <span data-ttu-id="f3588-132">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-132">false</span></span>                                |
| <span data-ttu-id="f3588-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="f3588-133">Position?</span></span>                            | <span data-ttu-id="f3588-134">1</span><span class="sxs-lookup"><span data-stu-id="f3588-134">1</span></span>                                    |
| <span data-ttu-id="f3588-135">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="f3588-135">Default Value</span></span>                        | <span data-ttu-id="f3588-136">pswa</span><span class="sxs-lookup"><span data-stu-id="f3588-136">pswa</span></span>                                 |
| <span data-ttu-id="f3588-137">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="f3588-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f3588-138">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-138">false</span></span>                                |
| <span data-ttu-id="f3588-139">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="f3588-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f3588-140">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="f3588-141">-WebSiteName &lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="f3588-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="f3588-142">Especifica o nome do web site onde a aplicação web está instalada.</span><span class="sxs-lookup"><span data-stu-id="f3588-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="f3588-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="f3588-143">Aliases</span></span>                              | <span data-ttu-id="f3588-144">nenhum</span><span class="sxs-lookup"><span data-stu-id="f3588-144">none</span></span>                                 |
| <span data-ttu-id="f3588-145">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="f3588-145">Required?</span></span>                            | <span data-ttu-id="f3588-146">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-146">false</span></span>                                |
| <span data-ttu-id="f3588-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="f3588-147">Position?</span></span>                            | <span data-ttu-id="f3588-148">com o nome</span><span class="sxs-lookup"><span data-stu-id="f3588-148">named</span></span>                                |
| <span data-ttu-id="f3588-149">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="f3588-149">Default Value</span></span>                        | <span data-ttu-id="f3588-150">Web Site predefinido</span><span class="sxs-lookup"><span data-stu-id="f3588-150">Default Web Site</span></span>                     |
| <span data-ttu-id="f3588-151">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="f3588-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f3588-152">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-152">false</span></span>                                |
| <span data-ttu-id="f3588-153">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="f3588-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f3588-154">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="f3588-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f3588-155">-Confirm</span></span>

<span data-ttu-id="f3588-156">Solicita a sua confirmação antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3588-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="f3588-157">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="f3588-157">Required?</span></span>                            | <span data-ttu-id="f3588-158">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-158">false</span></span>                                |
| <span data-ttu-id="f3588-159">Posição?</span><span class="sxs-lookup"><span data-stu-id="f3588-159">Position?</span></span>                            | <span data-ttu-id="f3588-160">com o nome</span><span class="sxs-lookup"><span data-stu-id="f3588-160">named</span></span>                                |
| <span data-ttu-id="f3588-161">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="f3588-161">Default Value</span></span>                        | <span data-ttu-id="f3588-162">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-162">false</span></span>                                |
| <span data-ttu-id="f3588-163">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="f3588-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f3588-164">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-164">false</span></span>                                |
| <span data-ttu-id="f3588-165">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="f3588-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f3588-166">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="f3588-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f3588-167">-WhatIf</span></span>

<span data-ttu-id="f3588-168">Apresenta o que aconteceria mediante a execução do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3588-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f3588-169">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="f3588-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="f3588-170">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="f3588-170">Required?</span></span>                            | <span data-ttu-id="f3588-171">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-171">false</span></span>                                |
| <span data-ttu-id="f3588-172">Posição?</span><span class="sxs-lookup"><span data-stu-id="f3588-172">Position?</span></span>                            | <span data-ttu-id="f3588-173">com o nome</span><span class="sxs-lookup"><span data-stu-id="f3588-173">named</span></span>                                |
| <span data-ttu-id="f3588-174">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="f3588-174">Default Value</span></span>                        | <span data-ttu-id="f3588-175">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-175">false</span></span>                                |
| <span data-ttu-id="f3588-176">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="f3588-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f3588-177">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-177">false</span></span>                                |
| <span data-ttu-id="f3588-178">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="f3588-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f3588-179">falso</span><span class="sxs-lookup"><span data-stu-id="f3588-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="f3588-180">&lt;Parâmetroscomuns&gt;</span><span class="sxs-lookup"><span data-stu-id="f3588-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="f3588-181">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="f3588-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="f3588-182">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f3588-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="f3588-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="f3588-183">INPUTS</span></span>

<span data-ttu-id="f3588-184">Este cmdlet não aceita nenhuma entrada.</span><span class="sxs-lookup"><span data-stu-id="f3588-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="f3588-185">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="f3588-185">OUTPUTS</span></span>

<span data-ttu-id="f3588-186">Este cmdlet não devolve nenhum resultado.</span><span class="sxs-lookup"><span data-stu-id="f3588-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="f3588-187">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="f3588-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="f3588-188">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="f3588-188">EXAMPLE 1</span></span>

<span data-ttu-id="f3588-189">Este comando desinstala a aplicação de Web do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3588-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="f3588-190">Pode utilizar este cmdlet para desinstalar a aplicação de Web do Windows PowerShell, se tiver instalado, utilizando os valores predefinidos.</span><span class="sxs-lookup"><span data-stu-id="f3588-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="f3588-191">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="f3588-191">EXAMPLE 2</span></span>

<span data-ttu-id="f3588-192">Este comando desinstala a aplicação de Web do Windows PowerShell e elimina o certificado de teste associado à aplicação.</span><span class="sxs-lookup"><span data-stu-id="f3588-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="f3588-193">Pode utilizar este cmdlet para desinstalar a aplicação de Web do Windows PowerShell, se instalou utilizando os valores predefinidos e criar um certificado de teste.</span><span class="sxs-lookup"><span data-stu-id="f3588-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="f3588-194">EXEMPLO 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="f3588-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="f3588-195">Este comando desinstala a aplicação do Windows PowerShell Web quando um Web site personalizado e aplicação foram especificadas durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="f3588-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="f3588-196">O comando remove o Web site com o nome *MySite* e a aplicação com o nome *TestApplication* e especifica que os certificados de teste associados à aplicação também são eliminados.</span><span class="sxs-lookup"><span data-stu-id="f3588-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="f3588-197">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="f3588-197">Related topics</span></span>

- [<span data-ttu-id="f3588-198">Adicionar-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f3588-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="f3588-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f3588-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="f3588-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="f3588-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="f3588-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f3588-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="f3588-202">Teste-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f3588-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
