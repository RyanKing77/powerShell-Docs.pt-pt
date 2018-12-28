---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Depurar os recursos de DSC
ms.openlocfilehash: 9b2e7dd9b42332b869c4d7fabb21bd4b5a6b8800
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404917"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="5246d-103">Depurar os recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="5246d-103">Debugging DSC resources</span></span>

> <span data-ttu-id="5246d-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5246d-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="5246d-105">No PowerShell 5.0, um novo recurso foi introduzido no pretendido Estado Configuraiton (DSC) que lhe permite depurar um recurso de DSC pois está a ser aplicada uma configuração.</span><span class="sxs-lookup"><span data-stu-id="5246d-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="5246d-106">Ativar a depuração de DSC</span><span class="sxs-lookup"><span data-stu-id="5246d-106">Enabling DSC debugging</span></span>
<span data-ttu-id="5246d-107">Antes de pode depurar um recurso, tem de ativar a depuração ao chamar o [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5246d-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span></span>
<span data-ttu-id="5246d-108">Este cmdlet utiliza um parâmetro obrigatório, **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="5246d-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="5246d-109">Pode verificar que a depuração foi ativada ao observar o resultado de uma chamada para [Get-dsclocalconfigurationmanager para](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="5246d-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span></span>

<span data-ttu-id="5246d-110">O resultado de PowerShell seguinte mostra o resultado de habilitar a depuração:</span><span class="sxs-lookup"><span data-stu-id="5246d-110">The following PowerShell output shows the result of enabling debugging:</span></span>


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="5246d-111">A partir de uma configuração com depuração ativada</span><span class="sxs-lookup"><span data-stu-id="5246d-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="5246d-112">Para depurar um recurso de DSC, inicie uma configuração que chama esse recurso.</span><span class="sxs-lookup"><span data-stu-id="5246d-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="5246d-113">Neste exemplo, vamos examinar uma configuração simples que chama o **WindowsFeature** recursos para garantir que a funcionalidade de "WindowsPowerShellWebAccess" está instalada:</span><span class="sxs-lookup"><span data-stu-id="5246d-113">For this example, we'll look at a simple configuration that calls the **WindowsFeature** resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
<span data-ttu-id="5246d-114">Depois de compilar a configuração, inicie-o ao chamar [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="5246d-114">After compiling the configuration, start it by calling [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span></span>
<span data-ttu-id="5246d-115">A configuração irá parar quando o Gestor de configuração Local (LCM) chama o primeiro recurso na configuração.</span><span class="sxs-lookup"><span data-stu-id="5246d-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="5246d-116">Se utilizar o `-Verbose` e `-Wait` parâmetros, a saída apresenta as linhas tem de introduzir para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="5246d-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
<span data-ttu-id="5246d-117">Neste momento, o LCM tem chamado o recurso e são fornecidos para o primeiro ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="5246d-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="5246d-118">As últimas três linhas na saída mostram-lhe como anexar ao processo e começar a depurar o script de recursos.</span><span class="sxs-lookup"><span data-stu-id="5246d-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="5246d-119">O script de recursos de depuração</span><span class="sxs-lookup"><span data-stu-id="5246d-119">Debugging the resource script</span></span>

<span data-ttu-id="5246d-120">Inicie uma nova instância do ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5246d-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="5246d-121">No painel da consola, introduza as últimas três linhas de saída a partir da `Start-DscConfiguration` saída como comandos, substituindo `<credentials>` com credenciais de utilizador válido.</span><span class="sxs-lookup"><span data-stu-id="5246d-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="5246d-122">Agora, deverá ver uma linha de comandos que é semelhante a:</span><span class="sxs-lookup"><span data-stu-id="5246d-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="5246d-123">O script de recursos será aberta num painel de script, e o depurador é interrompido na primeira linha dos **teste TargetResource** função (a **Test()** método de um recurso baseado em classes).</span><span class="sxs-lookup"><span data-stu-id="5246d-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="5246d-124">Agora, pode utilizar os comandos de depuração no ISE para percorrer o script de recursos, examinar os valores das variáveis, ver a pilha de chamadas e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="5246d-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="5246d-125">Lembre-se de que cada linha no script o recurso (ou classe) está definida como um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="5246d-125">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="5246d-126">Desativar a depuração de DSC</span><span class="sxs-lookup"><span data-stu-id="5246d-126">Disabling DSC debugging</span></span>

<span data-ttu-id="5246d-127">Após chamar [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), todas as chamadas para [início-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) resultará na configuração de última hora no depurador.</span><span class="sxs-lookup"><span data-stu-id="5246d-127">After calling [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), all calls to [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="5246d-128">Para permitir que as configurações para serem executados normalmente, tem de desativar a depuração ao chamar o [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5246d-128">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span></span>

><span data-ttu-id="5246d-129">**Nota:** A reiniciar não altera o estado de depuração do LCM.</span><span class="sxs-lookup"><span data-stu-id="5246d-129">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="5246d-130">Se estiver ativada a depuração, a partir de uma configuração ainda interromperá no depurador após um reinício.</span><span class="sxs-lookup"><span data-stu-id="5246d-130">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>

## <a name="see-also"></a><span data-ttu-id="5246d-131">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5246d-131">See Also</span></span>

- [<span data-ttu-id="5246d-132">Escrever um recurso personalizado do DSC com o MOF</span><span class="sxs-lookup"><span data-stu-id="5246d-132">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="5246d-133">Escrever um recurso personalizado do DSC com classes do PowerShell</span><span class="sxs-lookup"><span data-stu-id="5246d-133">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
