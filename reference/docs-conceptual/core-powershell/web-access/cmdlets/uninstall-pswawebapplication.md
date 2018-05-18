---
ms.topic: reference
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: Desinstalar-PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="4701d-103">Desinstalar-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="4701d-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="4701d-104">RESUMO</span><span class="sxs-lookup"><span data-stu-id="4701d-104">SYNOPSIS</span></span>

<span data-ttu-id="4701d-105">Desinstala a aplicação de web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="4701d-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="4701d-106">SINTAXE</span><span class="sxs-lookup"><span data-stu-id="4701d-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="4701d-107">Predefinido</span><span class="sxs-lookup"><span data-stu-id="4701d-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="4701d-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="4701d-108">DESCRIPTION</span></span>

<span data-ttu-id="4701d-109">O **Uninstall-PswaWebApplication** cmdlet desinstala a aplicação web do Windows PowerShell e remove o Web site do IIS.</span><span class="sxs-lookup"><span data-stu-id="4701d-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="4701d-110">O cmdlet não desinstala IIS nem outras funcionalidades instaladas porque estavam necessárias para o Windows PowerShell executar.</span><span class="sxs-lookup"><span data-stu-id="4701d-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="4701d-111">PARÂMETROS</span><span class="sxs-lookup"><span data-stu-id="4701d-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="4701d-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="4701d-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="4701d-113">Indica que os certificados de teste criado o **instalar\_PswaWebApplication** cmdlet (com o **UseTestCertificate** parâmetro) é eliminado.</span><span class="sxs-lookup"><span data-stu-id="4701d-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="4701d-114">Apenas o certificado de teste com o mesmo nome que criados pelo **Install-PswaWebApplication** cmdlet é removido.</span><span class="sxs-lookup"><span data-stu-id="4701d-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||
|-|-|
| <span data-ttu-id="4701d-115">Aliases</span><span class="sxs-lookup"><span data-stu-id="4701d-115">Aliases</span></span>                              | <span data-ttu-id="4701d-116">nenhum</span><span class="sxs-lookup"><span data-stu-id="4701d-116">none</span></span>                                 |
| <span data-ttu-id="4701d-117">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="4701d-117">Required?</span></span>                            | <span data-ttu-id="4701d-118">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-118">false</span></span>                                |
| <span data-ttu-id="4701d-119">Posição?</span><span class="sxs-lookup"><span data-stu-id="4701d-119">Position?</span></span>                            | <span data-ttu-id="4701d-120">com o nome</span><span class="sxs-lookup"><span data-stu-id="4701d-120">named</span></span>                                |
| <span data-ttu-id="4701d-121">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="4701d-121">Default Value</span></span>                        | <span data-ttu-id="4701d-122">VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="4701d-122">true</span></span>                                 |
| <span data-ttu-id="4701d-123">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="4701d-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4701d-124">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-124">false</span></span>                                |
| <span data-ttu-id="4701d-125">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="4701d-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4701d-126">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="4701d-127">-WebApplicationName &lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="4701d-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="4701d-128">Especifica o nome da aplicação web para desinstalar.</span><span class="sxs-lookup"><span data-stu-id="4701d-128">Specifies the name of the web application to uninstall.</span></span>

|||
|-|-|
| <span data-ttu-id="4701d-129">Aliases</span><span class="sxs-lookup"><span data-stu-id="4701d-129">Aliases</span></span>                              | <span data-ttu-id="4701d-130">nenhum</span><span class="sxs-lookup"><span data-stu-id="4701d-130">none</span></span>                                 |
| <span data-ttu-id="4701d-131">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="4701d-131">Required?</span></span>                            | <span data-ttu-id="4701d-132">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-132">false</span></span>                                |
| <span data-ttu-id="4701d-133">Posição?</span><span class="sxs-lookup"><span data-stu-id="4701d-133">Position?</span></span>                            | <span data-ttu-id="4701d-134">1</span><span class="sxs-lookup"><span data-stu-id="4701d-134">1</span></span>                                    |
| <span data-ttu-id="4701d-135">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="4701d-135">Default Value</span></span>                        | <span data-ttu-id="4701d-136">pswa</span><span class="sxs-lookup"><span data-stu-id="4701d-136">pswa</span></span>                                 |
| <span data-ttu-id="4701d-137">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="4701d-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4701d-138">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-138">false</span></span>                                |
| <span data-ttu-id="4701d-139">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="4701d-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4701d-140">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="4701d-141">-WebSiteName &lt;cadeia&gt;</span><span class="sxs-lookup"><span data-stu-id="4701d-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="4701d-142">Especifica o nome do web site onde a aplicação web está instalada.</span><span class="sxs-lookup"><span data-stu-id="4701d-142">Specifies the name of the web site where the web application is installed.</span></span>

|||
|-|-|
| <span data-ttu-id="4701d-143">Aliases</span><span class="sxs-lookup"><span data-stu-id="4701d-143">Aliases</span></span>                              | <span data-ttu-id="4701d-144">nenhum</span><span class="sxs-lookup"><span data-stu-id="4701d-144">none</span></span>                                 |
| <span data-ttu-id="4701d-145">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="4701d-145">Required?</span></span>                            | <span data-ttu-id="4701d-146">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-146">false</span></span>                                |
| <span data-ttu-id="4701d-147">Posição?</span><span class="sxs-lookup"><span data-stu-id="4701d-147">Position?</span></span>                            | <span data-ttu-id="4701d-148">com o nome</span><span class="sxs-lookup"><span data-stu-id="4701d-148">named</span></span>                                |
| <span data-ttu-id="4701d-149">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="4701d-149">Default Value</span></span>                        | <span data-ttu-id="4701d-150">Web Site predefinido</span><span class="sxs-lookup"><span data-stu-id="4701d-150">Default Web Site</span></span>                     |
| <span data-ttu-id="4701d-151">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="4701d-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4701d-152">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-152">false</span></span>                                |
| <span data-ttu-id="4701d-153">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="4701d-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4701d-154">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="4701d-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4701d-155">-Confirm</span></span>

