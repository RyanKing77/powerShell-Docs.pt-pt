---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Depurar os recursos de DSC
ms.openlocfilehash: c088e13a25ba31ceebaf52b2d24b5d32b96ae2fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076808"
---
# <a name="debugging-dsc-resources"></a>Depurar os recursos de DSC

> Aplica-se a: Windows PowerShell 5.0

No PowerShell 5.0, um novo recurso foi introduzido no Desired State Configuration (DSC) que lhe permite depurar um recurso de DSC pois está a ser aplicada uma configuração.

## <a name="enabling-dsc-debugging"></a>Ativar a depuração de DSC
Antes de pode depurar um recurso, tem de ativar a depuração ao chamar o [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.
Este cmdlet utiliza um parâmetro obrigatório, **BreakAll**.

Pode verificar que a depuração foi ativada ao observar o resultado de uma chamada para [Get-dsclocalconfigurationmanager para](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

O resultado de PowerShell seguinte mostra o resultado de habilitar a depuração:


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


## <a name="starting-a-configuration-with-debug-enabled"></a>A partir de uma configuração com depuração ativada
Para depurar um recurso de DSC, inicie uma configuração que chama esse recurso.
Neste exemplo, vamos examinar uma configuração simples que chama o **WindowsFeature** recursos para garantir que a funcionalidade de "WindowsPowerShellWebAccess" está instalada:

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
Depois de compilar a configuração, inicie-o ao chamar [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).
A configuração irá parar quando o Gestor de configuração Local (LCM) chama o primeiro recurso na configuração.
Se utilizar o `-Verbose` e `-Wait` parâmetros, a saída apresenta as linhas tem de introduzir para iniciar a depuração.

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
Neste momento, o LCM tem chamado o recurso e são fornecidos para o primeiro ponto de interrupção.
As últimas três linhas na saída mostram-lhe como anexar ao processo e começar a depurar o script de recursos.

## <a name="debugging-the-resource-script"></a>O script de recursos de depuração

Inicie uma nova instância do ISE do PowerShell.
No painel da consola, introduza as últimas três linhas de saída a partir da `Start-DscConfiguration` saída como comandos, substituindo `<credentials>` com credenciais de utilizador válido.
Agora, deverá ver uma linha de comandos que é semelhante a:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

O script de recursos será aberta num painel de script, e o depurador é interrompido na primeira linha dos **teste TargetResource** função (a **Test()** método de um recurso baseado em classes).
Agora, pode utilizar os comandos de depuração no ISE para percorrer o script de recursos, examinar os valores das variáveis, ver a pilha de chamadas e assim por diante. Lembre-se de que cada linha no script o recurso (ou classe) está definida como um ponto de interrupção.

## <a name="disabling-dsc-debugging"></a>Desativar a depuração de DSC

Após chamar [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), todas as chamadas para [início-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) resultará na configuração de última hora no depurador. Para permitir que as configurações para serem executados normalmente, tem de desativar a depuração ao chamar o [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.

>**Nota:** A reiniciar não altera o estado de depuração do LCM. Se estiver ativada a depuração, a partir de uma configuração ainda interromperá no depurador após um reinício.

## <a name="see-also"></a>Veja Também

- [Escrever um recurso personalizado do DSC com o MOF](../resources/authoringResourceMOF.md)
- [Escrever um recurso personalizado do DSC com classes do PowerShell](../resources/authoringResourceClass.md)
