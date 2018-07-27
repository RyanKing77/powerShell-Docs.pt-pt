---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268583"
---
# <a name="reporting-on-jea"></a><span data-ttu-id="fb512-102">Criar Relatórios na JEA</span><span class="sxs-lookup"><span data-stu-id="fb512-102">Reporting on JEA</span></span>

<span data-ttu-id="fb512-103">Para relatar o estado da sua configuração de JEA, pode usar:</span><span class="sxs-lookup"><span data-stu-id="fb512-103">In order to report on the state of your JEA configuration, you can use:</span></span>

1. <span data-ttu-id="fb512-104">**Get-PSSessionConfiguration** devolver uma lista de todos os registado pontos de extremidade num determinado computador.</span><span class="sxs-lookup"><span data-stu-id="fb512-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2. <span data-ttu-id="fb512-105">**Get-PSSessionCapability** para gerar relatórios sobre as capacidades de qualquer usuário tem sobre um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="fb512-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="fb512-106">Eis um exemplo de **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="fb512-106">Here's an example of **Get-PSSessionCapability**:</span></span>

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

<span data-ttu-id="fb512-107">Para gerar relatórios sobre o _ações_ utilizadores demorou durante uma sessão JEA, pode:</span><span class="sxs-lookup"><span data-stu-id="fb512-107">To report on the _actions_ users took during a JEA session, you can:</span></span>

1. <span data-ttu-id="fb512-108">Ativar as transcrições de "over-the-the shoulder" para esse ponto final da JEA e consulte o diretório de transcrição para um registo completo das ações de cada utilizador</span><span class="sxs-lookup"><span data-stu-id="fb512-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="fb512-109">Ativar o registo de módulo do PowerShell e Inspecione os registos de eventos do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb512-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>