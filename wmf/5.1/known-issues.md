---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Problemas conhecidos no WMF 5.1
ms.openlocfilehash: 74e5a6763a8a780000bf876f34caa9646a2a416a
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892142"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="7e0b8-103">Problemas conhecidos no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="7e0b8-103">Known Issues in WMF 5.1</span></span>

> [!Note]
> <span data-ttu-id="7e0b8-104">Estas informações estão sujeitas a alterações.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-104">This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="7e0b8-105">A iniciar o atalho para o PowerShell como administrador</span><span class="sxs-lookup"><span data-stu-id="7e0b8-105">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="7e0b8-106">Após a instalação de WMF, se tentar iniciar o PowerShell como administrador a partir do atalho, poderá receber uma mensagem de "Erro não especificado".</span><span class="sxs-lookup"><span data-stu-id="7e0b8-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="7e0b8-107">Reabra o atalho como não-administrador e o atalho agora funciona até mesmo como administrador.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="7e0b8-108">Pester</span><span class="sxs-lookup"><span data-stu-id="7e0b8-108">Pester</span></span>

<span data-ttu-id="7e0b8-109">Nesta versão, há dois problemas que deve estar ciente de quando utilizar Pester no servidor Nano:</span><span class="sxs-lookup"><span data-stu-id="7e0b8-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="7e0b8-110">Execução de testes no Pester em si pode resultar em algumas falhas devido às diferenças entre o CLR completa e CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="7e0b8-111">Em particular, o método Validate não está disponível no tipo XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="7e0b8-112">Testes de seis que tentam validar o esquema dos registos de saída do NUnit são conhecidos para efetuar a ativação.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="7e0b8-113">Um teste de cobertura de código atualmente falha porque o *WindowsFeature* recursos de DSC não existe no servidor Nano.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="7e0b8-114">No entanto, estas falhas são geralmente benignas e podem ser ignoradas com segurança.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="7e0b8-115">Validação da operação</span><span class="sxs-lookup"><span data-stu-id="7e0b8-115">Operation Validation</span></span>

- <span data-ttu-id="7e0b8-116">`Update-Help` Falha do módulo de Microsoft.PowerShell.Operation.Validation devido a URI de ajuda de descanso</span><span class="sxs-lookup"><span data-stu-id="7e0b8-116">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="7e0b8-117">DSC depois de desinstalar o WMF</span><span class="sxs-lookup"><span data-stu-id="7e0b8-117">DSC after uninstall WMF</span></span>

- <span data-ttu-id="7e0b8-118">Desinstalar o WMF não elimina os documentos de MOF de DSC a partir da pasta de configuração.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="7e0b8-119">DSC não funcionará corretamente se os documentos MOF contenham propriedades mais recentes que não estão disponíveis nos sistemas mais antigos.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="7e0b8-120">Neste caso, execute o seguinte script de consola elevada do PowerShell para limpar os Estados de DSC.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-120">In this case, run the following script from elevated PowerShell console to to clean up the DSC states.</span></span>

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="7e0b8-121">Contas de Virtual de JEA</span><span class="sxs-lookup"><span data-stu-id="7e0b8-121">JEA Virtual Accounts</span></span>

<span data-ttu-id="7e0b8-122">Pontos finais JEA e configurações de sessão configuradas para utilizar contas virtuais no WMF 5.0 não irão ser configuradas para utilizar uma conta virtual após a atualização para o WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="7e0b8-123">Isso significa que os comandos são executados em sessões JEA serão executado na identidade do usuário conectado, em vez de uma conta de administrador temporário, potencialmente a impedir que o utilizador executar comandos que requerem privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="7e0b8-124">Para restaurar as contas virtuais, terá de anular o registo e voltar a registar quaisquer configurações de sessão que utilizam contas virtuais.</span><span class="sxs-lookup"><span data-stu-id="7e0b8-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

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