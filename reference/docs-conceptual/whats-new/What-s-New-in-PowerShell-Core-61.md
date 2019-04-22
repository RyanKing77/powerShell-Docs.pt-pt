---
title: Quais são as novidades no PowerShell Core 6.1
description: Novos recursos e alterações lançadas no PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: fe1e892d4a13a7758f5405867fdd7488c059f5cc
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59293321"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="e7ca6-103">Quais são as novidades no PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="e7ca6-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="e7ca6-104">Segue-se uma seleção de alguns dos principais novos recursos e alterações que foram introduzidas no PowerShell Core 6.1.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="e7ca6-105">Também há **toneladas** de "aborrecida" que tornam o PowerShell mais rápido e mais estável (além de muitas e várias correções de erros)!</span><span class="sxs-lookup"><span data-stu-id="e7ca6-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="e7ca6-106">Para obter uma lista completa das alterações, confira nossos [registo de alterações no GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="e7ca6-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="e7ca6-107">E embora o que chamamos de alguns nomes abaixo, obrigado a [todos os contribuintes da Comunidade](https://github.com/PowerShell/PowerShell/graphs/contributors) que possibilitado nesta versão.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="e7ca6-108">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="e7ca6-108">.NET Core 2.1</span></span>

<span data-ttu-id="e7ca6-109">PowerShell Core 6.1 movido para .NET Core 2.1 após era [lançado em Maio](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), o que resulta numa série de aprimoramentos para o PowerShell, incluindo:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="e7ca6-110">melhorias de desempenho (consulte [abaixo](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="e7ca6-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="e7ca6-111">Suporte de Alpine Linux (pré-visualização)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="e7ca6-112">[Suporte de ferramenta global de .NET](/dotnet/core/tools/global-tools) - próximos em breve para o PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7ca6-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="e7ca6-113">Pacote de compatibilidade do Windows para .NET Core</span><span class="sxs-lookup"><span data-stu-id="e7ca6-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="e7ca6-114">No Windows, a equipe .NET fornecido a [Windows Compatibility Pack para .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), removido de um conjunto de assemblies que adicionar um número de APIs ao .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="e7ca6-115">Adicionámos o Compatibility Pack do Windows para a versão 6.1 do PowerShell Core, para que quaisquer módulos ou scripts que usam essas APIs podem basear nas mesmas estejam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="e7ca6-116">O pacote de compatibilidade do Windows permite que o PowerShell Core usar **mais de 1900 cmdlets que vêm com o Windows 10 de Outubro de 2018 Update e Windows Server 2019**.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="e7ca6-117">Suporte para permissões de aplicação</span><span class="sxs-lookup"><span data-stu-id="e7ca6-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="e7ca6-118">6.1 do PowerShell Core tem paridade com suporte do Windows PowerShell 5.1 [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) e [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) permissões de aplicação.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span>
<span data-ttu-id="e7ca6-119">Permissões de aplicação permite que um controle granular do que binários têm permissão para ser executado utilizado com o PowerShell [modo de idioma restrita](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span><span class="sxs-lookup"><span data-stu-id="e7ca6-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="e7ca6-120">Melhoramentos de desempenho</span><span class="sxs-lookup"><span data-stu-id="e7ca6-120">Performance improvements</span></span>

<span data-ttu-id="e7ca6-121">PowerShell Core 6.0 feitas algumas melhorias de desempenho significativas.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-121">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="e7ca6-122">PowerShell Core 6.1 continua a melhorar a velocidade de determinadas operações.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="e7ca6-123">Por exemplo, `Group-Object` acelera 66%:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="e7ca6-124">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e7ca6-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="e7ca6-125">O PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="e7ca6-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="e7ca6-126">O PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="e7ca6-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="e7ca6-127">Tempo (seg)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-127">Time (sec)</span></span>   | <span data-ttu-id="e7ca6-128">25.178</span><span class="sxs-lookup"><span data-stu-id="e7ca6-128">25.178</span></span>                 | <span data-ttu-id="e7ca6-129">19.653</span><span class="sxs-lookup"><span data-stu-id="e7ca6-129">19.653</span></span>              | <span data-ttu-id="e7ca6-130">6.641</span><span class="sxs-lookup"><span data-stu-id="e7ca6-130">6.641</span></span>               |
| <span data-ttu-id="e7ca6-131">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-131">Speed-up (%)</span></span> | <span data-ttu-id="e7ca6-132">N/A</span><span class="sxs-lookup"><span data-stu-id="e7ca6-132">N/A</span></span>                    | <span data-ttu-id="e7ca6-133">21.9%</span><span class="sxs-lookup"><span data-stu-id="e7ca6-133">21.9%</span></span>               | <span data-ttu-id="e7ca6-134">66.2%</span><span class="sxs-lookup"><span data-stu-id="e7ca6-134">66.2%</span></span>               |

<span data-ttu-id="e7ca6-135">Da mesma forma, os cenários de classificação como esta melhoraram por mais de 15%:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="e7ca6-136">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e7ca6-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="e7ca6-137">O PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="e7ca6-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="e7ca6-138">O PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="e7ca6-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="e7ca6-139">Tempo (seg)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-139">Time (sec)</span></span>   | <span data-ttu-id="e7ca6-140">12.170</span><span class="sxs-lookup"><span data-stu-id="e7ca6-140">12.170</span></span>                 | <span data-ttu-id="e7ca6-141">8.493</span><span class="sxs-lookup"><span data-stu-id="e7ca6-141">8.493</span></span>               | <span data-ttu-id="e7ca6-142">7.08</span><span class="sxs-lookup"><span data-stu-id="e7ca6-142">7.08</span></span>                |
| <span data-ttu-id="e7ca6-143">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-143">Speed-up (%)</span></span> | <span data-ttu-id="e7ca6-144">N/A</span><span class="sxs-lookup"><span data-stu-id="e7ca6-144">N/A</span></span>                    | <span data-ttu-id="e7ca6-145">30.2%</span><span class="sxs-lookup"><span data-stu-id="e7ca6-145">30.2%</span></span>               | <span data-ttu-id="e7ca6-146">16.6%</span><span class="sxs-lookup"><span data-stu-id="e7ca6-146">16.6%</span></span>               |

<span data-ttu-id="e7ca6-147">`Import-Csv` tem também foi acelera significativamente após uma regressão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-147">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="e7ca6-148">O exemplo seguinte utiliza um teste de CSV com 26,616 linhas e colunas de seis:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="e7ca6-149">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e7ca6-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="e7ca6-150">O PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="e7ca6-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="e7ca6-151">O PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="e7ca6-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="e7ca6-152">Tempo (seg)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-152">Time (sec)</span></span>   | <span data-ttu-id="e7ca6-153">0.441</span><span class="sxs-lookup"><span data-stu-id="e7ca6-153">0.441</span></span>                  | <span data-ttu-id="e7ca6-154">1.069</span><span class="sxs-lookup"><span data-stu-id="e7ca6-154">1.069</span></span>               | <span data-ttu-id="e7ca6-155">0.268</span><span class="sxs-lookup"><span data-stu-id="e7ca6-155">0.268</span></span>                  |
| <span data-ttu-id="e7ca6-156">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-156">Speed-up (%)</span></span> | <span data-ttu-id="e7ca6-157">N/A</span><span class="sxs-lookup"><span data-stu-id="e7ca6-157">N/A</span></span>                    | <span data-ttu-id="e7ca6-158">-142.4%</span><span class="sxs-lookup"><span data-stu-id="e7ca6-158">-142.4%</span></span>             | <span data-ttu-id="e7ca6-159">74.9% de (39.2% de WPS)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="e7ca6-160">Por último, a conversão de JSON em `PSObject` tem sido acelera por mais de 50% desde o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="e7ca6-161">O exemplo seguinte utiliza um ficheiro JSON de teste de ~ 2MB:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="e7ca6-162">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e7ca6-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="e7ca6-163">O PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="e7ca6-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="e7ca6-164">O PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="e7ca6-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="e7ca6-165">Tempo (seg)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-165">Time (sec)</span></span>   | <span data-ttu-id="e7ca6-166">0.259</span><span class="sxs-lookup"><span data-stu-id="e7ca6-166">0.259</span></span>                  | <span data-ttu-id="e7ca6-167">0.577</span><span class="sxs-lookup"><span data-stu-id="e7ca6-167">0.577</span></span>               | <span data-ttu-id="e7ca6-168">0.125</span><span class="sxs-lookup"><span data-stu-id="e7ca6-168">0.125</span></span>                  |
| <span data-ttu-id="e7ca6-169">Aceleração (%)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-169">Speed-up (%)</span></span> | <span data-ttu-id="e7ca6-170">N/A</span><span class="sxs-lookup"><span data-stu-id="e7ca6-170">N/A</span></span>                    | <span data-ttu-id="e7ca6-171">-122.8%</span><span class="sxs-lookup"><span data-stu-id="e7ca6-171">-122.8%</span></span>             | <span data-ttu-id="e7ca6-172">78.3% de (51.7% de WPS)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a><span data-ttu-id="e7ca6-173">Verificar `system32` para compatíveis módulos de incluído no Windows</span><span class="sxs-lookup"><span data-stu-id="e7ca6-173">Check `system32` for compatible in-box modules on Windows</span></span>

<span data-ttu-id="e7ca6-174">Na atualização do Windows 10 1809 e Windows Server 2019, atualizámos um número de módulos do PowerShell incluído para marcá-los como compatível com o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of in-box PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="e7ca6-175">Quando o PowerShell Core 6.1 é iniciado, ele incluirá automaticamente `$windir\System32` como parte do `PSModulePath` variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="e7ca6-176">No entanto, ele expõe apenas dos módulos `Get-Module` e `Import-Module` se sua `CompatiblePSEdition` está marcado como compatível com o `Core`.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="e7ca6-177">Poderá ver diferentes módulos disponíveis, dependendo de que funções e funcionalidades são instaladas.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-177">You may see different available modules depending on what roles and features are installed.</span></span>

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

<span data-ttu-id="e7ca6-178">Pode substituir este comportamento para mostrar todos os módulos com o `-SkipEditionCheck` mudar o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="e7ca6-179">Também adicionámos um `PSEdition` propriedade para a saída de tabela.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="e7ca6-180">Para obter mais informações sobre este comportamento, confira [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="e7ca6-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="e7ca6-181">Cmdlets de markdown e composição</span><span class="sxs-lookup"><span data-stu-id="e7ca6-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="e7ca6-182">Markdown é um padrão para criar documentos de texto sem formatação legível com formatação básica que pode ser processado em HTML.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="e7ca6-183">Adicionamos alguns cmdlets 6.1 que permitem que converta e compor Markdown de documentos na consola, incluindo:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="e7ca6-184">Por exemplo, `Show-Markdown` processa um ficheiro de Markdown no console:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Exemplo de show Markdown](./images/markdown_example.png)

<span data-ttu-id="e7ca6-186">Para obter mais informações sobre o funcionamento destes cmdlets, confira [este RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="e7ca6-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="e7ca6-187">Sinalizadores de funcionalidade experimental</span><span class="sxs-lookup"><span data-stu-id="e7ca6-187">Experimental feature flags</span></span>

<span data-ttu-id="e7ca6-188">Sinalizadores de funcionalidade experimental permitem aos utilizadores ativar as funcionalidades que ainda não foram determinadas.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-188">Experimental feature flags enable users to turn on features that haven't been finalized.</span></span>
<span data-ttu-id="e7ca6-189">Estas funcionalidades experimentais não são suportadas e podem ter bugs.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-189">These experimental features aren't supported and may have bugs.</span></span>

<span data-ttu-id="e7ca6-190">Pode saber mais sobre esta funcionalidade no [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="e7ca6-190">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="e7ca6-191">Melhorias de cmdlet da Web</span><span class="sxs-lookup"><span data-stu-id="e7ca6-191">Web cmdlet improvements</span></span>

<span data-ttu-id="e7ca6-192">Graças à [ @markekraus ](https://github.com/markekraus), uma grande quantidade de melhorias foram feitas aos nossos cmdlets web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="e7ca6-192">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="e7ca6-193">e [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span><span class="sxs-lookup"><span data-stu-id="e7ca6-193">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="e7ca6-194">[6109 de n. º de PR](https://github.com/PowerShell/PowerShell/pull/6109) -padrão de codificação definida como UTF-8 para `application-json` respostas</span><span class="sxs-lookup"><span data-stu-id="e7ca6-194">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="e7ca6-195">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` parâmetro para permitir `Content-Type` cabeçalhos que não são compatíveis com padrões</span><span class="sxs-lookup"><span data-stu-id="e7ca6-195">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="e7ca6-196">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` simplificado de parâmetro para suportar `multipart/form-data` de suporte</span><span class="sxs-lookup"><span data-stu-id="e7ca6-196">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="e7ca6-197">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) – em conformidade, maiúsculas de minúsculas manipulação das chaves de relação</span><span class="sxs-lookup"><span data-stu-id="e7ca6-197">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="e7ca6-198">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) -adicionar `-Resume` parâmetro para cmdlets de web</span><span class="sxs-lookup"><span data-stu-id="e7ca6-198">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="e7ca6-199">Melhorias de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="e7ca6-199">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="e7ca6-200">PowerShell Direct para contentores tenta utilizar o PowerShell Core primeiro</span><span class="sxs-lookup"><span data-stu-id="e7ca6-200">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="e7ca6-201">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) é uma funcionalidade do PowerShell e o Hyper-V que permite-lhe ligar a uma VM de Hyper-V ou o contentor sem conectividade de rede ou outros serviços de gestão remota.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-201">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="e7ca6-202">No passado, o PowerShell Direct ligados utilizando a instância do Windows PowerShell de caixa de entrada no contentor.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-202">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the Container.</span></span>
<span data-ttu-id="e7ca6-203">Agora, PowerShell Direct primeiro tenta se conectar usando qualquer disponíveis `pwsh.exe` sobre o `PATH` variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-203">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="e7ca6-204">Se `pwsh.exe` não estiver disponível, PowerShell Direct retrocede para utilizar `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-204">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="e7ca6-205">`Enable-PSRemoting` agora cria pontos de extremidade de comunicação remota separado para versões de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="e7ca6-205">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="e7ca6-206">`Enable-PSRemoting` Agora, cria duas configurações de sessão de comunicação remota:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-206">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="e7ca6-207">Uma para a versão principal do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-207">One for the major version of PowerShell.</span></span> <span data-ttu-id="e7ca6-208">Por exemplo, `PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-208">For example, `PowerShell.6`.</span></span> <span data-ttu-id="e7ca6-209">Este ponto de extremidade que pode ser utilizado em atualizações de versão secundária como a configuração de sessão do PowerShell 6 "todo o sistema"</span><span class="sxs-lookup"><span data-stu-id="e7ca6-209">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="e7ca6-210">Uma configuração de sessão específicas da versão, por exemplo: `PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="e7ca6-210">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="e7ca6-211">Este comportamento é útil se pretender ter várias versões do PowerShell 6 instaladas e acessíveis na mesma máquina.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-211">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="e7ca6-212">Além disso, as versões de pré-visualização do PowerShell agora obtém seus próprios comunicação remota de configurações de sessão após a execução do `Enable-PSRemoting` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-212">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="e7ca6-213">A saída pode ser diferente se não tiver configurado o WinRM antes.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-213">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="e7ca6-214">Em seguida, pode ver as configurações de sessão do PowerShell separadas para a pré-visualização e estável baseia-se do PowerShell 6 e para cada versão específica.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-214">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

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

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="e7ca6-215">`user@host:port` sintaxe suportada para SSH</span><span class="sxs-lookup"><span data-stu-id="e7ca6-215">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="e7ca6-216">SSH clientes normalmente suportam uma cadeia de ligação no formato `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-216">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="e7ca6-217">Com a adição do SSH como um protocolo de comunicação remota do PowerShell, adicionámos suporte para esse formato de cadeia de ligação:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-217">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="e7ca6-218">Opção de MSI para adicionar o menu de contexto de shell do explorer no Windows</span><span class="sxs-lookup"><span data-stu-id="e7ca6-218">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="e7ca6-219">Graças à [ @bergmeister ](https://github.com/bergmeister), agora pode ativar um menu de contexto no Windows.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-219">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="e7ca6-220">Agora pode abrir a instalação de todo o sistema do PowerShell 6.1 de qualquer pasta no Explorador do Windows:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-220">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Menu de contexto do shell do PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="e7ca6-222">Coisas boas</span><span class="sxs-lookup"><span data-stu-id="e7ca6-222">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="e7ca6-223">"Executar como administrador" da lista de atalhos de atalho do Windows</span><span class="sxs-lookup"><span data-stu-id="e7ca6-223">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="e7ca6-224">Graças à [ @bergmeister ](https://github.com/bergmeister), lista de atalhos no atalho PowerShell Core inclui agora "Executar como administrador":</span><span class="sxs-lookup"><span data-stu-id="e7ca6-224">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![Executar como administrador na lista de atalhos do PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="e7ca6-226">`cd -` Devolve a diretório anterior</span><span class="sxs-lookup"><span data-stu-id="e7ca6-226">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="e7ca6-227">Ou no Linux:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-227">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="e7ca6-228">Além disso, `cd` e `cd --` alterar para `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-228">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="e7ca6-229">Graças à [ @iSazonov ](https://github.com/iSazonov), o [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) cmdlet tem sido transportado para o PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-229">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="e7ca6-230">`Update-Help` como não-administrador</span><span class="sxs-lookup"><span data-stu-id="e7ca6-230">`Update-Help` as non-admin</span></span>

<span data-ttu-id="e7ca6-231">Por demanda popular, `Update-Help` já não precisa ser executado como administrador.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-231">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
<span data-ttu-id="e7ca6-232">`Update-Help` agora usa como padrão salvar ajuda para uma pasta no âmbito do utilizador.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-232">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="e7ca6-233">Novos métodos/as propriedades no `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="e7ca6-233">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="e7ca6-234">Graças à [ @iSazonov ](https://github.com/iSazonov), adicionamos novos métodos e propriedades para `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-234">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span>
<span data-ttu-id="e7ca6-235">`PSCustomObject` inclui agora uma `Count` / `Length` propriedade como outros objetos.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-235">`PSCustomObject` now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="e7ca6-236">Este trabalho também inclui `ForEach` e `Where` métodos que permitem operar e filtrar `PSCustomObject` itens:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-236">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="e7ca6-237">Graças à @SimonWahlin, adicionamos o `-Not` parâmetro para `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-237">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="e7ca6-238">Agora pode filtrar um objeto no pipeline, a não existência de uma propriedade ou um valor de propriedade de nulo/vazio.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-238">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="e7ca6-239">Por exemplo, este comando devolve todos os serviços que não têm quaisquer serviços dependentes definidos:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-239">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="e7ca6-240">`New-ModuleManifest` cria um documento sem BOM UTF-8</span><span class="sxs-lookup"><span data-stu-id="e7ca6-240">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="e7ca6-241">Considerando nossa mudança para BOM sem UTF-8 no PowerShell 6.0, atualizámos o `New-ModuleManifest` cmdlet para criar um documento sem BOM UTF-8, em vez de um UTF-16 um.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-241">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="e7ca6-242">Conversões de PSMethod ao delegado</span><span class="sxs-lookup"><span data-stu-id="e7ca6-242">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="e7ca6-243">Graças à [ @powercode ](https://github.com/powercode), agora, suportamos a conversão de um `PSMethod` num delegado.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-243">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="e7ca6-244">Isso permite que faça coisas como passagem `PSMethod` `[M]::DoubleStrLen` como um valor de delegado em `[M]::AggregateString`:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-244">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

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

<span data-ttu-id="e7ca6-245">Para obter mais informações sobre esta alteração, confira [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="e7ca6-245">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="e7ca6-246">Desvio padrão no `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="e7ca6-246">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="e7ca6-247">Graças à [ @CloudyDino ](https://github.com/CloudyDino), adicionamos uma `StandardDeviation` propriedade `Measure-Object`:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-247">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

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

<span data-ttu-id="e7ca6-248">Graças à [ @maybe-hello-world ](https://github.com/maybe-hello-world), `Get-PfxCertificate` tem agora o `Password` parâmetro, que assume um `SecureString`.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-248">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="e7ca6-249">Isto permite-lhe utilizá-lo de forma não interativa:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-249">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="e7ca6-250">Remoção do `more` função</span><span class="sxs-lookup"><span data-stu-id="e7ca6-250">Removal of the `more` function</span></span>

<span data-ttu-id="e7ca6-251">No passado, PowerShell foi lançado uma função no Windows chamado `more` que encapsulada `more.com`.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-251">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="e7ca6-252">Essa função agora foi removida.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-252">That function has now been removed.</span></span>

<span data-ttu-id="e7ca6-253">Além disso, o `help` função alterado para utilizar `more.com` no Windows ou pager de padrão do sistema especificado pelo `$env:PAGER` em plataformas não Windows.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-253">Also, the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="e7ca6-254">`cd DriveName:` Devolve agora os utilizadores para o diretório de trabalho atual nessa unidade</span><span class="sxs-lookup"><span data-stu-id="e7ca6-254">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="e7ca6-255">Anteriormente, utilizando `Set-Location` ou `cd` para regressar a uma PSDrive enviada aos utilizadores para a localização predefinida para essa unidade.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-255">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="e7ca6-256">Graças à [ @mcbobke ](https://github.com/mcbobke), os usuários agora são enviados para o último conhecido atual diretório de trabalho da sessão.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-256">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="e7ca6-257">Aceleradores de tipo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7ca6-257">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="e7ca6-258">No Windows PowerShell, incluímos os Aceleradores de tipo seguintes para que seja mais fácil trabalhar com seus respectivos tipos:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-258">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="e7ca6-259">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="e7ca6-259">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="e7ca6-260">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="e7ca6-260">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="e7ca6-261">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="e7ca6-261">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="e7ca6-262">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="e7ca6-262">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="e7ca6-263">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="e7ca6-263">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="e7ca6-264">Estes aceleradores de tipo não foram incluídos no PowerShell 6, mas foram adicionados ao 6.1 do PowerShell em execução no Windows.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-264">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="e7ca6-265">Esses tipos são úteis para construir facilmente AD e objetos WMI.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-265">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="e7ca6-266">Por exemplo, pode consultar ao utilizar o LDAP:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-266">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="e7ca6-267">Exemplo seguinte cria um objeto de Win32_OperatingSystem CIM:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-267">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="e7ca6-268">Este exemplo retorna um objeto de ManagementClass para a classe Win32_OperatingSystem.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-268">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="e7ca6-269">`-lp` alias de todos os `-LiteralPath` parâmetros</span><span class="sxs-lookup"><span data-stu-id="e7ca6-269">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="e7ca6-270">Graças à [ @kvprasoon ](https://github.com/kvprasoon), agora temos um alias de parâmetro `-lp` todos os incorporada cmdlets do PowerShell que tenham um `-LiteralPath` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-270">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="e7ca6-271">Alterações Interruptivas</span><span class="sxs-lookup"><span data-stu-id="e7ca6-271">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="e7ca6-272">Caminhos de instalação baseada em MSI no Windows</span><span class="sxs-lookup"><span data-stu-id="e7ca6-272">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="e7ca6-273">No Windows, o pacote MSI instala agora para o seguinte caminho:</span><span class="sxs-lookup"><span data-stu-id="e7ca6-273">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="e7ca6-274">`$env:ProgramFiles\PowerShell\6\` para a instalação estável do 6.x</span><span class="sxs-lookup"><span data-stu-id="e7ca6-274">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="e7ca6-275">`$env:ProgramFiles\PowerShell\6-preview\` para a instalação de pré-visualização do 6.x</span><span class="sxs-lookup"><span data-stu-id="e7ca6-275">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="e7ca6-276">Esta alteração garante que o PowerShell Core pode ser atualizado/atendido pelo Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-276">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="e7ca6-277">Para obter mais informações, confira [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="e7ca6-277">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="e7ca6-278">Telemetria só pode ser desativada com uma variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="e7ca6-278">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="e7ca6-279">O PowerShell Core envia dados de telemetria básico para a Microsoft quando é iniciado.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-279">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="e7ca6-280">Os dados incluem o nome do SO, versão do SO e versão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-280">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="e7ca6-281">Estes dados permite-nos compreender melhor os ambientes nos quais o PowerShell é utilizado e permite-nos atribuir prioridades a novas funcionalidades e correções.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-281">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="e7ca6-282">Para sair desta telemetria, defina a variável de ambiente `POWERSHELL_TELEMETRY_OPTOUT` para `true`, `yes`, ou `1`.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-282">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="e7ca6-283">Já não suportamos a eliminação do ficheiro `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` para desativar a telemetria.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-283">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="e7ca6-284">Não são permitidas autenticação básica através de HTTP na comunicação remota do PowerShell em plataformas de Unix</span><span class="sxs-lookup"><span data-stu-id="e7ca6-284">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="e7ca6-285">Para impedir a utilização de tráfego não criptografado, a comunicação remota do PowerShell em plataformas Unix agora requer a utilização de NTLM/negociar ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-285">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="e7ca6-286">Para obter mais informações sobre estas alterações, confira [problema #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span><span class="sxs-lookup"><span data-stu-id="e7ca6-286">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="e7ca6-287">Removido `VisualBasic` como um idioma suportado no Add-Type</span><span class="sxs-lookup"><span data-stu-id="e7ca6-287">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="e7ca6-288">No passado, poderia compilar código do Visual Basic utilizando o `Add-Type` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-288">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="e7ca6-289">Visual Basic foi raramente utilizado com `Add-Type`.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-289">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="e7ca6-290">Removemos esta funcionalidade para reduzir o tamanho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-290">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="e7ca6-291">Limpos usos de `CommandTypes.Workflow` e `WorkflowInfoCleaned`</span><span class="sxs-lookup"><span data-stu-id="e7ca6-291">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="e7ca6-292">Para obter mais informações sobre estas alterações, confira [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="e7ca6-292">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>

### <a name="group-object-now-sorts-the-groups"></a><span data-ttu-id="e7ca6-293">Os grupos ordena agora de objeto de grupo</span><span class="sxs-lookup"><span data-stu-id="e7ca6-293">Group-Object now sorts the groups</span></span>

<span data-ttu-id="e7ca6-294">Como parte da melhoria no desempenho, `Group-Object` agora retorna uma lista classificada dos grupos.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-294">As part of the performance improvement, `Group-Object` now returns a sorted listing of the groups.</span></span>
<span data-ttu-id="e7ca6-295">Embora não deve confiar na ordem, poderia ser quebrada por esta alteração se quisesse que o primeiro grupo.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-295">Although you should not rely on the order, you could be broken by this change if you wanted the first group.</span></span> <span data-ttu-id="e7ca6-296">Decidimos que essa melhoria de desempenho era que vale a pena a alteração, uma vez que o impacto de ser dependentes do comportamento anterior é baixo.</span><span class="sxs-lookup"><span data-stu-id="e7ca6-296">We decided that this performance improvement was worth the change since the impact of being dependent on previous behavior is low.</span></span>

<span data-ttu-id="e7ca6-297">Para obter mais informações sobre esta alteração, consulte [problema #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span><span class="sxs-lookup"><span data-stu-id="e7ca6-297">For more information on this change, see [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span></span>
