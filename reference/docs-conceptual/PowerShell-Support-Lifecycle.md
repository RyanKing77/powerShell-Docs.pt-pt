---
title: Ciclo de Vida do Suporte do PowerShell Core
description: As políticas que regem suportam para o PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 178e5c43520f9a392ca219b9f785eb18b1ec5436
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086969"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="f0899-103">Ciclo de Vida do Suporte do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="f0899-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="f0899-104">O PowerShell Core é um conjunto distinto de ferramentas e componentes que é entregue, instalado e configurado separadamente a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0899-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="f0899-105">Então, o PowerShell Core não está incluído nos contratos de licenciamento do Windows 7/8.1/10 ou Windows Server.</span><span class="sxs-lookup"><span data-stu-id="f0899-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="f0899-106">No entanto, o PowerShell Core é suportado por tradicionais contratos de suporte da Microsoft, incluindo [Premier][], [contratos Enterprise do Microsoft][enterprise-agreement]e [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="f0899-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="f0899-107">Também pode pagar [o suporte assistido][] para o PowerShell Core através do preenchimento de um pedido de suporte para o seu problema.</span><span class="sxs-lookup"><span data-stu-id="f0899-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="f0899-108">Suporte da Comunidade</span><span class="sxs-lookup"><span data-stu-id="f0899-108">Community Support</span></span>

<span data-ttu-id="f0899-109">Também oferecemos [suporte da Comunidade][] no GitHub onde pode enviar um problema, correção ou pedido de funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="f0899-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="f0899-110">Além disso, pode encontrar a ajuda de outros membros da Comunidade sobre gerais [Microsoft Community][] ou o Microsoft [Comunidade tecnológica do PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="f0899-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="f0899-111">Não oferecemos nenhuma garantia aí que a Comunidade irá abordar ou resolver o problema em tempo hábil.</span><span class="sxs-lookup"><span data-stu-id="f0899-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="f0899-112">Se tiver um problema que requeira atenção imediata, deve usar o tradicional, opções de suporte pago.</span><span class="sxs-lookup"><span data-stu-id="f0899-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="f0899-113">Ciclo de vida do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="f0899-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="f0899-114">Está a adotar o PowerShell Core a [política de ciclo de vida moderno do Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="f0899-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="f0899-115">Este ciclo de vida do suporte destina-se para manter os clientes atualizados com as versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="f0899-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="f0899-116">O ramo do 6.x de versão do PowerShell Core será atualizado aproximadamente uma vez a cada seis meses (exemplos: 6.0, 6.1, 6.2, etc.)</span><span class="sxs-lookup"><span data-stu-id="f0899-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0899-117">Tem de atualizar dentro de seis meses depois de cada nova versão secundária da versão para continuar a receber suporte.</span><span class="sxs-lookup"><span data-stu-id="f0899-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="f0899-118">Por exemplo, se o PowerShell Core 6.1 for lançado no dia 1 de Julho de 2018, esperada para atualizar para o PowerShell Core 6.1 até 1 de Janeiro de 2019 para manter o suporte.</span><span class="sxs-lookup"><span data-stu-id="f0899-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0899-119">Tem de atualizar dentro de 30 dias após cada nova versão de patch de versão para continuar a receber suporte.</span><span class="sxs-lookup"><span data-stu-id="f0899-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="f0899-120">Por exemplo, se estiver a executar o PowerShell Core 6.1 e 6.1.3 foi lançado no dia 19 de Fevereiro de 2019, esperada para atualizar para o PowerShell Core 6.1.3 até 21 de Março de 2019, que é 30 dias após o lançamento para manter o suporte.</span><span class="sxs-lookup"><span data-stu-id="f0899-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="f0899-121">Se quaisquer correções são necessárias, as correções serão lançadas em nossa próxima atualização cumulativa.</span><span class="sxs-lookup"><span data-stu-id="f0899-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

![O ciclo de vida do PowerShell Core ramo][lifecycle-chart]

