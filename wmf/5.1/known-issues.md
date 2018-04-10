---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Problemas conhecidos no WMF 5.1
ms.openlocfilehash: 467a191f40d85bfca7c794915d6274a9a1b201e7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="e3e18-103">Problemas conhecidos no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="e3e18-103">Known Issues in WMF 5.1</span></span> #

> <span data-ttu-id="e3e18-104">Nota: Estas informações estão sujeitas a alterações.</span><span class="sxs-lookup"><span data-stu-id="e3e18-104">Note: This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="e3e18-105">Iniciar o atalho do PowerShell como administrador</span><span class="sxs-lookup"><span data-stu-id="e3e18-105">Starting PowerShell shortcut as Administrator</span></span>
<span data-ttu-id="e3e18-106">Após instalar o WMF, se tentar inicie o PowerShell como administrador a partir do atalho, poderá receber uma mensagem de "Erro não especificado".</span><span class="sxs-lookup"><span data-stu-id="e3e18-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="e3e18-107">Reabra o atalho como não administrador e o atalho funciona agora mesmo como administrador.</span><span class="sxs-lookup"><span data-stu-id="e3e18-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="e3e18-108">Pester</span><span class="sxs-lookup"><span data-stu-id="e3e18-108">Pester</span></span>
<span data-ttu-id="e3e18-109">Nesta versão, existem dois problemas que deve ter conhecimento ao utilizar Pester num servidor de Nano:</span><span class="sxs-lookup"><span data-stu-id="e3e18-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

* <span data-ttu-id="e3e18-110">A execução de testes no Pester próprio pode resultar em algumas falhas devido às diferenças entre CLR completas e NÚCLEO CLR.</span><span class="sxs-lookup"><span data-stu-id="e3e18-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="e3e18-111">Em particular, o método Validate não está disponível no tipo XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="e3e18-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="e3e18-112">Testes de seis que tentarem validar o esquema dos registos de saída NUnit são conhecidos falhar.</span><span class="sxs-lookup"><span data-stu-id="e3e18-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
* <span data-ttu-id="e3e18-113">Um teste de cobertura de código atualmente falha porque o *WindowsFeature* recursos de DSC não existe no servidor de nano for apresentado.</span><span class="sxs-lookup"><span data-stu-id="e3e18-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="e3e18-114">No entanto, estas falhas são geralmente benignas e podem ser ignoradas.</span><span class="sxs-lookup"><span data-stu-id="e3e18-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="e3e18-115">Validação da operação</span><span class="sxs-lookup"><span data-stu-id="e3e18-115">Operation Validation</span></span>

* <span data-ttu-id="e3e18-116">Update-Help falha por Microsoft.PowerShell.Operation.Validation módulo devido a ajuda de descanso URI</span><span class="sxs-lookup"><span data-stu-id="e3e18-116">Update-Help fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="e3e18-117">DSC após desinstalar WMF</span><span class="sxs-lookup"><span data-stu-id="e3e18-117">DSC after uninstall WMF</span></span>
* <span data-ttu-id="e3e18-118">Desinstalar o WMF não eliminar documentos DSC MOF da pasta de configuração.</span><span class="sxs-lookup"><span data-stu-id="e3e18-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="e3e18-119">DSC não irão funcionar corretamente se os documentos MOF contêm propriedades mais recentes que não estão disponíveis nos sistemas operativos mais antigos.</span><span class="sxs-lookup"><span data-stu-id="e3e18-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="e3e18-120">Neste caso, execute o seguinte script na consola do PowerShell elevada para limpar os Estados de DSC.</span><span class="sxs-lookup"><span data-stu-id="e3e18-120">In this case, run the following script from elevated PowerShell console to to clean up the DSC states.</span></span>
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="e3e18-121">Contas de Virtual JEA</span><span class="sxs-lookup"><span data-stu-id="e3e18-121">JEA Virtual Accounts</span></span>
<span data-ttu-id="e3e18-122">Pontos finais JEA e configurações de sessão configuradas para utilizar as contas virtual no WMF 5.0 não serão configuradas para utilizar uma conta virtual após a atualização para o WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="e3e18-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="e3e18-123">Isto significa que os comandos executados em sessões JEA serão executados com a ligação identidade do utilizador em vez de uma conta de administrador temporário, potencialmente a impedir que o utilizador executar comandos que precise de privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="e3e18-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="e3e18-124">Para restaurar as contas virtuais, terá de anular o registo e volte a registar as configurações de sessão que utilizem contas virtuais.</span><span class="sxs-lookup"><span data-stu-id="e3e18-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```