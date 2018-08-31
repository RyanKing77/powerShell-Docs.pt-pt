---
title: Ciclo de Vida do Suporte do PowerShell Core
description: As políticas que regem suportam para o PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587164"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="00b07-103">Ciclo de Vida do Suporte do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="00b07-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="00b07-104">O PowerShell Core é um conjunto distinto de ferramentas e componentes que é entregue, instalado e configurado separadamente a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00b07-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="00b07-105">Por conseguinte, o PowerShell Core não está incluído nos contratos de licenciamento do Windows 7/8.1/10 ou Windows Server.</span><span class="sxs-lookup"><span data-stu-id="00b07-105">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="00b07-106">No entanto, o PowerShell Core é suportado por tradicionais contratos de suporte da Microsoft, incluindo [Premier][], [contratos Enterprise do Microsoft][enterprise-agreement]e [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="00b07-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="00b07-107">Também pode pagar [o suporte assistido][] para o PowerShell Core através do preenchimento de um pedido de suporte para o seu problema.</span><span class="sxs-lookup"><span data-stu-id="00b07-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="00b07-108">Também oferecemos [suporte da Comunidade][] no GitHub onde pode enviar um problema, correção ou pedido de funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="00b07-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="00b07-109">Em alternativa, pode encontrar a ajuda de outros membros da Comunidade sobre gerais [Microsoft Community][] ou o Microsoft [Comunidade tecnológica do PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="00b07-109">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="00b07-110">Não oferecemos nenhuma garantia aí que o problema será resolvido ou resolvido em tempo hábil.</span><span class="sxs-lookup"><span data-stu-id="00b07-110">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="00b07-111">Se tiver um problema que requeira atenção imediata, deve usar o tradicional, opções de suporte pago.</span><span class="sxs-lookup"><span data-stu-id="00b07-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="00b07-112">Ciclo de vida do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="00b07-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="00b07-113">Está a adotar o PowerShell Core a [política de ciclo de vida moderno do Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="00b07-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="00b07-114">Este ciclo de vida do suporte destina-se para manter os clientes atualizados com as versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="00b07-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="00b07-115">O ramo do 6.x de versão do PowerShell Core será atualizado aproximadamente uma vez a cada seis meses (por exemplo, 6.0, 6.1, 6.2, etc.)</span><span class="sxs-lookup"><span data-stu-id="00b07-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00b07-116">Tem de atualizar dentro de seis meses depois de cada nova versão secundária da versão para continuar a receber suporte.</span><span class="sxs-lookup"><span data-stu-id="00b07-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="00b07-117">Por exemplo, se o PowerShell Core 6.1 for lançado no dia 1 de Julho de 2018, esperada para atualizar para o PowerShell Core 6.1 até 1 de Janeiro de 2019 para manter o suporte.</span><span class="sxs-lookup"><span data-stu-id="00b07-117">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![O ciclo de vida do PowerShell Core ramo][lifecycle-chart]

<span data-ttu-id="00b07-119">A política de ciclo de vida moderno também requer que Microsoft disponibilizar aos clientes aviso de 12 meses antes de interromper o suporte para um produto (ou seja, o PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="00b07-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="00b07-120">Por fim, podemos esperar o PowerShell Core irá adotar o "longo prazo de manutenção" abordagem em que é necessário apenas e manutenção de segurança de atualizações para manter o suporte numa filial/versão específica do 6.x.</span><span class="sxs-lookup"><span data-stu-id="00b07-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="00b07-121">Plataformas suportadas</span><span class="sxs-lookup"><span data-stu-id="00b07-121">Supported platforms</span></span>

<span data-ttu-id="00b07-122">Consulte a tabela seguinte para ver qual plataforma a versão do PowerShell Core estiver a utilizar é oficialmente suportada.</span><span class="sxs-lookup"><span data-stu-id="00b07-122">Please see the following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="00b07-123">Nossa Comunidade também contribuiu pacotes em algumas plataformas, mas não são suportadas oficialmente.</span><span class="sxs-lookup"><span data-stu-id="00b07-123">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="00b07-124">Esses pacotes são marcados como `Community` na tabela.</span><span class="sxs-lookup"><span data-stu-id="00b07-124">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="00b07-125">Plataformas listadas como `Experimental` não serem suportados oficialmente, mas estão disponíveis para a experimentação e comentários.</span><span class="sxs-lookup"><span data-stu-id="00b07-125">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="00b07-126">6.0</span><span class="sxs-lookup"><span data-stu-id="00b07-126">6.0</span></span>         | <span data-ttu-id="00b07-127">6.1</span><span class="sxs-lookup"><span data-stu-id="00b07-127">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="00b07-128">Windows 7, 8.1 e 10</span><span class="sxs-lookup"><span data-stu-id="00b07-128">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="00b07-129">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-129">Supported</span></span>   | <span data-ttu-id="00b07-130">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-130">Supported</span></span>   |
| <span data-ttu-id="00b07-131">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="00b07-131">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="00b07-132">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-132">Supported</span></span>   | <span data-ttu-id="00b07-133">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-133">Supported</span></span>   |
| <span data-ttu-id="00b07-134">[Canal Semianual do Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="00b07-134">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="00b07-135">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-135">Supported</span></span>   | <span data-ttu-id="00b07-136">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-136">Supported</span></span>   |
| <span data-ttu-id="00b07-137">Ubuntu 14.04 e 16.04</span><span class="sxs-lookup"><span data-stu-id="00b07-137">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="00b07-138">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-138">Supported</span></span>   | <span data-ttu-id="00b07-139">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-139">Supported</span></span>   |
| <span data-ttu-id="00b07-140">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="00b07-140">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="00b07-141">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-141">Supported</span></span>   |
| <span data-ttu-id="00b07-142">Ubuntu 18.10 (por meio do ajuste pacote)</span><span class="sxs-lookup"><span data-stu-id="00b07-142">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="00b07-143">Comunidade</span><span class="sxs-lookup"><span data-stu-id="00b07-143">Community</span></span>   |
| <span data-ttu-id="00b07-144">Debian 8,7 + e 9</span><span class="sxs-lookup"><span data-stu-id="00b07-144">Debian 8.7+, and 9</span></span>                                | <span data-ttu-id="00b07-145">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-145">Supported</span></span>   | <span data-ttu-id="00b07-146">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-146">Supported</span></span>   |
| <span data-ttu-id="00b07-147">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="00b07-147">CentOS 7</span></span>                                          | <span data-ttu-id="00b07-148">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-148">Supported</span></span>   | <span data-ttu-id="00b07-149">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-149">Supported</span></span>   |
| <span data-ttu-id="00b07-150">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="00b07-150">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="00b07-151">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-151">Supported</span></span>   | <span data-ttu-id="00b07-152">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-152">Supported</span></span>   |
| <span data-ttu-id="00b07-153">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="00b07-153">OpenSUSE 42.3</span></span>                                     | <span data-ttu-id="00b07-154">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-154">Supported</span></span>   | <span data-ttu-id="00b07-155">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-155">Supported</span></span>   |
| <span data-ttu-id="00b07-156">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="00b07-156">Fedora 27</span></span>                                         | <span data-ttu-id="00b07-157">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-157">Supported</span></span>   | <span data-ttu-id="00b07-158">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-158">Supported</span></span>   |
| <span data-ttu-id="00b07-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="00b07-159">Fedora 28</span></span>                                         |             | <span data-ttu-id="00b07-160">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-160">Supported</span></span>   |
| <span data-ttu-id="00b07-161">macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="00b07-161">macOS 10.12+</span></span>                                      | <span data-ttu-id="00b07-162">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-162">Supported</span></span>   | <span data-ttu-id="00b07-163">Suportada</span><span class="sxs-lookup"><span data-stu-id="00b07-163">Supported</span></span>   |
| <span data-ttu-id="00b07-164">Arch</span><span class="sxs-lookup"><span data-stu-id="00b07-164">Arch</span></span>                                              | <span data-ttu-id="00b07-165">Comunidade</span><span class="sxs-lookup"><span data-stu-id="00b07-165">Community</span></span>   | <span data-ttu-id="00b07-166">Comunidade</span><span class="sxs-lookup"><span data-stu-id="00b07-166">Community</span></span>   |
| <span data-ttu-id="00b07-167">Raspbian</span><span class="sxs-lookup"><span data-stu-id="00b07-167">Raspbian</span></span>                                          | <span data-ttu-id="00b07-168">Experimentais</span><span class="sxs-lookup"><span data-stu-id="00b07-168">Experimental</span></span>| <span data-ttu-id="00b07-169">Comunidade</span><span class="sxs-lookup"><span data-stu-id="00b07-169">Community</span></span>   |
| <span data-ttu-id="00b07-170">Kali</span><span class="sxs-lookup"><span data-stu-id="00b07-170">Kali</span></span>                                              | <span data-ttu-id="00b07-171">Comunidade</span><span class="sxs-lookup"><span data-stu-id="00b07-171">Community</span></span>   | <span data-ttu-id="00b07-172">Comunidade</span><span class="sxs-lookup"><span data-stu-id="00b07-172">Community</span></span>   |
| <span data-ttu-id="00b07-173">AppImage (funciona em várias plataformas Linux)</span><span class="sxs-lookup"><span data-stu-id="00b07-173">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="00b07-174">Comunidade</span><span class="sxs-lookup"><span data-stu-id="00b07-174">Community</span></span>   | <span data-ttu-id="00b07-175">Comunidade</span><span class="sxs-lookup"><span data-stu-id="00b07-175">Community</span></span>   |
| [<span data-ttu-id="00b07-176">Ajustar o pacote</span><span class="sxs-lookup"><span data-stu-id="00b07-176">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="00b07-177">Consulte a nota</span><span class="sxs-lookup"><span data-stu-id="00b07-177">See note</span></span>    | <span data-ttu-id="00b07-178">Consulte a nota</span><span class="sxs-lookup"><span data-stu-id="00b07-178">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="00b07-179">Ajuste pacotes estarão experimentais durante um período.</span><span class="sxs-lookup"><span data-stu-id="00b07-179">Snap packages will be experimental for a period.</span></span>  <span data-ttu-id="00b07-180">Depois, estamos a certeza de que Snap não introduz novos problemas de suporte, o suporte seguirão a distribuição que está a executar o pacote.</span><span class="sxs-lookup"><span data-stu-id="00b07-180">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="platform-which-are-out-of-support"></a><span data-ttu-id="00b07-181">Plataforma que estão fora de suporte</span><span class="sxs-lookup"><span data-stu-id="00b07-181">Platform which are out of support</span></span>

<span data-ttu-id="00b07-182">Quando uma versão de plataforma atinge o fim-de-vida conforme definido pelo proprietário de plataforma, o PowerShell Core também deixará de fornecer suporte para essa versão de plataforma.</span><span class="sxs-lookup"><span data-stu-id="00b07-182">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to provide support for that platform version.</span></span> <span data-ttu-id="00b07-183">Já lançadas pacotes permanecerá disponíveis para clientes que precisam de acesso, mas suporte formal e atualizações de qualquer tipo já não serão fornecidas.</span><span class="sxs-lookup"><span data-stu-id="00b07-183">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="00b07-184">Por conseguinte, o suporte para as seguintes versões foi terminada pelos proprietários de distribuição e não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="00b07-184">Therefore, support for the following versions was ended by the distribution owners and are not supported.</span></span>

| <span data-ttu-id="00b07-185">SO</span><span class="sxs-lookup"><span data-stu-id="00b07-185">OS</span></span>       | <span data-ttu-id="00b07-186">Versão</span><span class="sxs-lookup"><span data-stu-id="00b07-186">Version</span></span> | <span data-ttu-id="00b07-187">Fim de vida</span><span class="sxs-lookup"><span data-stu-id="00b07-187">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="00b07-188">Fedora</span><span class="sxs-lookup"><span data-stu-id="00b07-188">Fedora</span></span>   | <span data-ttu-id="00b07-189">24</span><span class="sxs-lookup"><span data-stu-id="00b07-189">24</span></span>      | [<span data-ttu-id="00b07-190">Agosto de 2017</span><span class="sxs-lookup"><span data-stu-id="00b07-190">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="00b07-191">Fedora</span><span class="sxs-lookup"><span data-stu-id="00b07-191">Fedora</span></span>   | <span data-ttu-id="00b07-192">25</span><span class="sxs-lookup"><span data-stu-id="00b07-192">25</span></span>      | [<span data-ttu-id="00b07-193">Dezembro de 2017</span><span class="sxs-lookup"><span data-stu-id="00b07-193">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="00b07-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="00b07-194">Fedora</span></span>   | <span data-ttu-id="00b07-195">26</span><span class="sxs-lookup"><span data-stu-id="00b07-195">26</span></span>      | [<span data-ttu-id="00b07-196">Maio de 2018</span><span class="sxs-lookup"><span data-stu-id="00b07-196">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="00b07-197">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="00b07-197">openSUSE</span></span> | <span data-ttu-id="00b07-198">42.1</span><span class="sxs-lookup"><span data-stu-id="00b07-198">42.1</span></span>    | [<span data-ttu-id="00b07-199">Maio de 2017</span><span class="sxs-lookup"><span data-stu-id="00b07-199">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="00b07-200">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="00b07-200">openSUSE</span></span> | <span data-ttu-id="00b07-201">42.2</span><span class="sxs-lookup"><span data-stu-id="00b07-201">42.2</span></span>    | [<span data-ttu-id="00b07-202">Janeiro de 2018</span><span class="sxs-lookup"><span data-stu-id="00b07-202">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="00b07-203">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="00b07-203">Ubuntu</span></span>   | <span data-ttu-id="00b07-204">16.10</span><span class="sxs-lookup"><span data-stu-id="00b07-204">16.10</span></span>   | [<span data-ttu-id="00b07-205">Julho de 2017</span><span class="sxs-lookup"><span data-stu-id="00b07-205">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="00b07-206">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="00b07-206">Ubuntu</span></span>   | <span data-ttu-id="00b07-207">17.04</span><span class="sxs-lookup"><span data-stu-id="00b07-207">17.04</span></span>   | [<span data-ttu-id="00b07-208">Janeiro de 2018</span><span class="sxs-lookup"><span data-stu-id="00b07-208">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="00b07-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="00b07-209">Ubuntu</span></span>   | <span data-ttu-id="00b07-210">17.10</span><span class="sxs-lookup"><span data-stu-id="00b07-210">17.10</span></span>   | [<span data-ttu-id="00b07-211">Julho de 2018</span><span class="sxs-lookup"><span data-stu-id="00b07-211">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a><span data-ttu-id="00b07-212">Notas de licenciamento</span><span class="sxs-lookup"><span data-stu-id="00b07-212">Notes on licensing</span></span>

<span data-ttu-id="00b07-213">O PowerShell Core é lançado sob o [licença MIT][].</span><span class="sxs-lookup"><span data-stu-id="00b07-213">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="00b07-214">Sob esta licença e, na ausência de um contrato de suporte pago, os utilizadores estão limitados a [suporte da Comunidade][].</span><span class="sxs-lookup"><span data-stu-id="00b07-214">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="00b07-215">Com o suporte da Comunidade, Microsoft não garante de capacidade de resposta ou correções.</span><span class="sxs-lookup"><span data-stu-id="00b07-215">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="00b07-216">Módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="00b07-216">Windows PowerShell Module</span></span>

<span data-ttu-id="00b07-217">Suporte para o PowerShell Core não se estende para outros módulos de produto, a menos que esses módulos do PowerShell Core tem suporte explícito.</span><span class="sxs-lookup"><span data-stu-id="00b07-217">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="00b07-218">Por exemplo, utilizando o `ActiveDirectory` módulo que é fornecido como parte do Windows Server é um cenário não suportado.</span><span class="sxs-lookup"><span data-stu-id="00b07-218">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="00b07-219">No entanto, os módulos que não suportam explicitamente o PowerShell Core podem ser compatíveis em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="00b07-219">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="00b07-220">Ao instalar o [`WindowsPSModulePath`][] módulo, pode acrescentar o Windows PowerShell `PSModulePath` para o PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="00b07-220">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="00b07-221">Primeiro, instale o `WindowsPSModulePath` módulo a partir da galeria do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="00b07-221">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="00b07-222">Depois de instalar este módulo, execute o `Add-WindowsPSModulePath` cmdlet para adicionar o Windows PowerShell `PSModulePath` para o PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="00b07-222">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[suporte da Comunidade]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[Comunidade tecnológica do PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[o suporte assistido]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Licença MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
