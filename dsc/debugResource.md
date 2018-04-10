---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Depurar os recursos de DSC
ms.openlocfilehash: 6a1f4b04a11185c2cfe9be26324bd66ed13ca7dd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="3aae1-103">Depurar os recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="3aae1-103">Debugging DSC resources</span></span>

> <span data-ttu-id="3aae1-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3aae1-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="3aae1-105">No PowerShell 5.0, uma nova funcionalidade introduzida na pretendido Estado elementos (DSC) que permite-lhe depurar um recurso de DSC como um configuration está a ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="3aae1-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="3aae1-106">Ativar depuração de DSC</span><span class="sxs-lookup"><span data-stu-id="3aae1-106">Enabling DSC debugging</span></span>
<span data-ttu-id="3aae1-107">Antes de pode depurar um recurso, tem de ativar a depuração de chamar o [ativar DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3aae1-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.</span></span>
<span data-ttu-id="3aae1-108">Este cmdlet assume um parâmetro obrigatório, **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="3aae1-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="3aae1-109">Pode verificar que a depuração foi ativada ao observar o resultado de uma chamada para [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span><span class="sxs-lookup"><span data-stu-id="3aae1-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span></span>

<span data-ttu-id="3aae1-110">A saída do PowerShell seguinte mostra o resultado da ativação da depuração:</span><span class="sxs-lookup"><span data-stu-id="3aae1-110">The following PowerShell output shows the result of enabling debugging:</span></span>


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


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="3aae1-111">A partir de uma configuração com a depuração ativada</span><span class="sxs-lookup"><span data-stu-id="3aae1-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="3aae1-112">Para depurar um recurso de DSC, inicie uma configuração que chama esse recurso.</span><span class="sxs-lookup"><span data-stu-id="3aae1-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="3aae1-113">Neste exemplo, vamos ver uma configuração simple que chama o [WindowsFeature](windowsfeatureResource.md) recursos para se certificar de que a funcionalidade de "WindowsPowerShellWebAccess" está instalada:</span><span class="sxs-lookup"><span data-stu-id="3aae1-113">For this example, we'll look at a simple configuration that calls the [WindowsFeature](windowsfeatureResource.md) resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

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
<span data-ttu-id="3aae1-114">Depois de compilar a configuração, inicie-o ao chamar [início DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="3aae1-114">After compiling the configuration, start it by calling [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span></span>
<span data-ttu-id="3aae1-115">A configuração irá parar quando chama o Gestor de configuração Local (MMC) para o recurso primeiro na configuração.</span><span class="sxs-lookup"><span data-stu-id="3aae1-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="3aae1-116">Se utilizar o `-Verbose` e `-Wait` parâmetros, a saída apresenta as linhas tem de introduzir para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="3aae1-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

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
<span data-ttu-id="3aae1-117">Neste momento, o MMC tem o recurso for chamada e enviadas para o primeiro ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="3aae1-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="3aae1-118">As últimas três linhas na saída mostram como ligar ao processo e iniciar a depurar o script de recursos.</span><span class="sxs-lookup"><span data-stu-id="3aae1-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="3aae1-119">Depurar o script de recursos</span><span class="sxs-lookup"><span data-stu-id="3aae1-119">Debugging the resource script</span></span>

<span data-ttu-id="3aae1-120">Inicie uma nova instância do ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3aae1-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="3aae1-121">No painel de consola, introduza as últimas três linhas de saída do `Start-DscConfiguration` de saída como comandos, substituindo `<credentials>` com credenciais de utilizador válido.</span><span class="sxs-lookup"><span data-stu-id="3aae1-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="3aae1-122">Deverá ver uma linha semelhante a:</span><span class="sxs-lookup"><span data-stu-id="3aae1-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="3aae1-123">O script de recursos irá abrir no painel de script e o depurador for parado, a primeira linha do **teste TargetResource** função (a **Test()** método de um recurso com base na classe).</span><span class="sxs-lookup"><span data-stu-id="3aae1-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="3aae1-124">Agora, pode utilizar os comandos de depuração no ISE para seguir o script de recursos, observe os valores das variáveis, ver a pilha de chamadas e assim sucessivamente.</span><span class="sxs-lookup"><span data-stu-id="3aae1-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span>
<span data-ttu-id="3aae1-125">Para obter informações sobre depuração no ISE do PowerShell, consulte [como depurar Scripts no ISE do Windows PowerShell](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span><span class="sxs-lookup"><span data-stu-id="3aae1-125">For information about debugging in the PowerShell ISE, see [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span></span>
<span data-ttu-id="3aae1-126">Lembre-se de que todas as linhas de script de recursos (ou classe) está definida como um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="3aae1-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="3aae1-127">Desativar a depuração de DSC</span><span class="sxs-lookup"><span data-stu-id="3aae1-127">Disabling DSC debugging</span></span>

<span data-ttu-id="3aae1-128">Após a chamada [ativar DscDebug](https://technet.microsoft.com/library/mt517870.aspx), todas as chamadas para [início DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) resultará na configuração interrompendo ao depurador.</span><span class="sxs-lookup"><span data-stu-id="3aae1-128">After calling [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx), all calls to [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="3aae1-129">Para permitir que as configurações executar normalmente, tem de desativar a depuração ao chamar o [desativar DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3aae1-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span></span>

><span data-ttu-id="3aae1-130">**Nota:** Rebooting não altera o estado de depuração do MMC.</span><span class="sxs-lookup"><span data-stu-id="3aae1-130">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="3aae1-131">Se a depuração está ativada, a partir de uma configuração irá ainda aceder ao depurador após um reinício.</span><span class="sxs-lookup"><span data-stu-id="3aae1-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>


## <a name="see-also"></a><span data-ttu-id="3aae1-132">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="3aae1-132">See Also</span></span>
- [<span data-ttu-id="3aae1-133">Escrever um recurso personalizado de DSC com MOF</span><span class="sxs-lookup"><span data-stu-id="3aae1-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="3aae1-134">Escrever um recurso personalizado de DSC com classes de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3aae1-134">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)