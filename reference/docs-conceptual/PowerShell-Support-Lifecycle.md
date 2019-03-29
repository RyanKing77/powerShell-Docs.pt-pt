---
title: Ciclo de Vida do Suporte do PowerShell Core
description: As políticas que regem suportam para o PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 178e5c43520f9a392ca219b9f785eb18b1ec5436
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623863"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="12b61-103">Ciclo de Vida do Suporte do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="12b61-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="12b61-104">O PowerShell Core é um conjunto distinto de ferramentas e componentes que é entregue, instalado e configurado separadamente a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12b61-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="12b61-105">Então, o PowerShell Core não está incluído nos contratos de licenciamento do Windows 7/8.1/10 ou Windows Server.</span><span class="sxs-lookup"><span data-stu-id="12b61-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="12b61-106">No entanto, o PowerShell Core é suportado por tradicionais contratos de suporte da Microsoft, incluindo [Premier][], [contratos Enterprise do Microsoft][enterprise-agreement]e [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="12b61-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="12b61-107">Também pode pagar [o suporte assistido][] para o PowerShell Core através do preenchimento de um pedido de suporte para o seu problema.</span><span class="sxs-lookup"><span data-stu-id="12b61-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="12b61-108">Suporte da Comunidade</span><span class="sxs-lookup"><span data-stu-id="12b61-108">Community Support</span></span>

<span data-ttu-id="12b61-109">Também oferecemos [suporte da Comunidade][] no GitHub onde pode enviar um problema, correção ou pedido de funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="12b61-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="12b61-110">Além disso, pode encontrar a ajuda de outros membros da Comunidade sobre gerais [Microsoft Community][] ou o Microsoft [Comunidade tecnológica do PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="12b61-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="12b61-111">Não oferecemos nenhuma garantia aí que a Comunidade irá abordar ou resolver o problema em tempo hábil.</span><span class="sxs-lookup"><span data-stu-id="12b61-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="12b61-112">Se tiver um problema que requeira atenção imediata, deve usar o tradicional, opções de suporte pago.</span><span class="sxs-lookup"><span data-stu-id="12b61-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="12b61-113">Ciclo de vida do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="12b61-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="12b61-114">Está a adotar o PowerShell Core a [política de ciclo de vida moderno do Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="12b61-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="12b61-115">Este ciclo de vida do suporte destina-se para manter os clientes atualizados com as versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="12b61-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="12b61-116">O ramo do 6.x de versão do PowerShell Core será atualizado aproximadamente uma vez a cada seis meses (exemplos: 6.0, 6.1, 6.2, etc.)</span><span class="sxs-lookup"><span data-stu-id="12b61-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="12b61-117">Tem de atualizar dentro de seis meses depois de cada nova versão secundária da versão para continuar a receber suporte.</span><span class="sxs-lookup"><span data-stu-id="12b61-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="12b61-118">Por exemplo, se o PowerShell Core 6.1 for lançado no dia 1 de Julho de 2018, esperada para atualizar para o PowerShell Core 6.1 até 1 de Janeiro de 2019 para manter o suporte.</span><span class="sxs-lookup"><span data-stu-id="12b61-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="12b61-119">Tem de atualizar dentro de 30 dias após cada nova versão de patch de versão para continuar a receber suporte.</span><span class="sxs-lookup"><span data-stu-id="12b61-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="12b61-120">Por exemplo, se estiver a executar o PowerShell Core 6.1 e 6.1.3 foi lançado no dia 19 de Fevereiro de 2019, esperada para atualizar para o PowerShell Core 6.1.3 até 21 de Março de 2019, que é 30 dias após o lançamento para manter o suporte.</span><span class="sxs-lookup"><span data-stu-id="12b61-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="12b61-121">Se quaisquer correções são necessárias, as correções serão lançadas em nossa próxima atualização cumulativa.</span><span class="sxs-lookup"><span data-stu-id="12b61-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

![O ciclo de vida do PowerShell Core ramo][lifecycle-chart]