<span data-ttu-id="f0899-123">A política de ciclo de vida moderno também requer que Microsoft disponibilizar aos clientes aviso de 12 meses antes de interromper o suporte para um produto (ou seja, o PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="f0899-123">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="f0899-124">Por fim, podemos esperar o PowerShell Core irá adotar o "longo prazo de manutenção" abordagem.</span><span class="sxs-lookup"><span data-stu-id="f0899-124">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="f0899-125">Nesta abordagem de manutenção, vamos exigiria apenas de manutenção e atualizações de segurança para se manter em suporte numa filial/versão específica do 6.x.</span><span class="sxs-lookup"><span data-stu-id="f0899-125">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="f0899-126">Plataformas suportadas</span><span class="sxs-lookup"><span data-stu-id="f0899-126">Supported platforms</span></span>

<span data-ttu-id="f0899-127">A tabela seguinte para ver qual plataforma a versão do PowerShell Core estiver a utilizar é oficialmente suportada.</span><span class="sxs-lookup"><span data-stu-id="f0899-127">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="f0899-128">Nossa Comunidade também contribuiu pacotes em algumas plataformas, mas não são suportadas oficialmente.</span><span class="sxs-lookup"><span data-stu-id="f0899-128">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="f0899-129">Esses pacotes são marcados como `Community` na tabela.</span><span class="sxs-lookup"><span data-stu-id="f0899-129">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="f0899-130">Plataformas listadas como `Experimental` não serem suportados oficialmente, mas estão disponíveis para a experimentação e comentários.</span><span class="sxs-lookup"><span data-stu-id="f0899-130">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="f0899-131">6.1</span><span class="sxs-lookup"><span data-stu-id="f0899-131">6.1</span></span>         | <span data-ttu-id="f0899-132">6.2</span><span class="sxs-lookup"><span data-stu-id="f0899-132">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="f0899-133">Windows 7, 8.1 e 10</span><span class="sxs-lookup"><span data-stu-id="f0899-133">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="f0899-134">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-134">Supported</span></span>   | <span data-ttu-id="f0899-135">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-135">Supported</span></span>   |
| <span data-ttu-id="f0899-136">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="f0899-136">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="f0899-137">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-137">Supported</span></span>   | <span data-ttu-id="f0899-138">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-138">Supported</span></span>   |
| <span data-ttu-id="f0899-139">[Canal Semianual do Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="f0899-139">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="f0899-140">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-140">Supported</span></span>   | <span data-ttu-id="f0899-141">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-141">Supported</span></span>   |
| <span data-ttu-id="f0899-142">Ubuntu 16.04 e 18.04</span><span class="sxs-lookup"><span data-stu-id="f0899-142">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="f0899-143">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-143">Supported</span></span>   | <span data-ttu-id="f0899-144">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-144">Supported</span></span>   |
| <span data-ttu-id="f0899-145">Ubuntu 18.10 (por meio do ajuste pacote)</span><span class="sxs-lookup"><span data-stu-id="f0899-145">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="f0899-146">Comunidade</span><span class="sxs-lookup"><span data-stu-id="f0899-146">Community</span></span>   | <span data-ttu-id="f0899-147">Comunidade</span><span class="sxs-lookup"><span data-stu-id="f0899-147">Community</span></span>   |
| <span data-ttu-id="f0899-148">Debian 9</span><span class="sxs-lookup"><span data-stu-id="f0899-148">Debian 9</span></span>                                          | <span data-ttu-id="f0899-149">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-149">Supported</span></span>   | <span data-ttu-id="f0899-150">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-150">Supported</span></span>   |
| <span data-ttu-id="f0899-151">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f0899-151">CentOS 7</span></span>                                          | <span data-ttu-id="f0899-152">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-152">Supported</span></span>   | <span data-ttu-id="f0899-153">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-153">Supported</span></span>   |
| <span data-ttu-id="f0899-154">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="f0899-154">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="f0899-155">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-155">Supported</span></span>   | <span data-ttu-id="f0899-156">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-156">Supported</span></span>   |
| <span data-ttu-id="f0899-157">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="f0899-157">openSUSE 42.3</span></span>                                     | <span data-ttu-id="f0899-158">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-158">Supported</span></span>   | <span data-ttu-id="f0899-159">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-159">Supported</span></span>   |
| <span data-ttu-id="f0899-160">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="f0899-160">Fedora 28</span></span>                                         | <span data-ttu-id="f0899-161">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-161">Supported</span></span>   | <span data-ttu-id="f0899-162">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-162">Supported</span></span>   |
| <span data-ttu-id="f0899-163">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="f0899-163">macOS 10.12+</span></span>                                      | <span data-ttu-id="f0899-164">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-164">Supported</span></span>   | <span data-ttu-id="f0899-165">Suportado</span><span class="sxs-lookup"><span data-stu-id="f0899-165">Supported</span></span>   |
| <span data-ttu-id="f0899-166">Arch</span><span class="sxs-lookup"><span data-stu-id="f0899-166">Arch</span></span>                                              | <span data-ttu-id="f0899-167">Comunidade</span><span class="sxs-lookup"><span data-stu-id="f0899-167">Community</span></span>   | <span data-ttu-id="f0899-168">Comunidade</span><span class="sxs-lookup"><span data-stu-id="f0899-168">Community</span></span>   |
| <span data-ttu-id="f0899-169">Raspbian</span><span class="sxs-lookup"><span data-stu-id="f0899-169">Raspbian</span></span>                                          | <span data-ttu-id="f0899-170">Comunidade</span><span class="sxs-lookup"><span data-stu-id="f0899-170">Community</span></span>   | <span data-ttu-id="f0899-171">Comunidade</span><span class="sxs-lookup"><span data-stu-id="f0899-171">Community</span></span>   |
| <span data-ttu-id="f0899-172">Kali</span><span class="sxs-lookup"><span data-stu-id="f0899-172">Kali</span></span>                                              | <span data-ttu-id="f0899-173">Comunidade</span><span class="sxs-lookup"><span data-stu-id="f0899-173">Community</span></span>   | <span data-ttu-id="f0899-174">Comunidade</span><span class="sxs-lookup"><span data-stu-id="f0899-174">Community</span></span>   |
| <span data-ttu-id="f0899-175">AppImage (funciona em várias plataformas Linux)</span><span class="sxs-lookup"><span data-stu-id="f0899-175">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="f0899-176">Comunidade</span><span class="sxs-lookup"><span data-stu-id="f0899-176">Community</span></span>   | <span data-ttu-id="f0899-177">Comunidade</span><span class="sxs-lookup"><span data-stu-id="f0899-177">Community</span></span>   |
| [<span data-ttu-id="f0899-178">Ajustar o pacote</span><span class="sxs-lookup"><span data-stu-id="f0899-178">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="f0899-179">Consulte a nota</span><span class="sxs-lookup"><span data-stu-id="f0899-179">See note</span></span>    | <span data-ttu-id="f0899-180">Consulte a nota</span><span class="sxs-lookup"><span data-stu-id="f0899-180">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="f0899-181">Ajustar os pacotes são suportados o mesmo que a distribuição estiver a executar o pacote no.</span><span class="sxs-lookup"><span data-stu-id="f0899-181">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="f0899-182">PowerShell versão final de vida</span><span class="sxs-lookup"><span data-stu-id="f0899-182">PowerShell release end of life</span></span>

<span data-ttu-id="f0899-183">Com base na [ciclo de vida do PowerShell Core](#lifecycle-of-powershell-core), a tabela seguinte lista as datas de lançamento vários quando já não será suportado.</span><span class="sxs-lookup"><span data-stu-id="f0899-183">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="f0899-184">Versão</span><span class="sxs-lookup"><span data-stu-id="f0899-184">Version</span></span> | <span data-ttu-id="f0899-185">Fim de vida</span><span class="sxs-lookup"><span data-stu-id="f0899-185">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="f0899-186">6.0</span><span class="sxs-lookup"><span data-stu-id="f0899-186">6.0</span></span>     | <span data-ttu-id="f0899-187">13 de Fevereiro de 2019</span><span class="sxs-lookup"><span data-stu-id="f0899-187">February 13, 2019</span></span>             |
| <span data-ttu-id="f0899-188">6.1</span><span class="sxs-lookup"><span data-stu-id="f0899-188">6.1</span></span>     | <span data-ttu-id="f0899-189">28 de Setembro de 2019</span><span class="sxs-lookup"><span data-stu-id="f0899-189">September 28, 2019</span></span>            |
| <span data-ttu-id="f0899-190">6.2</span><span class="sxs-lookup"><span data-stu-id="f0899-190">6.2</span></span>     | <span data-ttu-id="f0899-191">versões de seis meses a 6.3</span><span class="sxs-lookup"><span data-stu-id="f0899-191">6 months after 6.3 releases</span></span>   |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="f0899-192">Plataformas, que estão fora de suporte</span><span class="sxs-lookup"><span data-stu-id="f0899-192">Platforms, which are out of support</span></span>

<span data-ttu-id="f0899-193">Quando uma versão de plataforma atinge o final da vida, conforme definido pelo proprietário de plataforma, o PowerShell Core também deixará de suportar essa versão de plataforma.</span><span class="sxs-lookup"><span data-stu-id="f0899-193">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="f0899-194">Já lançadas pacotes permanecerá disponíveis para clientes que precisam de acesso, mas suporte formal e atualizações de qualquer tipo já não serão fornecidas.</span><span class="sxs-lookup"><span data-stu-id="f0899-194">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="f0899-195">Então, os proprietários de distribuição terminou o suporte para as seguintes versões e não são suportados.</span><span class="sxs-lookup"><span data-stu-id="f0899-195">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="f0899-196">SO</span><span class="sxs-lookup"><span data-stu-id="f0899-196">OS</span></span>       | <span data-ttu-id="f0899-197">Versão</span><span class="sxs-lookup"><span data-stu-id="f0899-197">Version</span></span> | <span data-ttu-id="f0899-198">Fim de vida</span><span class="sxs-lookup"><span data-stu-id="f0899-198">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="f0899-199">Fedora</span><span class="sxs-lookup"><span data-stu-id="f0899-199">Fedora</span></span>   | <span data-ttu-id="f0899-200">24</span><span class="sxs-lookup"><span data-stu-id="f0899-200">24</span></span>      | [<span data-ttu-id="f0899-201">Agosto de 2017</span><span class="sxs-lookup"><span data-stu-id="f0899-201">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="f0899-202">Fedora</span><span class="sxs-lookup"><span data-stu-id="f0899-202">Fedora</span></span>   | <span data-ttu-id="f0899-203">25</span><span class="sxs-lookup"><span data-stu-id="f0899-203">25</span></span>      | [<span data-ttu-id="f0899-204">Dezembro de 2017</span><span class="sxs-lookup"><span data-stu-id="f0899-204">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="f0899-205">Fedora</span><span class="sxs-lookup"><span data-stu-id="f0899-205">Fedora</span></span>   | <span data-ttu-id="f0899-206">26</span><span class="sxs-lookup"><span data-stu-id="f0899-206">26</span></span>      | [<span data-ttu-id="f0899-207">Maio de 2018</span><span class="sxs-lookup"><span data-stu-id="f0899-207">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="f0899-208">openSUSE</span><span class="sxs-lookup"><span data-stu-id="f0899-208">openSUSE</span></span> | <span data-ttu-id="f0899-209">42.1</span><span class="sxs-lookup"><span data-stu-id="f0899-209">42.1</span></span>    | [<span data-ttu-id="f0899-210">Maio de 2017</span><span class="sxs-lookup"><span data-stu-id="f0899-210">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="f0899-211">openSUSE</span><span class="sxs-lookup"><span data-stu-id="f0899-211">openSUSE</span></span> | <span data-ttu-id="f0899-212">42.2</span><span class="sxs-lookup"><span data-stu-id="f0899-212">42.2</span></span>    | [<span data-ttu-id="f0899-213">Janeiro de 2018</span><span class="sxs-lookup"><span data-stu-id="f0899-213">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="f0899-214">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f0899-214">Ubuntu</span></span>   | <span data-ttu-id="f0899-215">16.10</span><span class="sxs-lookup"><span data-stu-id="f0899-215">16.10</span></span>   | [<span data-ttu-id="f0899-216">Julho de 2017</span><span class="sxs-lookup"><span data-stu-id="f0899-216">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="f0899-217">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f0899-217">Ubuntu</span></span>   | <span data-ttu-id="f0899-218">17.04</span><span class="sxs-lookup"><span data-stu-id="f0899-218">17.04</span></span>   | [<span data-ttu-id="f0899-219">Janeiro de 2018</span><span class="sxs-lookup"><span data-stu-id="f0899-219">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="f0899-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f0899-220">Ubuntu</span></span>   | <span data-ttu-id="f0899-221">17.10</span><span class="sxs-lookup"><span data-stu-id="f0899-221">17.10</span></span>   | [<span data-ttu-id="f0899-222">Julho de 2018</span><span class="sxs-lookup"><span data-stu-id="f0899-222">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="f0899-223">Debian</span><span class="sxs-lookup"><span data-stu-id="f0899-223">Debian</span></span>   | <span data-ttu-id="f0899-224">8</span><span class="sxs-lookup"><span data-stu-id="f0899-224">8</span></span>       | [<span data-ttu-id="f0899-225">Junho de 2018</span><span class="sxs-lookup"><span data-stu-id="f0899-225">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="f0899-226">Fedora</span><span class="sxs-lookup"><span data-stu-id="f0899-226">Fedora</span></span>   | <span data-ttu-id="f0899-227">27</span><span class="sxs-lookup"><span data-stu-id="f0899-227">27</span></span>      | [<span data-ttu-id="f0899-228">Novembro de 2018</span><span class="sxs-lookup"><span data-stu-id="f0899-228">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="f0899-229">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f0899-229">Ubuntu</span></span>   | <span data-ttu-id="f0899-230">14.04</span><span class="sxs-lookup"><span data-stu-id="f0899-230">14.04</span></span>   | [<span data-ttu-id="f0899-231">Abril de 2019</span><span class="sxs-lookup"><span data-stu-id="f0899-231">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="f0899-232">Notas de licenciamento</span><span class="sxs-lookup"><span data-stu-id="f0899-232">Notes on licensing</span></span>

<span data-ttu-id="f0899-233">O PowerShell Core é lançado sob o [licença MIT][].</span><span class="sxs-lookup"><span data-stu-id="f0899-233">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="f0899-234">Sob esta licença e sem um contrato de suporte pago, os utilizadores estão limitados a [suporte da Comunidade][].</span><span class="sxs-lookup"><span data-stu-id="f0899-234">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="f0899-235">Com o suporte da Comunidade, Microsoft não garante de capacidade de resposta ou correções.</span><span class="sxs-lookup"><span data-stu-id="f0899-235">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="f0899-236">Módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f0899-236">Windows PowerShell Module</span></span>

<span data-ttu-id="f0899-237">Suporte para o PowerShell Core não inclui módulos do produto, a menos que esses módulos do PowerShell Core tem suporte explícito.</span><span class="sxs-lookup"><span data-stu-id="f0899-237">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="f0899-238">Por exemplo, utilizando o `ActiveDirectory` módulo que é fornecido como parte do Windows Server é um cenário não suportado.</span><span class="sxs-lookup"><span data-stu-id="f0899-238">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="f0899-239">No entanto, os módulos que não suportam explicitamente o PowerShell Core podem ser compatíveis em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="f0899-239">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="f0899-240">Ao instalar o [ `WindowsPSModulePath` ][] módulo, pode adicionar o Windows PowerShell `PSModulePath` para o PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="f0899-240">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="f0899-241">Primeiro, instale o `WindowsPSModulePath` módulo a partir da galeria do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f0899-241">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="f0899-242">Depois de instalar este módulo, execute o `Add-WindowsPSModulePath` cmdlet para adicionar o Windows PowerShell `PSModulePath` para o PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="f0899-242">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="f0899-243">Funcionalidades experimentais</span><span class="sxs-lookup"><span data-stu-id="f0899-243">Experimental features</span></span>

<span data-ttu-id="f0899-244">[Funcionalidades experimentais][] estão limitados a [suporte da Comunidade](#community-support).</span><span class="sxs-lookup"><span data-stu-id="f0899-244">[Experimental features][] are limited to [community support](#community-support).</span></span>

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Suporte da Comunidade]: https://github.com/powershell/powershell/issues
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
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Funcionalidades experimentais]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
