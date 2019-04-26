---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085265"
---
# <a name="reporting-on-jea"></a>Criar Relatórios na JEA

Para relatar o estado da sua configuração de JEA, pode usar:

1. **Get-PSSessionConfiguration** devolver uma lista de todos os registado pontos de extremidade num determinado computador.
2. **Get-PSSessionCapability** para gerar relatórios sobre as capacidades de qualquer usuário tem sobre um ponto de extremidade específico.

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

Para gerar relatórios sobre o _ações_ utilizadores demorou durante uma sessão JEA, pode:

1. Ativar as transcrições de "over-the-the shoulder" para esse ponto final da JEA e consulte o diretório de transcrição para um registo completo das ações de cada utilizador
2. Ativar o registo de módulo do PowerShell e Inspecione os registos de eventos do PowerShell.