<span data-ttu-id="12b61-123">A política de ciclo de vida moderno também requer que Microsoft disponibilizar aos clientes aviso de 12 meses antes de interromper o suporte para um produto (ou seja, o PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="12b61-123">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="12b61-124">Por fim, podemos esperar o PowerShell Core irá adotar o "longo prazo de manutenção" abordagem.</span><span class="sxs-lookup"><span data-stu-id="12b61-124">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="12b61-125">Nesta abordagem de manutenção, vamos exigiria apenas de manutenção e atualizações de segurança para se manter em suporte numa filial/versão específica do 6.x.</span><span class="sxs-lookup"><span data-stu-id="12b61-125">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="12b61-126">Plataformas suportadas</span><span class="sxs-lookup"><span data-stu-id="12b61-126">Supported platforms</span></span>

<span data-ttu-id="12b61-127">A tabela seguinte para ver qual plataforma a versão do PowerShell Core estiver a utilizar é oficialmente suportada.</span><span class="sxs-lookup"><span data-stu-id="12b61-127">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="12b61-128">Nossa Comunidade também contribuiu pacotes em algumas plataformas, mas não são suportadas oficialmente.</span><span class="sxs-lookup"><span data-stu-id="12b61-128">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="12b61-129">Esses pacotes são marcados como `Community` na tabela.</span><span class="sxs-lookup"><span data-stu-id="12b61-129">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="12b61-130">Plataformas listadas como `Experimental` não serem suportados oficialmente, mas estão disponíveis para a experimentação e comentários.</span><span class="sxs-lookup"><span data-stu-id="12b61-130">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="12b61-131">6.1</span><span class="sxs-lookup"><span data-stu-id="12b61-131">6.1</span></span>         | <span data-ttu-id="12b61-132">6.2</span><span class="sxs-lookup"><span data-stu-id="12b61-132">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="12b61-133">Windows 7, 8.1 e 10</span><span class="sxs-lookup"><span data-stu-id="12b61-133">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="12b61-134">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-134">Supported</span></span>   | <span data-ttu-id="12b61-135">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-135">Supported</span></span>   |
| <span data-ttu-id="12b61-136">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="12b61-136">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="12b61-137">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-137">Supported</span></span>   | <span data-ttu-id="12b61-138">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-138">Supported</span></span>   |
| <span data-ttu-id="12b61-139">[Canal Semianual do Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="12b61-139">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="12b61-140">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-140">Supported</span></span>   | <span data-ttu-id="12b61-141">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-141">Supported</span></span>   |
| <span data-ttu-id="12b61-142">Ubuntu 16.04 e 18.04</span><span class="sxs-lookup"><span data-stu-id="12b61-142">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="12b61-143">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-143">Supported</span></span>   | <span data-ttu-id="12b61-144">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-144">Supported</span></span>   |
| <span data-ttu-id="12b61-145">Ubuntu 18.10 (por meio do ajuste pacote)</span><span class="sxs-lookup"><span data-stu-id="12b61-145">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="12b61-146">Comunidade</span><span class="sxs-lookup"><span data-stu-id="12b61-146">Community</span></span>   | <span data-ttu-id="12b61-147">Comunidade</span><span class="sxs-lookup"><span data-stu-id="12b61-147">Community</span></span>   |
| <span data-ttu-id="12b61-148">Debian 9</span><span class="sxs-lookup"><span data-stu-id="12b61-148">Debian 9</span></span>                                          | <span data-ttu-id="12b61-149">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-149">Supported</span></span>   | <span data-ttu-id="12b61-150">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-150">Supported</span></span>   |
| <span data-ttu-id="12b61-151">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="12b61-151">CentOS 7</span></span>                                          | <span data-ttu-id="12b61-152">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-152">Supported</span></span>   | <span data-ttu-id="12b61-153">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-153">Supported</span></span>   |
| <span data-ttu-id="12b61-154">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="12b61-154">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="12b61-155">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-155">Supported</span></span>   | <span data-ttu-id="12b61-156">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-156">Supported</span></span>   |
| <span data-ttu-id="12b61-157">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="12b61-157">openSUSE 42.3</span></span>                                     | <span data-ttu-id="12b61-158">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-158">Supported</span></span>   | <span data-ttu-id="12b61-159">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-159">Supported</span></span>   |
| <span data-ttu-id="12b61-160">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="12b61-160">Fedora 28</span></span>                                         | <span data-ttu-id="12b61-161">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-161">Supported</span></span>   | <span data-ttu-id="12b61-162">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-162">Supported</span></span>   |
| <span data-ttu-id="12b61-163">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="12b61-163">macOS 10.12+</span></span>                                      | <span data-ttu-id="12b61-164">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-164">Supported</span></span>   | <span data-ttu-id="12b61-165">Suportado</span><span class="sxs-lookup"><span data-stu-id="12b61-165">Supported</span></span>   |
| <span data-ttu-id="12b61-166">Arch</span><span class="sxs-lookup"><span data-stu-id="12b61-166">Arch</span></span>                                              | <span data-ttu-id="12b61-167">Comunidade</span><span class="sxs-lookup"><span data-stu-id="12b61-167">Community</span></span>   | <span data-ttu-id="12b61-168">Comunidade</span><span class="sxs-lookup"><span data-stu-id="12b61-168">Community</span></span>   |
| <span data-ttu-id="12b61-169">Raspbian</span><span class="sxs-lookup"><span data-stu-id="12b61-169">Raspbian</span></span>                                          | <span data-ttu-id="12b61-170">Comunidade</span><span class="sxs-lookup"><span data-stu-id="12b61-170">Community</span></span>   | <span data-ttu-id="12b61-171">Comunidade</span><span class="sxs-lookup"><span data-stu-id="12b61-171">Community</span></span>   |
| <span data-ttu-id="12b61-172">Kali</span><span class="sxs-lookup"><span data-stu-id="12b61-172">Kali</span></span>                                              | <span data-ttu-id="12b61-173">Comunidade</span><span class="sxs-lookup"><span data-stu-id="12b61-173">Community</span></span>   | <span data-ttu-id="12b61-174">Comunidade</span><span class="sxs-lookup"><span data-stu-id="12b61-174">Community</span></span>   |
| <span data-ttu-id="12b61-175">AppImage (funciona em várias plataformas Linux)</span><span class="sxs-lookup"><span data-stu-id="12b61-175">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="12b61-176">Comunidade</span><span class="sxs-lookup"><span data-stu-id="12b61-176">Community</span></span>   | <span data-ttu-id="12b61-177">Comunidade</span><span class="sxs-lookup"><span data-stu-id="12b61-177">Community</span></span>   |
| [<span data-ttu-id="12b61-178">Ajustar o pacote</span><span class="sxs-lookup"><span data-stu-id="12b61-178">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="12b61-179">Consulte a nota</span><span class="sxs-lookup"><span data-stu-id="12b61-179">See note</span></span>    | <span data-ttu-id="12b61-180">Consulte a nota</span><span class="sxs-lookup"><span data-stu-id="12b61-180">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="12b61-181">Ajustar os pacotes são suportados o mesmo que a distribuição estiver a executar o pacote no.</span><span class="sxs-lookup"><span data-stu-id="12b61-181">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="12b61-182">PowerShell versão final de vida</span><span class="sxs-lookup"><span data-stu-id="12b61-182">PowerShell release end of life</span></span>

<span data-ttu-id="12b61-183">Com base na [ciclo de vida do PowerShell Core](#lifecycle-of-powershell-core), a tabela seguinte lista as datas de lançamento vários quando já não será suportado.</span><span class="sxs-lookup"><span data-stu-id="12b61-183">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="12b61-184">Versão</span><span class="sxs-lookup"><span data-stu-id="12b61-184">Version</span></span> | <span data-ttu-id="12b61-185">Fim de vida</span><span class="sxs-lookup"><span data-stu-id="12b61-185">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="12b61-186">6.0</span><span class="sxs-lookup"><span data-stu-id="12b61-186">6.0</span></span>     | <span data-ttu-id="12b61-187">13 de Fevereiro de 2019</span><span class="sxs-lookup"><span data-stu-id="12b61-187">February 13, 2019</span></span>             |
| <span data-ttu-id="12b61-188">6.1</span><span class="sxs-lookup"><span data-stu-id="12b61-188">6.1</span></span>     | <span data-ttu-id="12b61-189">28 de Setembro de 2019</span><span class="sxs-lookup"><span data-stu-id="12b61-189">September 28, 2019</span></span>            |
| <span data-ttu-id="12b61-190">6.2</span><span class="sxs-lookup"><span data-stu-id="12b61-190">6.2</span></span>     | <span data-ttu-id="12b61-191">versões de seis meses a 6.3</span><span class="sxs-lookup"><span data-stu-id="12b61-191">6 months after 6.3 releases</span></span>   |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="12b61-192">Plataformas, que estão fora de suporte</span><span class="sxs-lookup"><span data-stu-id="12b61-192">Platforms, which are out of support</span></span>

<span data-ttu-id="12b61-193">Quando uma versão de plataforma atinge o final da vida, conforme definido pelo proprietário de plataforma, o PowerShell Core também deixará de suportar essa versão de plataforma.</span><span class="sxs-lookup"><span data-stu-id="12b61-193">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="12b61-194">Já lançadas pacotes permanecerá disponíveis para clientes que precisam de acesso, mas suporte formal e atualizações de qualquer tipo já não serão fornecidas.</span><span class="sxs-lookup"><span data-stu-id="12b61-194">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="12b61-195">Então, os proprietários de distribuição terminou o suporte para as seguintes versões e não são suportados.</span><span class="sxs-lookup"><span data-stu-id="12b61-195">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="12b61-196">SO</span><span class="sxs-lookup"><span data-stu-id="12b61-196">OS</span></span>       | <span data-ttu-id="12b61-197">Versão</span><span class="sxs-lookup"><span data-stu-id="12b61-197">Version</span></span> | <span data-ttu-id="12b61-198">Fim de vida</span><span class="sxs-lookup"><span data-stu-id="12b61-198">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="12b61-199">Fedora</span><span class="sxs-lookup"><span data-stu-id="12b61-199">Fedora</span></span>   | <span data-ttu-id="12b61-200">24</span><span class="sxs-lookup"><span data-stu-id="12b61-200">24</span></span>      | [<span data-ttu-id="12b61-201">Agosto de 2017</span><span class="sxs-lookup"><span data-stu-id="12b61-201">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="12b61-202">Fedora</span><span class="sxs-lookup"><span data-stu-id="12b61-202">Fedora</span></span>   | <span data-ttu-id="12b61-203">25</span><span class="sxs-lookup"><span data-stu-id="12b61-203">25</span></span>      | [<span data-ttu-id="12b61-204">Dezembro de 2017</span><span class="sxs-lookup"><span data-stu-id="12b61-204">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="12b61-205">Fedora</span><span class="sxs-lookup"><span data-stu-id="12b61-205">Fedora</span></span>   | <span data-ttu-id="12b61-206">26</span><span class="sxs-lookup"><span data-stu-id="12b61-206">26</span></span>      | [<span data-ttu-id="12b61-207">Maio de 2018</span><span class="sxs-lookup"><span data-stu-id="12b61-207">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="12b61-208">openSUSE</span><span class="sxs-lookup"><span data-stu-id="12b61-208">openSUSE</span></span> | <span data-ttu-id="12b61-209">42.1</span><span class="sxs-lookup"><span data-stu-id="12b61-209">42.1</span></span>    | [<span data-ttu-id="12b61-210">Maio de 2017</span><span class="sxs-lookup"><span data-stu-id="12b61-210">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="12b61-211">openSUSE</span><span class="sxs-lookup"><span data-stu-id="12b61-211">openSUSE</span></span> | <span data-ttu-id="12b61-212">42.2</span><span class="sxs-lookup"><span data-stu-id="12b61-212">42.2</span></span>    | [<span data-ttu-id="12b61-213">Janeiro de 2018</span><span class="sxs-lookup"><span data-stu-id="12b61-213">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="12b61-214">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="12b61-214">Ubuntu</span></span>   | <span data-ttu-id="12b61-215">16.10</span><span class="sxs-lookup"><span data-stu-id="12b61-215">16.10</span></span>   | [<span data-ttu-id="12b61-216">Julho de 2017</span><span class="sxs-lookup"><span data-stu-id="12b61-216">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="12b61-217">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="12b61-217">Ubuntu</span></span>   | <span data-ttu-id="12b61-218">17.04</span><span class="sxs-lookup"><span data-stu-id="12b61-218">17.04</span></span>   | [<span data-ttu-id="12b61-219">Janeiro de 2018</span><span class="sxs-lookup"><span data-stu-id="12b61-219">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="12b61-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="12b61-220">Ubuntu</span></span>   | <span data-ttu-id="12b61-221">17.10</span><span class="sxs-lookup"><span data-stu-id="12b61-221">17.10</span></span>   | [<span data-ttu-id="12b61-222">Julho de 2018</span><span class="sxs-lookup"><span data-stu-id="12b61-222">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="12b61-223">Debian</span><span class="sxs-lookup"><span data-stu-id="12b61-223">Debian</span></span>   | <span data-ttu-id="12b61-224">8</span><span class="sxs-lookup"><span data-stu-id="12b61-224">8</span></span>       | [<span data-ttu-id="12b61-225">Junho de 2018</span><span class="sxs-lookup"><span data-stu-id="12b61-225">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="12b61-226">Fedora</span><span class="sxs-lookup"><span data-stu-id="12b61-226">Fedora</span></span>   | <span data-ttu-id="12b61-227">27</span><span class="sxs-lookup"><span data-stu-id="12b61-227">27</span></span>      | [<span data-ttu-id="12b61-228">Novembro de 2018</span><span class="sxs-lookup"><span data-stu-id="12b61-228">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="12b61-229">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="12b61-229">Ubuntu</span></span>   | <span data-ttu-id="12b61-230">14.04</span><span class="sxs-lookup"><span data-stu-id="12b61-230">14.04</span></span>   | [<span data-ttu-id="12b61-231">Abril de 2019</span><span class="sxs-lookup"><span data-stu-id="12b61-231">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="12b61-232">Notas de licenciamento</span><span class="sxs-lookup"><span data-stu-id="12b61-232">Notes on licensing</span></span>

<span data-ttu-id="12b61-233">O PowerShell Core é lançado sob o [licença MIT][].</span><span class="sxs-lookup"><span data-stu-id="12b61-233">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="12b61-234">Sob esta licença e sem um contrato de suporte pago, os utilizadores estão limitados a [suporte da Comunidade][].</span><span class="sxs-lookup"><span data-stu-id="12b61-234">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="12b61-235">Com o suporte da Comunidade, Microsoft não garante de capacidade de resposta ou correções.</span><span class="sxs-lookup"><span data-stu-id="12b61-235">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="12b61-236">Módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="12b61-236">Windows PowerShell Module</span></span>

<span data-ttu-id="12b61-237">Suporte para o PowerShell Core não inclui módulos do produto, a menos que esses módulos do PowerShell Core tem suporte explícito.</span><span class="sxs-lookup"><span data-stu-id="12b61-237">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="12b61-238">Por exemplo, utilizando o `ActiveDirectory` módulo que é fornecido como parte do Windows Server é um cenário não suportado.</span><span class="sxs-lookup"><span data-stu-id="12b61-238">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="12b61-239">No entanto, os módulos que não suportam explicitamente o PowerShell Core podem ser compatíveis em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="12b61-239">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="12b61-240">Ao instalar o [ `WindowsPSModulePath` ][] módulo, pode adicionar o Windows PowerShell `PSModulePath` para o PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="12b61-240">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="12b61-241">Primeiro, instale o `WindowsPSModulePath` módulo a partir da galeria do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="12b61-241">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="12b61-242">Depois de instalar este módulo, execute o `Add-WindowsPSModulePath` cmdlet para adicionar o Windows PowerShell `PSModulePath` para o PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="12b61-242">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="12b61-243">Funcionalidades experimentais</span><span class="sxs-lookup"><span data-stu-id="12b61-243">Experimental features</span></span>

<span data-ttu-id="12b61-244">[Funcionalidades experimentais][] estão limitados a [suporte da Comunidade](#community-support).</span><span class="sxs-lookup"><span data-stu-id="12b61-244">[Experimental features][] are limited to [community support](#community-support).</span></span>

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
