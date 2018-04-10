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
# <a name="reporting-on-jea"></a><span data-ttu-id="26be9-102">Criar Relatórios na JEA</span><span class="sxs-lookup"><span data-stu-id="26be9-102">Reporting on JEA</span></span>
<span data-ttu-id="26be9-103">Para gerar relatórios sobre o estado da configuração JEA, pode utilizar:</span><span class="sxs-lookup"><span data-stu-id="26be9-103">In order to report on the state of your JEA configuration, you can use:</span></span>
1.  <span data-ttu-id="26be9-104">**Get-PSSessionConfiguration** devolver uma lista de todos os registado pontos finais num computador especificado.</span><span class="sxs-lookup"><span data-stu-id="26be9-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2.  <span data-ttu-id="26be9-105">**Get-PSSessionCapability** para elaborar relatórios sobre as capacidades de qualquer utilizador especificado tem um ponto final específico.</span><span class="sxs-lookup"><span data-stu-id="26be9-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="26be9-106">Eis um exemplo de **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="26be9-106">Here’s an example of **Get-PSSessionCapability**:</span></span>
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

<span data-ttu-id="26be9-107">Para elaborar relatórios sobre o _ações_ utilizadores demorou durante uma sessão JEA, pode:</span><span class="sxs-lookup"><span data-stu-id="26be9-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="26be9-108">Ativar as transcrições "over-a-por cima ombro ficará" para esse ponto final JEA e consulte o diretório de transcript para um registo das ações de cada utilizador completo</span><span class="sxs-lookup"><span data-stu-id="26be9-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="26be9-109">Ativar o registo de módulo do PowerShell e Inspecione os registos de eventos do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26be9-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>