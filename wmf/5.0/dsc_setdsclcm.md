---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f30f43265d9daa47383e42f0f8abf4844365ea6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057955"
---
# <a name="set-dsclocalconfigurationmanager-cmdlet-supports--force-parameter"></a><span data-ttu-id="d334b-102">Cmdlet Set-dsclocalconfigurationmanager para suporta - o parâmetro force</span><span class="sxs-lookup"><span data-stu-id="d334b-102">Set-DscLocalConfigurationManager cmdlet supports -force parameter</span></span>

<span data-ttu-id="d334b-103">Foi adicionado um suporte para o novo parâmetro para o cmdlet Set-dsclocalconfigurationmanager para.</span><span class="sxs-lookup"><span data-stu-id="d334b-103">We have added a support for new parameter to Set-DscLocalConfigurationManager cmdlet.</span></span> <span data-ttu-id="d334b-104">Isso permitirá que o utilizador reponha a configuração de meta no computador forma não determinística quando outras operações como a verificação de consistência estão em execução em segundo plano como fará com que todas as operações em execução ser parado.</span><span class="sxs-lookup"><span data-stu-id="d334b-104">This will allow the user to reset meta configuration on machine deterministically when other operations like consistency check are running in background as it will cause all running operations to be stopped.</span></span>

<span data-ttu-id="d334b-105">A experiência fica assim ao tentar definir a configuração de meta sem – parâmetro Force.</span><span class="sxs-lookup"><span data-stu-id="d334b-105">The experience looks like this when trying to set meta configuration without –Force parameter.</span></span>
```powershell
PS C:\\Configs&gt; Set-DscLocalConfigurationManager -Path .\\MetaTest1\\ -Verbose
VERBOSE: Performing the operation "Start-DscConfiguration: SendMetaConfigurationApply" on target "MSFT\_DSCLocalConfigurationManager".
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendMetaConfigurationApply,'className' = MSFT\_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer DEV-10586-465 with user sid S-1-5-21-2127521184-1604012920-1887927527-5557045.
Cannot invoke the Set-DscLocalConfigurationManager cmdlet. The Consistency Check or Pull cmdlet is in progress and must return before
Set-DscLocalConfigurationManager can be invoked. Use -Force option if that is available to cancel the current operation.
+ CategoryInfo : NotSpecified: (root/Microsoft/...gurationManager:String) \[\], CimException
+ FullyQualifiedErrorId : MI RESULT 1
+ PSComputerName : localhost
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Set-DscLocalConfigurationManager finished in 0.046 seconds.
```

<span data-ttu-id="d334b-106">Quando usamos – forçá-lo com êxito atualiza a configuração de meta no sistema ao cancelar a operação atual em execução na máquina.</span><span class="sxs-lookup"><span data-stu-id="d334b-106">When we use –force it successfully updates the meta configuration on system by canceling the current running operation on the machine.</span></span>
```powershell
PS C:\\Configs&gt; Set-DscLocalConfigurationManager -Path .\\MetaTest1\\ -Verbose -Force
VERBOSE: Performing the operation "Start-DscConfiguration: SendMetaConfigurationApply" on target "MSFT\_DSCLocalConfigurationManager".
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendMetaConfigurationApply,'className' = MSFT\_DSCLocalConfigurationManager,'n
amespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer DEV-10586-465 with user sid S-1-5-21-2127521184-1604012920-1887927527-5557045.
VERBOSE: The -Force option was specified with the Stop operation. The current configuration has been successfully cancelled.
VERBOSE: An LCM method call arrived from computer DEV-10586-465 with user sid S-1-5-21-2127521184-1604012920-1887927527-5557045.
VERBOSE: \[DEV-10586-465\]: LCM: \[ Start Set \]
VERBOSE: \[DEV-10586-465\]: LCM: \[ Start Resource \] \[MSFT\_DSCMetaConfiguration\]
VERBOSE: \[DEV-10586-465\]: LCM: \[ Start Set \] \[MSFT\_DSCMetaConfiguration\]
VERBOSE: \[DEV-10586-465\]: LCM: \[ End Set \] \[MSFT\_DSCMetaConfiguration\] in 0.0310 seconds.
VERBOSE: \[DEV-10586-465\]: LCM: \[ End Resource \] \[MSFT\_DSCMetaConfiguration\]
VERBOSE: \[DEV-10586-465\]: LCM: \[ End Set \]
VERBOSE: \[DEV-10586-465\]: LCM: \[ End Set \] in 0.1410 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Set-DscLocalConfigurationManager finished in 0.421 seconds.
```
