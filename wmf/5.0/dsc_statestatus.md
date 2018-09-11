---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339876"
---
# <a name="unified-and-consistent-state-and-status-representation"></a>Estado Unificado e Consistente e Representação de Estado

Uma série de aprimoramentos foram feitos nesta versão para automatizações de fluxos de criado o estado do LCM e o estado de DSC. Estes incluem unificadas e consistentes Estado representações, propriedade datetime gerenciável de objetos de estado devolvido pelo `Get-DscConfigurationStatus` cmdlet e LCM aprimorado Estado propriedade detalhes devolvida por `Get-DscLocalConfigurationManager` cmdlet.

A representação de estado do LCM e o estado da operação de DSC são revisitada e unificação de acordo com as seguintes regras:

1. Recursos de Notprocessed não afetam o estado do LCM e o estado de DSC.
2. LCM parar recursos de processamento adicionais depois de encontrar um recurso que pede o reinício.
3. Um recurso que pede o reinício não está no estado pretendido até que realmente acontece reinício.
4. Depois de encontrar um recurso que não consegue, LCM mantém processar ainda mais recursos, desde que não são dependentes de uma falha.
5. O estado geral devolvido pelo `Get-DscConfigurationStatus` cmdlet é o conjunto super de estado de todos os recursos.
6. O estado de PendingReboot é um superconjunto do Estado de PendingConfiguration.

A tabela abaixo ilustra o resultante Estado relacionadas com as propriedades em alguns cenários típicos.

| Cenário                        | LCMState             | Estado     | Pedido de reinício | ResourcesInDesiredState   | ResourcesNotInDesiredState |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S<sub>eu</sub>                   | Inativo                 | Sucesso    | $false        | S                            | $null                          |
| F<sub>eu</sub>                   | PendingConfiguration | Falha    | $false        | $null                        | F                              |
| S, F                             | PendingConfiguration | Falha    | $false        | S                            | F                              |
| F, S                             | PendingConfiguration | Falha    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Falha    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Falha    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, o r                            | PendingReboot        | Sucesso    | $true         | S                            | r                              |
| F, r                            | PendingReboot        | Falha    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Sucesso    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Sucesso    | $true         | $null                        | r                              |

- S<sub>eu</sub>: uma série de recursos que são aplicadas com êxito
- F<sub>eu</sub>: uma série de recursos que são aplicadas sem êxito
- r: um recurso que exige reinicialização

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Melhoria no cmdlet Get-DscConfigurationStatus

Foram feitas algumas melhorias para `Get-DscConfigurationStatus` cmdlet nesta versão. Anteriormente, a propriedade StartDate de objetos devolvido pelo cmdlet é do tipo cadeia. Agora, é do tipo Datetime, que permite complexos selecionando e filtragem mais fácil com base nas propriedades de intrínsecas de um objeto de Datetime.

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

O exemplo seguinte devolve todos os registos de operação de DSC que aconteceram no mesmo dia da semana, como o dia atual.

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Registos de operações que não faça alterações na configuração do nó (ou seja, apenas operações de leitura) são eliminados. Por conseguinte, `Test-DscConfiguration`, `Get-DscConfiguration` operações já não são adulterated em objetos devolvidos de `Get-DscConfigurationStatus` cmdlet. Registos de operação de definição de configuração de metadados é adicionada para o retorno de `Get-DscConfigurationStatus` cmdlet.

Segue-se um exemplo de resultado da `Get-DscConfigurationStatus –All` cmdlet.

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a>Melhoria no cmdlet Get-dsclocalconfigurationmanager para

Um novo campo de LCMStateDetail é adicionado para o objeto devolvido do `Get-DscLocalConfigurationManager` cmdlet. Este campo é preenchido quando LCMState é "Ocupado". Pode ser obtido pelo cmdlet seguinte:

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Segue-se uma saída de exemplo de uma monitorização contínua na configuração que requer dois reinícios num nó remoto.

```output
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
