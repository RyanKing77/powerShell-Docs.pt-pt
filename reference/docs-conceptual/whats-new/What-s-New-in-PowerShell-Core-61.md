---
title: Quais são as novidades no PowerShell Core 6.1
description: Novos recursos e alterações lançadas no PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 27e7e846e9ba6ab34d83a084c2589b67a9d5cba9
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557317"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="fc66f-103">Quais são as novidades no PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="fc66f-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="fc66f-104">Segue-se uma seleção de alguns dos principais novos recursos e alterações que foram introduzidas no PowerShell Core 6.1.</span><span class="sxs-lookup"><span data-stu-id="fc66f-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="fc66f-105">Também há **toneladas** de "aborrecida" que tornam o PowerShell mais rápido e mais estável (além de muitas e várias correções de erros)!</span><span class="sxs-lookup"><span data-stu-id="fc66f-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="fc66f-106">Para obter uma lista completa das alterações, confira nossos [registo de alterações no GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="fc66f-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="fc66f-107">E embora o que chamamos de alguns nomes abaixo, obrigado a [todos os contribuintes da Comunidade](https://github.com/PowerShell/PowerShell/graphs/contributors) que possibilitado nesta versão.</span><span class="sxs-lookup"><span data-stu-id="fc66f-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="fc66f-108">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="fc66f-108">.NET Core 2.1</span></span>

<span data-ttu-id="fc66f-109">PowerShell Core 6.1 movido para .NET Core 2.1 após era [lançado em Maio](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), o que resulta numa série de aprimoramentos para o PowerShell, incluindo:</span><span class="sxs-lookup"><span data-stu-id="fc66f-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="fc66f-110">melhorias de desempenho (consulte [abaixo](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="fc66f-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="fc66f-111">Suporte de Alpine Linux (pré-visualização)</span><span class="sxs-lookup"><span data-stu-id="fc66f-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="fc66f-112">[Suporte de ferramenta global de .NET](/dotnet/core/tools/global-tools) - próximos em breve para o PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc66f-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="fc66f-113">Pacote de compatibilidade do Windows para .NET Core</span><span class="sxs-lookup"><span data-stu-id="fc66f-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="fc66f-114">No Windows, a equipe .NET fornecido a [Windows Compatibility Pack para .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), removido de um conjunto de assemblies que adicionar um número de APIs ao .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="fc66f-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="fc66f-115">Adicionámos o Compatibility Pack do Windows para a versão 6.1 do PowerShell Core, para que quaisquer módulos ou scripts que usam essas APIs podem basear nas mesmas estejam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fc66f-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="fc66f-116">O pacote de compatibilidade do Windows permite que o PowerShell Core usar **mais de 1900 cmdlets que vêm com o Windows 10 de Outubro de 2018 Update e Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="fc66f-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="fc66f-117">Melhoramentos de desempenho</span><span class="sxs-lookup"><span data-stu-id="fc66f-117">Performance improvements</span></span>

<span data-ttu-id="fc66f-118">PowerShell Core 6.0 feitas algumas melhorias de desempenho significativas.</span><span class="sxs-lookup"><span data-stu-id="fc66f-118">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="fc66f-119">PowerShell Core 6.1 continua a melhorar a velocidade de determinadas operações.</span><span class="sxs-lookup"><span data-stu-id="fc66f-119">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="fc66f-120">Por exemplo, `Group-Object` acelera 66%:</span><span class="sxs-lookup"><span data-stu-id="fc66f-120">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="fc66f-121">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="fc66f-121">Windows PowerShell 5.1</span></span> | <span data-ttu-id="fc66f-122">O PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="fc66f-122">PowerShell Core 6.0</span></span> | <span data-ttu-id="fc66f-123">O PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="fc66f-123">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="fc66f-124">Tempo (seg)</span><span class="sxs-lookup"><span data-stu-id="fc66f-124">Time (sec)</span></span>   | <span data-ttu-id="fc66f-125">25.178</span><span class="sxs-lookup"><span data-stu-id="fc66f-125">25.178</span></span>                 | <span data-ttu-id="fc66f-126">19.653</span><span class="sxs-lookup"><span data-stu-id="fc66f-126">19.653</span></span>              | <span data-ttu-id="fc66f-127">6.641</span><span class="sxs-lookup"><span data-stu-id="fc66f-127">6.641</span></span>               |
| <span data-ttu-id="fc66f-128">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="fc66f-128">Speed-up (%)</span></span> | <span data-ttu-id="fc66f-129">N/A</span><span class="sxs-lookup"><span data-stu-id="fc66f-129">N/A</span></span>                    | <span data-ttu-id="fc66f-130">% de 21.9</span><span class="sxs-lookup"><span data-stu-id="fc66f-130">21.9%</span></span>               | <span data-ttu-id="fc66f-131">% de 66.2</span><span class="sxs-lookup"><span data-stu-id="fc66f-131">66.2%</span></span>               |

<span data-ttu-id="fc66f-132">Da mesma forma, os cenários de classificação como esta melhoraram por mais de 15%:</span><span class="sxs-lookup"><span data-stu-id="fc66f-132">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="fc66f-133">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="fc66f-133">Windows PowerShell 5.1</span></span> | <span data-ttu-id="fc66f-134">O PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="fc66f-134">PowerShell Core 6.0</span></span> | <span data-ttu-id="fc66f-135">O PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="fc66f-135">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="fc66f-136">Tempo (seg)</span><span class="sxs-lookup"><span data-stu-id="fc66f-136">Time (sec)</span></span>   | <span data-ttu-id="fc66f-137">12.170</span><span class="sxs-lookup"><span data-stu-id="fc66f-137">12.170</span></span>                 | <span data-ttu-id="fc66f-138">8.493</span><span class="sxs-lookup"><span data-stu-id="fc66f-138">8.493</span></span>               | <span data-ttu-id="fc66f-139">7.08</span><span class="sxs-lookup"><span data-stu-id="fc66f-139">7.08</span></span>                |
| <span data-ttu-id="fc66f-140">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="fc66f-140">Speed-up (%)</span></span> | <span data-ttu-id="fc66f-141">N/A</span><span class="sxs-lookup"><span data-stu-id="fc66f-141">N/A</span></span>                    | <span data-ttu-id="fc66f-142">% de 30.2</span><span class="sxs-lookup"><span data-stu-id="fc66f-142">30.2%</span></span>               | <span data-ttu-id="fc66f-143">% de 16.6</span><span class="sxs-lookup"><span data-stu-id="fc66f-143">16.6%</span></span>               |

<span data-ttu-id="fc66f-144">`Import-Csv` tem também foi acelera significativamente após uma regressão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc66f-144">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="fc66f-145">O exemplo seguinte utiliza um teste de CSV com 26,616 linhas e colunas de seis:</span><span class="sxs-lookup"><span data-stu-id="fc66f-145">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="fc66f-146">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="fc66f-146">Windows PowerShell 5.1</span></span> | <span data-ttu-id="fc66f-147">O PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="fc66f-147">PowerShell Core 6.0</span></span> | <span data-ttu-id="fc66f-148">O PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="fc66f-148">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="fc66f-149">Tempo (seg)</span><span class="sxs-lookup"><span data-stu-id="fc66f-149">Time (sec)</span></span>   | <span data-ttu-id="fc66f-150">0.441</span><span class="sxs-lookup"><span data-stu-id="fc66f-150">0.441</span></span>                  | <span data-ttu-id="fc66f-151">1.069</span><span class="sxs-lookup"><span data-stu-id="fc66f-151">1.069</span></span>               | <span data-ttu-id="fc66f-152">0.268</span><span class="sxs-lookup"><span data-stu-id="fc66f-152">0.268</span></span>                  |
| <span data-ttu-id="fc66f-153">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="fc66f-153">Speed-up (%)</span></span> | <span data-ttu-id="fc66f-154">N/A</span><span class="sxs-lookup"><span data-stu-id="fc66f-154">N/A</span></span>                    | <span data-ttu-id="fc66f-155">-142.4%</span><span class="sxs-lookup"><span data-stu-id="fc66f-155">-142.4%</span></span>             | <span data-ttu-id="fc66f-156">74.9% de (39.2% de WPS)</span><span class="sxs-lookup"><span data-stu-id="fc66f-156">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="fc66f-157">Por último, a conversão de JSON em `PSObject` tem sido acelera por mais de 50% desde o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc66f-157">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="fc66f-158">O exemplo seguinte utiliza um ficheiro JSON de teste de ~ 2MB:</span><span class="sxs-lookup"><span data-stu-id="fc66f-158">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="fc66f-159">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="fc66f-159">Windows PowerShell 5.1</span></span> | <span data-ttu-id="fc66f-160">O PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="fc66f-160">PowerShell Core 6.0</span></span> | <span data-ttu-id="fc66f-161">O PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="fc66f-161">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="fc66f-162">Tempo (seg)</span><span class="sxs-lookup"><span data-stu-id="fc66f-162">Time (sec)</span></span>   | <span data-ttu-id="fc66f-163">0.259</span><span class="sxs-lookup"><span data-stu-id="fc66f-163">0.259</span></span>                  | <span data-ttu-id="fc66f-164">0.577</span><span class="sxs-lookup"><span data-stu-id="fc66f-164">0.577</span></span>               | <span data-ttu-id="fc66f-165">0.125</span><span class="sxs-lookup"><span data-stu-id="fc66f-165">0.125</span></span>                  |
| <span data-ttu-id="fc66f-166">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="fc66f-166">Speed-up (%)</span></span> | <span data-ttu-id="fc66f-167">N/A</span><span class="sxs-lookup"><span data-stu-id="fc66f-167">N/A</span></span>                    | <span data-ttu-id="fc66f-168">-122.8%</span><span class="sxs-lookup"><span data-stu-id="fc66f-168">-122.8%</span></span>             | <span data-ttu-id="fc66f-169">78.3% de (51.7% de WPS)</span><span class="sxs-lookup"><span data-stu-id="fc66f-169">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-inbox-modules-on-windows"></a><span data-ttu-id="fc66f-170">Verificar `system32` para módulos de caixa de entrada compatível no Windows</span><span class="sxs-lookup"><span data-stu-id="fc66f-170">Check `system32` for compatible inbox modules on Windows</span></span>

<span data-ttu-id="fc66f-171">Na atualização do Windows 10 1809 e Windows Server 2019, atualizámos um número de módulos do PowerShell de caixa de entrada para marcá-los como compatível com o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="fc66f-171">In the Windows 10 1809 update and Windows Server 2019, we updated a number of inbox PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="fc66f-172">Quando o PowerShell Core 6.1 é iniciado, ele incluirá automaticamente `$windir\System32` como parte do `PSModulePath` variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="fc66f-172">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="fc66f-173">No entanto, ele expõe apenas dos módulos `Get-Module` e `Import-Module` se sua `CompatiblePSEdition` está marcado como compatível com o `Core`.</span><span class="sxs-lookup"><span data-stu-id="fc66f-173">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="fc66f-174">Poderá ver diferentes módulos disponíveis, dependendo de que funções e funcionalidades são instaladas.</span><span class="sxs-lookup"><span data-stu-id="fc66f-174">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="fc66f-175">Pode substituir este comportamento para mostrar todos os módulos com o `-SkipEditionCheck` mudar o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fc66f-175">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="fc66f-176">Também adicionámos um `PSEdition` propriedade para a saída de tabela.</span><span class="sxs-lookup"><span data-stu-id="fc66f-176">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Desk      {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Desk      {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Desk      {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Desk      {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Desk      {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="fc66f-177">Para obter mais informações sobre este comportamento, confira [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/2-Draft-Accepted/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="fc66f-177">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/2-Draft-Accepted/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="fc66f-178">Cmdlets de markdown e composição</span><span class="sxs-lookup"><span data-stu-id="fc66f-178">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="fc66f-179">Markdown é um padrão para criar documentos de texto sem formatação legível com formatação básica que pode ser processado em HTML.</span><span class="sxs-lookup"><span data-stu-id="fc66f-179">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="fc66f-180">Adicionamos alguns cmdlets 6.1 que permitem que converta e compor Markdown de documentos na consola, incluindo:</span><span class="sxs-lookup"><span data-stu-id="fc66f-180">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="fc66f-181">Por exemplo, `Show-Markdown` processa um ficheiro de Markdown no console:</span><span class="sxs-lookup"><span data-stu-id="fc66f-181">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Exemplo de show Markdown](./images/markdown_example.png)

<span data-ttu-id="fc66f-183">Para obter mais informações sobre o funcionamento destes cmdlets, confira [este RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="fc66f-183">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="fc66f-184">Sinalizadores de funcionalidade experimental</span><span class="sxs-lookup"><span data-stu-id="fc66f-184">Experimental feature flags</span></span>

<span data-ttu-id="fc66f-185">Sinalizadores de funcionalidade experimental permitem aos utilizadores ativar as funcionalidades que ainda não foram determinadas.</span><span class="sxs-lookup"><span data-stu-id="fc66f-185">Experimental feature flags enable users to turn on features that haven't been finalized.</span></span>
<span data-ttu-id="fc66f-186">Estas funcionalidades experimentais não são suportadas e podem ter bugs.</span><span class="sxs-lookup"><span data-stu-id="fc66f-186">These experimental features aren't supported and may have bugs.</span></span>

<span data-ttu-id="fc66f-187">Pode saber mais sobre esta funcionalidade no [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="fc66f-187">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="fc66f-188">Melhorias de cmdlet da Web</span><span class="sxs-lookup"><span data-stu-id="fc66f-188">Web cmdlet improvements</span></span>

<span data-ttu-id="fc66f-189">Graças a @markekraus, uma grande quantidade de melhorias foram feitas aos nossos cmdlets web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="fc66f-189">Thanks to @markekraus, a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="fc66f-190">e [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="fc66f-190">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="fc66f-191">[6109 de n. º de PR](https://github.com/PowerShell/PowerShell/pull/6109) -padrão de codificação definida como UTF-8 para `application-json` respostas</span><span class="sxs-lookup"><span data-stu-id="fc66f-191">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="fc66f-192">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` parâmetro para permitir `Content-Type` cabeçalhos que não são compatíveis com padrões</span><span class="sxs-lookup"><span data-stu-id="fc66f-192">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="fc66f-193">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` simplificado de parâmetro para suportar `multipart/form-data` de suporte</span><span class="sxs-lookup"><span data-stu-id="fc66f-193">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="fc66f-194">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) – em conformidade, maiúsculas de minúsculas manipulação das chaves de relação</span><span class="sxs-lookup"><span data-stu-id="fc66f-194">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="fc66f-195">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) -adicionar `-Resume` parâmetro para cmdlets de web</span><span class="sxs-lookup"><span data-stu-id="fc66f-195">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="fc66f-196">Melhorias de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="fc66f-196">Remoting improvements</span></span>

### <a name="powershell-direct-tries-to-use-powershell-core-first"></a><span data-ttu-id="fc66f-197">PowerShell Direct tenta utilizar o PowerShell Core primeiro</span><span class="sxs-lookup"><span data-stu-id="fc66f-197">PowerShell Direct tries to use PowerShell Core first</span></span>

<span data-ttu-id="fc66f-198">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) é uma funcionalidade do PowerShell e o Hyper-V que permite-lhe ligar a uma VM de Hyper-V sem conectividade de rede ou outros serviços de gestão remota.</span><span class="sxs-lookup"><span data-stu-id="fc66f-198">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM without network connectivity or other remote management services.</span></span>

<span data-ttu-id="fc66f-199">No passado, o PowerShell Direct ligados utilizando a instância do Windows PowerShell de caixa de entrada na VM.</span><span class="sxs-lookup"><span data-stu-id="fc66f-199">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the VM.</span></span>
<span data-ttu-id="fc66f-200">Agora, PowerShell Direct primeiro tenta se conectar usando qualquer disponíveis `pwsh.exe` sobre o `PATH` variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="fc66f-200">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="fc66f-201">Se `pwsh.exe` não estiver disponível, PowerShell Direct retrocede para utilizar `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="fc66f-201">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="fc66f-202">`Enable-PSRemoting` agora cria pontos de extremidade de comunicação remota separado para versões de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="fc66f-202">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="fc66f-203">`Enable-PSRemoting` Agora, cria duas configurações de sessão de comunicação remota:</span><span class="sxs-lookup"><span data-stu-id="fc66f-203">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="fc66f-204">Uma para a versão principal do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc66f-204">One for the major version of PowerShell.</span></span> <span data-ttu-id="fc66f-205">Por exemplo,`PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="fc66f-205">For example,`PowerShell.6`.</span></span> <span data-ttu-id="fc66f-206">Este ponto de extremidade que pode ser utilizado em atualizações de versão secundária como a configuração de sessão do PowerShell 6 "todo o sistema"</span><span class="sxs-lookup"><span data-stu-id="fc66f-206">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="fc66f-207">Uma configuração de sessão específicas da versão, por exemplo: `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="fc66f-207">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="fc66f-208">Este comportamento é útil se pretender ter várias versões do PowerShell 6 instaladas e acessíveis na mesma máquina.</span><span class="sxs-lookup"><span data-stu-id="fc66f-208">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="fc66f-209">Além disso, as versões de pré-visualização do PowerShell agora obtém seus próprios comunicação remota de configurações de sessão após a execução do `Enable-PSRemoting` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="fc66f-209">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="fc66f-210">A saída pode ser diferente se não tiver configurado o WinRM antes.</span><span class="sxs-lookup"><span data-stu-id="fc66f-210">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="fc66f-211">Em seguida, pode ver as configurações de sessão do PowerShell separadas para a pré-visualização e estável baseia-se do PowerShell 6 e para cada versão específica.</span><span class="sxs-lookup"><span data-stu-id="fc66f-211">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="fc66f-212">`user@host:port` sintaxe suportada para SSH</span><span class="sxs-lookup"><span data-stu-id="fc66f-212">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="fc66f-213">SSH clientes normalmente suportam uma cadeia de ligação no formato `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="fc66f-213">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="fc66f-214">Com a adição do SSH como um protocolo de comunicação remota do PowerShell, adicionámos suporte para esse formato de cadeia de ligação:</span><span class="sxs-lookup"><span data-stu-id="fc66f-214">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="fc66f-215">Opção de MSI para adicionar o menu de contexto de shell do explorer no Windows</span><span class="sxs-lookup"><span data-stu-id="fc66f-215">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="fc66f-216">Graças a @bergmeister, agora pode ativar um menu de contexto no Windows.</span><span class="sxs-lookup"><span data-stu-id="fc66f-216">Thanks to @bergmeister, now you can enable a context menu on Windows.</span></span> <span data-ttu-id="fc66f-217">Agora pode abrir a instalação de todo o sistema do PowerShell 6.1 de qualquer pasta no Explorador do Windows:</span><span class="sxs-lookup"><span data-stu-id="fc66f-217">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Menu de contexto do shell do PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="fc66f-219">Coisas boas</span><span class="sxs-lookup"><span data-stu-id="fc66f-219">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="fc66f-220">"Executar como administrador" da lista de atalhos de atalho do Windows</span><span class="sxs-lookup"><span data-stu-id="fc66f-220">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="fc66f-221">Graças a @bergmeister, lista de atalhos no atalho PowerShell Core inclui agora "Executar como administrador":</span><span class="sxs-lookup"><span data-stu-id="fc66f-221">Thanks to @bergmeister, the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![Executar como administrador na lista de atalhos do PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="fc66f-223">`cd -` Devolve a diretório anterior</span><span class="sxs-lookup"><span data-stu-id="fc66f-223">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="fc66f-224">Ou no Linux:</span><span class="sxs-lookup"><span data-stu-id="fc66f-224">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="fc66f-225">Além disso, `cd --` é alterado para `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="fc66f-225">Also, `cd --` changes to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="fc66f-226">Graças à @iSazonov, o [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) cmdlet tem sido transportado para o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="fc66f-226">Thanks to @iSazonov, the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="fc66f-227">`Update-Help` como não-administrador</span><span class="sxs-lookup"><span data-stu-id="fc66f-227">`Update-Help` as non-admin</span></span>

<span data-ttu-id="fc66f-228">Por demanda popular, `Update-Help` já não precisa ser executado como administrador.</span><span class="sxs-lookup"><span data-stu-id="fc66f-228">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
<span data-ttu-id="fc66f-229">`Update-Help` agora usa como padrão salvar ajuda para uma pasta no âmbito do utilizador.</span><span class="sxs-lookup"><span data-stu-id="fc66f-229">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="fc66f-230">Novos métodos/as propriedades no `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="fc66f-230">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="fc66f-231">Graças à @iSazonov, adicionamos novos métodos e propriedades para `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="fc66f-231">Thanks to @iSazonov, we've added new methods and properties to `PSCustomObject`.</span></span>
<span data-ttu-id="fc66f-232">`PSCustomObject` inclui agora uma `Count` / `Length` propriedade que indica o número de itens.</span><span class="sxs-lookup"><span data-stu-id="fc66f-232">`PSCustomObject` now includes a `Count`/`Length` property that gives the number of items.</span></span>

<span data-ttu-id="fc66f-233">Ambos estes exemplos retornam `2` como o número de `PSCustomObjects` na coleção.</span><span class="sxs-lookup"><span data-stu-id="fc66f-233">Both of these examples return `2` as the number of `PSCustomObjects` in the collection.</span></span>

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Length
```

```powershell
@(
[pscustomobject]@{foo = '1'},
[pscustomobject]@{bar = '2' }).Count
```

<span data-ttu-id="fc66f-234">Este trabalho também inclui `ForEach` e `Where` métodos que permitem operar e filtrar `PSCustomObject` itens:</span><span class="sxs-lookup"><span data-stu-id="fc66f-234">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).ForEach({$_.foo+1})
```

```Output
2
3
```

```powershell
@(
>> [pscustomobject]@{foo = 1},
>> [pscustomobject]@{foo = 2 }).Where({$_.foo -gt 1})
```

```Output
foo
---
  2
```

### `Where-Object -Not`

<span data-ttu-id="fc66f-235">Graças à @SimonWahlin, adicionamos o `-Not` parâmetro para `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="fc66f-235">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="fc66f-236">Agora pode filtrar um objeto no pipeline, a não existência de uma propriedade ou um valor de propriedade de nulo/vazio.</span><span class="sxs-lookup"><span data-stu-id="fc66f-236">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="fc66f-237">Por exemplo, este comando devolve todos os serviços que não têm quaisquer serviços dependentes definidos:</span><span class="sxs-lookup"><span data-stu-id="fc66f-237">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="fc66f-238">`New-ModuleManifest` cria um documento sem BOM UTF-8</span><span class="sxs-lookup"><span data-stu-id="fc66f-238">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="fc66f-239">Considerando nossa mudança para BOM sem UTF-8 no PowerShell 6.0, atualizámos o `New-ModuleManifest` cmdlet para criar um documento sem BOM UTF-8, em vez de um UTF-16 um.</span><span class="sxs-lookup"><span data-stu-id="fc66f-239">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="fc66f-240">Conversões de PSMethod ao delegado</span><span class="sxs-lookup"><span data-stu-id="fc66f-240">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="fc66f-241">Graças à @powercode, suportamos agora a conversão de um `PSMethod` num delegado.</span><span class="sxs-lookup"><span data-stu-id="fc66f-241">Thanks to @powercode, we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="fc66f-242">Isso permite que faça coisas como passagem `PSMethod` `[M]::DoubleStrLen` como um valor de delegado em `[M]::AggregateString`:</span><span class="sxs-lookup"><span data-stu-id="fc66f-242">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="fc66f-243">Para obter mais informações sobre esta alteração, confira [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="fc66f-243">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="fc66f-244">Desvio padrão no `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="fc66f-244">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="fc66f-245">Graças à @CloudyDino, adicionamos uma `StandardDeviation` propriedade `Measure-Object`:</span><span class="sxs-lookup"><span data-stu-id="fc66f-245">Thanks to @CloudyDino, we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="fc66f-246">Graças à @maybe-hello-world, `Get-PfxCertificate` tem agora o `Password` parâmetro, que assume um `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="fc66f-246">Thanks to @maybe-hello-world, `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="fc66f-247">Isto permite-lhe utilizá-lo de forma não interativa:</span><span class="sxs-lookup"><span data-stu-id="fc66f-247">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="fc66f-248">Remoção do `more` função</span><span class="sxs-lookup"><span data-stu-id="fc66f-248">Removal of the `more` function</span></span>

<span data-ttu-id="fc66f-249">No passado, PowerShell foi lançado uma função no Windows chamado `more` que encapsulada `more.com`.</span><span class="sxs-lookup"><span data-stu-id="fc66f-249">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="fc66f-250">Essa função agora foi removida.</span><span class="sxs-lookup"><span data-stu-id="fc66f-250">That function has now been removed.</span></span>

<span data-ttu-id="fc66f-251">Também o `help` função alterado para utilizar `more.com` no Windows ou pager de padrão do sistema especificado pelo `$env:PAGER` em plataformas não Windows.</span><span class="sxs-lookup"><span data-stu-id="fc66f-251">Also the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="fc66f-252">`cd DriveName:` Devolve agora os utilizadores para o diretório de trabalho atual nessa unidade</span><span class="sxs-lookup"><span data-stu-id="fc66f-252">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="fc66f-253">Anteriormente, utilizando `Set-Location` ou `cd` para regressar a uma PSDrive enviada aos utilizadores para a localização predefinida para essa unidade.</span><span class="sxs-lookup"><span data-stu-id="fc66f-253">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="fc66f-254">Graças a @mcbobke, os usuários agora são enviados para o último conhecido atual diretório de trabalho da sessão.</span><span class="sxs-lookup"><span data-stu-id="fc66f-254">Thanks to @mcbobke, users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="fc66f-255">Aceleradores de tipo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc66f-255">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="fc66f-256">No Windows PowerShell, incluímos os Aceleradores de tipo seguintes para que seja mais fácil trabalhar com seus respectivos tipos:</span><span class="sxs-lookup"><span data-stu-id="fc66f-256">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="fc66f-257">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="fc66f-257">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="fc66f-258">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="fc66f-258">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="fc66f-259">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="fc66f-259">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="fc66f-260">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="fc66f-260">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="fc66f-261">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="fc66f-261">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="fc66f-262">Estes aceleradores de tipo não foram incluídos no PowerShell 6, mas foram adicionados ao 6.1 do PowerShell em execução no Windows.</span><span class="sxs-lookup"><span data-stu-id="fc66f-262">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="fc66f-263">Esses tipos são úteis para construir facilmente AD e objetos WMI.</span><span class="sxs-lookup"><span data-stu-id="fc66f-263">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="fc66f-264">Por exemplo, pode consultar ao utilizar o LDAP:</span><span class="sxs-lookup"><span data-stu-id="fc66f-264">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="fc66f-265">Ambos estes exemplos criam um objeto de Win32_OperatingSystem CIM:</span><span class="sxs-lookup"><span data-stu-id="fc66f-265">Both of these examples create a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"win32_operatingsystem=@"
[wmiclass]"win32_operatingsystem"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="fc66f-266">`-lp` alias de todos os `-LiteralPath` parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc66f-266">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="fc66f-267">Graças à @kvprasoon, agora temos um alias de parâmetro `-lp` todos os os incorporada cmdlets do PowerShell que tenham um `-LiteralPath` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fc66f-267">Thanks to @kvprasoon, we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="fc66f-268">Alterações recentes</span><span class="sxs-lookup"><span data-stu-id="fc66f-268">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="fc66f-269">Caminhos de instalação baseada em MSI no Windows</span><span class="sxs-lookup"><span data-stu-id="fc66f-269">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="fc66f-270">No Windows, o pacote MSI instala agora para o seguinte caminho:</span><span class="sxs-lookup"><span data-stu-id="fc66f-270">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="fc66f-271">`$env:ProgramFiles\PowerShell\6\` para a instalação estável do 6.x</span><span class="sxs-lookup"><span data-stu-id="fc66f-271">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="fc66f-272">`$env:ProgramFiles\PowerShell\6-preview\` para a instalação de pré-visualização do 6.x</span><span class="sxs-lookup"><span data-stu-id="fc66f-272">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="fc66f-273">Esta alteração garante que o PowerShell Core pode ser atualizado/atendido pelo Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="fc66f-273">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="fc66f-274">Para obter mais informações, confira [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="fc66f-274">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="fc66f-275">Telemetria só pode ser desativada com uma variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="fc66f-275">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="fc66f-276">O PowerShell Core envia dados de telemetria básico para a Microsoft quando é iniciado.</span><span class="sxs-lookup"><span data-stu-id="fc66f-276">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="fc66f-277">Os dados incluem o nome do SO, versão do SO e versão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc66f-277">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="fc66f-278">Estes dados permite-nos compreender melhor os ambientes nos quais o PowerShell é utilizado e permite-nos atribuir prioridades a novas funcionalidades e correções.</span><span class="sxs-lookup"><span data-stu-id="fc66f-278">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="fc66f-279">Para sair desta telemetria, defina a variável de ambiente `POWERSHELL_TELEMETRY_OPTOUT` para `true`, `yes`, ou `1`.</span><span class="sxs-lookup"><span data-stu-id="fc66f-279">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="fc66f-280">Já não suportamos a eliminação do ficheiro `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` para desativar a telemetria.</span><span class="sxs-lookup"><span data-stu-id="fc66f-280">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="fc66f-281">Não são permitidas autenticação básica através de HTTP na comunicação remota do PowerShell em plataformas de Unix</span><span class="sxs-lookup"><span data-stu-id="fc66f-281">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="fc66f-282">Para impedir a utilização de tráfego não criptografado, a comunicação remota do PowerShell em plataformas Unix agora requer a utilização de NTLM/negociar ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="fc66f-282">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="fc66f-283">Para obter mais informações sobre estas alterações, confira [PR #6799](https://github.com/PowerShell/PowerShell/pull/6799).</span><span class="sxs-lookup"><span data-stu-id="fc66f-283">For more information on these changes, check out [PR #6799](https://github.com/PowerShell/PowerShell/pull/6799).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="fc66f-284">Removido `VisualBasic` como um idioma suportado no Add-Type</span><span class="sxs-lookup"><span data-stu-id="fc66f-284">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="fc66f-285">No passado, poderia compilar código do Visual Basic utilizando o `Add-Type` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fc66f-285">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="fc66f-286">Visual Basic foi raramente utilizado com `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="fc66f-286">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="fc66f-287">Removemos esta funcionalidade para reduzir o tamanho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fc66f-287">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="fc66f-288">Limpos usos de `CommandTypes.Workflow` e `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="fc66f-288">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="fc66f-289">Para obter mais informações sobre estas alterações, confira [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="fc66f-289">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>