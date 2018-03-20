---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 32f8e20889ddc526def4b925e8d0761a2e851e19
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/20/2018
---
# <a name="unified-and-consistent-state-and-status-representation"></a>Estado Unificado e Consistente e Representação de Estado

Uma série de melhorias foram efetuadas nesta versão para automatizações incorporadas estado do MMC e estado de DSC. Estes incluem Estado unificado e consistente e a declaração de estado, datetime gerível propriedade dos objetos de estado devolvido pelo cmdlet Get-DscConfigurationStatus e modulação de propriedade de detalhes do Estado do MMC devolvida pelo Get-DscLocalConfigurationManager cmdlet.

A representação de estado do MMC e o estado da operação de DSC são Revisitado e unificada, de acordo com as seguintes regras:
1.  Recurso Notprocessed não afeta o estado do MMC e o estado de DSC.
2.  Parar o MMC recursos de processamento adicional depois de encontrar um recurso de que os pedidos de reinício.
3.  Um recurso de que os pedidos de reiniciar o computador não está no estado pretendido até que o reinício, na verdade, acontece.
4.  Depois de encontrar um recurso que falha, o MMC mantém os recursos de processamento adicional, desde que não são dependentes de falha de um.
5.  O estado geral devolvido pelo cmdlet Get-DscConfigurationStatus é o conjunto super de estado de todos os recursos.
6.  O estado de PendingReboot é um superconjunto do Estado de PendingConfiguration.

A tabela abaixo ilustra o resultante Estado relacionadas com propriedades em alguns cenários típicos.

| **Cenário**                    | **LCMState\***       | **Status** | **Reiniciar o computador solicitado**  | **ResourcesInDesiredState**  | **ResourcesNotInDesiredState** |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S**^**                          | Inativo                 | Sucesso    | $false        | S                            | $null                          |
| F**^**                          | PendingConfiguration | Falha    | $false        | $null                        | F                              |
| S, F                             | PendingConfiguration | Falha    | $false        | S                            | F                              |
| F, S                             | PendingConfiguration | Falha    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Falha    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Falha    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Sucesso    | $true         | S                            | r                              |
| F, r                            | PendingReboot        | Falha    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Sucesso    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Sucesso    | $true         | $null                        | r                              |

^ S<sub>posso</sub>: uma série de recursos que aplicada com êxito F<sub>posso</sub>: uma série de recursos que aplicadas sem êxito r: um recurso que requer o reinício \*

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Melhoramento no cmdlet Get-DscConfigurationStatus

Foram efetuados alguns melhoramentos para o cmdlet Get-DscConfigurationStatus nesta versão. Anteriormente, a propriedade StartDate de objetos devolvido pelo cmdlet é do tipo cadeia. Agora, é do tipo Datetime, que permite complexas a seleção e filtragem mais fácil com base nas propriedades de intrínsecos de um objeto de Datetime.
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

Segue-se um exemplo que devolve que todos os registos de operação de DSC acontecido no mesmo dia da semana como hoje.
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Registos de operações que não faça alterações à configuração do nó (ou seja, apenas operações de leitura) são eliminados. Por conseguinte, teste-DscConfiguration operações Get-DscConfiguration são já não adulterated no devolveu objetos do cmdlet Get-DscConfigurationStatus.
Registos de operação de definição de configuração de metadados é adicionada para o retorno do cmdlet Get-DscConfigurationStatus.

Segue-se um exemplo do resultado devolvido pelo Get-DscConfigurationStatus – todas as cmdlet.
```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a>Melhoramento no cmdlet Get-DscLocalConfigurationManager
O objeto devolvido pelo cmdlet Get-DscLocalConfigurationManager é adicionado um novo campo de LCMStateDetail. Este campo é preenchido quando LCMState é "Ocupado". Pode ser obtida pelo seguinte cmdlet:
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Segue-se um exemplo de resultado de uma monitorização contínua numa configuração de que necessita de dois reinícios num nó remoto.
```powershell
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```

