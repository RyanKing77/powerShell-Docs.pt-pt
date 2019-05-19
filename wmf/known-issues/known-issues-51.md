---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Problemas conhecidos no WMF 5.1
ms.openlocfilehash: 8348f9d45dca32dcda2ef8baa75d586c8728d0a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856365"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="40605-103">Problemas conhecidos no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="40605-103">Known Issues in WMF 5.1</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="40605-104">A iniciar o atalho para o PowerShell como administrador</span><span class="sxs-lookup"><span data-stu-id="40605-104">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="40605-105">Após a instalação de WMF, se tentar iniciar o PowerShell como administrador a partir do atalho, poderá receber uma mensagem de "Erro não especificado".</span><span class="sxs-lookup"><span data-stu-id="40605-105">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span> <span data-ttu-id="40605-106">Reabra o atalho como não-administrador e o atalho agora funciona até mesmo como administrador.</span><span class="sxs-lookup"><span data-stu-id="40605-106">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="40605-107">Pester</span><span class="sxs-lookup"><span data-stu-id="40605-107">Pester</span></span>

<span data-ttu-id="40605-108">Nesta versão, há dois problemas que deve estar ciente de quando utilizar Pester no servidor Nano:</span><span class="sxs-lookup"><span data-stu-id="40605-108">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="40605-109">Execução de testes no Pester em si pode resultar em algumas falhas devido às diferenças entre o CLR completa e CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="40605-109">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="40605-110">Em particular, o **Validate** método não está disponível na **XmlDocument** tipo.</span><span class="sxs-lookup"><span data-stu-id="40605-110">In particular, the **Validate** method is not available on the **XmlDocument** type.</span></span> <span data-ttu-id="40605-111">Testes de seis que tentam validar o esquema dos registos de saída do NUnit são conhecidos para efetuar a ativação.</span><span class="sxs-lookup"><span data-stu-id="40605-111">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="40605-112">Um teste de cobertura de código falha porque o **WindowsFeature** recursos de DSC não existe no servidor Nano.</span><span class="sxs-lookup"><span data-stu-id="40605-112">One code coverage test fails because the **WindowsFeature** DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="40605-113">No entanto, estas falhas são geralmente benignas e podem ser ignoradas com segurança.</span><span class="sxs-lookup"><span data-stu-id="40605-113">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="40605-114">Validação da operação</span><span class="sxs-lookup"><span data-stu-id="40605-114">Operation Validation</span></span>

- <span data-ttu-id="40605-115">`Update-Help` Falha do módulo de Microsoft.PowerShell.Operation.Validation devido a URI de ajuda de descanso</span><span class="sxs-lookup"><span data-stu-id="40605-115">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="40605-116">DSC depois de desinstalar o WMF</span><span class="sxs-lookup"><span data-stu-id="40605-116">DSC after uninstall WMF</span></span>

- <span data-ttu-id="40605-117">Desinstalar o WMF não elimina os documentos de MOF de DSC a partir da pasta de configuração.</span><span class="sxs-lookup"><span data-stu-id="40605-117">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="40605-118">DSC não funcionará corretamente se os documentos MOF contenham propriedades mais recentes que não estão disponíveis nos sistemas mais antigos.</span><span class="sxs-lookup"><span data-stu-id="40605-118">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="40605-119">Neste caso, execute o seguinte script de consola elevada do PowerShell para limpar os Estados de DSC.</span><span class="sxs-lookup"><span data-stu-id="40605-119">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="40605-120">Contas de Virtual de JEA</span><span class="sxs-lookup"><span data-stu-id="40605-120">JEA Virtual Accounts</span></span>

<span data-ttu-id="40605-121">Pontos finais JEA e configurações de sessão configuradas para utilizar contas virtuais no WMF 5.0 não irão ser configuradas para utilizar uma conta virtual após a atualização para o WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="40605-121">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span> <span data-ttu-id="40605-122">Isso significa que os comandos são executados em sessões JEA serão executado na identidade do usuário conectado, em vez de uma conta de administrador temporário, potencialmente a impedir que o utilizador executar comandos que requerem privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="40605-122">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span> <span data-ttu-id="40605-123">Para restaurar as contas virtuais, terá de anular o registo e voltar a registar quaisquer configurações de sessão que utilizam contas virtuais.</span><span class="sxs-lookup"><span data-stu-id="40605-123">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

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