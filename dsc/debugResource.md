---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "A depuração de recursos de DSC"
ms.openlocfilehash: 944eca3d9f21d7e06d128caf19e4aebacc5c0b26
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="debugging-dsc-resources"></a>A depuração de recursos de DSC

> Aplica-se a: O Windows PowerShell 5.0

No PowerShell 5.0, uma nova funcionalidade introduzida na pretendido Estado elementos (DSC) que permite-lhe depurar um recurso de DSC como um configuration está a ser aplicada.

## <a name="enabling-dsc-debugging"></a>Ativar depuração de DSC
Antes de pode depurar um recurso, tem de ativar a depuração de chamar o [ativar DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx) cmdlet. Este cmdlet assume um parâmetro obrigatório, **BreakAll**. 

Pode verificar que a depuração foi ativada ao observar o resultado de uma chamada para [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).

A saída do PowerShell seguinte mostra o resultado da ativação da depuração:


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


## <a name="starting-a-configuration-with-debug-enabled"></a>A partir de uma configuração com a depuração ativada
Para depurar um recurso de DSC, inicie uma configuração que chama esse recurso. Neste exemplo, vamos ver uma configuração simple que chama o [WindowsFeature](windowsfeatureResource.md) recursos para se certificar de que a funcionalidade de "WindowsPowerShellWebAccess" está instalada:

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
Depois de compilar a configuração, inicie-o ao chamar [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). A configuração irá parar quando chama o Gestor de configuração Local (MMC) para o recurso primeiro na configuração. Se utilizar o `-Verbose` e `-Wait` parâmetros, a saída apresenta as linhas tem de introduzir para iniciar a depuração.

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
Neste momento, o MMC tem o recurso for chamada e enviadas para o primeiro ponto de interrupção. As últimas três linhas na saída mostram como ligar ao processo e iniciar a depurar o script de recursos.

## <a name="debugging-the-resource-script"></a>Depurar o script de recursos

Inicie uma nova instância do ISE do PowerShell. No painel de consola, introduza as últimas três linhas de saída do `Start-DscConfiguration` de saída como comandos, substituindo `<credentials>` com credenciais de utilizador válido. Deverá ver uma linha semelhante a:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

O script de recursos irá abrir no painel de script e o depurador for parado, a primeira linha do **teste TargetResource** função (a **Test()** método de um recurso com base na classe).
Agora, pode utilizar os comandos de depuração no ISE para seguir o script de recursos, observe os valores das variáveis, ver a pilha de chamadas e assim sucessivamente. Para obter informações sobre depuração no ISE do PowerShell, consulte [como depurar Scripts no ISE do Windows PowerShell](https://technet.microsoft.com/en-us/library/dd819480.aspx). Lembre-se de que todas as linhas de script de recursos (ou classe) está definida como um ponto de interrupção.

## <a name="disabling-dsc-debugging"></a>Desativar a depuração de DSC

Após a chamada [ativar DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx), todas as chamadas para [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) resultará na configuração interrompendo ao depurador. Para permitir que as configurações executar normalmente, tem de desativar a depuração ao chamar o [desativar DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.

>**Nota:** Rebooting não altera o estado de depuração do MMC. Se a depuração está ativada, a partir de uma configuração irá ainda aceder ao depurador após um reinício.


## <a name="see-also"></a>Consulte Também
- [Escrever um recurso personalizado de DSC com MOF](authoringResourceMOF.md) 
- [Escrever um recurso personalizado de DSC com classes de PowerShell](authoringResourceClass.md)

