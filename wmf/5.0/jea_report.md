---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2af56be1915c148809f52cd9040c45da160ae0a2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="reporting-on-jea"></a>Criar Relatórios na JEA
Para gerar relatórios sobre o estado da configuração JEA, pode utilizar:
1.  **Get-PSSessionConfiguration** devolver uma lista de todos os registado pontos finais num computador especificado.
2.  **Get-PSSessionCapability** para elaborar relatórios sobre as capacidades de qualquer utilizador especificado tem um ponto final específico.

Eis um exemplo de **Get-PSSessionCapability**:
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

Para elaborar relatórios sobre o _ações_ utilizadores demorou durante uma sessão JEA, pode:
1. Ativar as transcrições "over-a-por cima ombro ficará" para esse ponto final JEA e consulte o diretório de transcript para um registo das ações de cada utilizador completo
2. Ativar o registo de módulo do PowerShell e Inspecione os registos de eventos do PowerShell.