<span data-ttu-id="4701d-156">Solicita a sua confirmação antes de executar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4701d-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="4701d-157">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="4701d-157">Required?</span></span>                            | <span data-ttu-id="4701d-158">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-158">false</span></span>                                |
| <span data-ttu-id="4701d-159">Posição?</span><span class="sxs-lookup"><span data-stu-id="4701d-159">Position?</span></span>                            | <span data-ttu-id="4701d-160">com o nome</span><span class="sxs-lookup"><span data-stu-id="4701d-160">named</span></span>                                |
| <span data-ttu-id="4701d-161">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="4701d-161">Default Value</span></span>                        | <span data-ttu-id="4701d-162">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-162">false</span></span>                                |
| <span data-ttu-id="4701d-163">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="4701d-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4701d-164">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-164">false</span></span>                                |
| <span data-ttu-id="4701d-165">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="4701d-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4701d-166">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="4701d-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4701d-167">-WhatIf</span></span>

<span data-ttu-id="4701d-168">Apresenta o que aconteceria mediante a execução do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4701d-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4701d-169">O cmdlet não é executado.</span><span class="sxs-lookup"><span data-stu-id="4701d-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="4701d-170">Obrigatório?</span><span class="sxs-lookup"><span data-stu-id="4701d-170">Required?</span></span>                            | <span data-ttu-id="4701d-171">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-171">false</span></span>                                |
| <span data-ttu-id="4701d-172">Posição?</span><span class="sxs-lookup"><span data-stu-id="4701d-172">Position?</span></span>                            | <span data-ttu-id="4701d-173">com o nome</span><span class="sxs-lookup"><span data-stu-id="4701d-173">named</span></span>                                |
| <span data-ttu-id="4701d-174">Valor Predefinido</span><span class="sxs-lookup"><span data-stu-id="4701d-174">Default Value</span></span>                        | <span data-ttu-id="4701d-175">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-175">false</span></span>                                |
| <span data-ttu-id="4701d-176">Aceitar Entrada de Pipeline?</span><span class="sxs-lookup"><span data-stu-id="4701d-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4701d-177">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-177">false</span></span>                                |
| <span data-ttu-id="4701d-178">Aceitar Carateres Universais?</span><span class="sxs-lookup"><span data-stu-id="4701d-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4701d-179">falso</span><span class="sxs-lookup"><span data-stu-id="4701d-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="4701d-180">&lt;Parâmetroscomuns&gt;</span><span class="sxs-lookup"><span data-stu-id="4701d-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="4701d-181">Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="4701d-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="4701d-182">Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4701d-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="4701d-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="4701d-183">INPUTS</span></span>

<span data-ttu-id="4701d-184">Este cmdlet não aceita nenhuma entrada.</span><span class="sxs-lookup"><span data-stu-id="4701d-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="4701d-185">SAÍDAS</span><span class="sxs-lookup"><span data-stu-id="4701d-185">OUTPUTS</span></span>

<span data-ttu-id="4701d-186">Este cmdlet não devolve nenhum resultado.</span><span class="sxs-lookup"><span data-stu-id="4701d-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="4701d-187">EXEMPLOS</span><span class="sxs-lookup"><span data-stu-id="4701d-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="4701d-188">EXEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="4701d-188">EXAMPLE 1</span></span>

<span data-ttu-id="4701d-189">Este comando desinstala a aplicação de Web do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4701d-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="4701d-190">Pode utilizar este cmdlet para desinstalar a aplicação de Web do Windows PowerShell, se tiver instalado, utilizando os valores predefinidos.</span><span class="sxs-lookup"><span data-stu-id="4701d-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="4701d-191">EXEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="4701d-191">EXAMPLE 2</span></span>

<span data-ttu-id="4701d-192">Este comando desinstala a aplicação de Web do Windows PowerShell e elimina o certificado de teste associado à aplicação.</span><span class="sxs-lookup"><span data-stu-id="4701d-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="4701d-193">Pode utilizar este cmdlet para desinstalar a aplicação de Web do Windows PowerShell, se instalou utilizando os valores predefinidos e criar um certificado de teste.</span><span class="sxs-lookup"><span data-stu-id="4701d-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="4701d-194">EXEMPLO 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="4701d-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="4701d-195">Este comando desinstala a aplicação do Windows PowerShell Web quando um Web site personalizado e aplicação foram especificadas durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="4701d-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="4701d-196">O comando remove o Web site com o nome *MySite* e a aplicação com o nome *TestApplication* e especifica que os certificados de teste associados à aplicação também são eliminados.</span><span class="sxs-lookup"><span data-stu-id="4701d-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="4701d-197">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="4701d-197">Related topics</span></span>

- [<span data-ttu-id="4701d-198">Adicionar-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4701d-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="4701d-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4701d-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="4701d-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="4701d-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="4701d-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4701d-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="4701d-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4701d-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)