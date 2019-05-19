---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Fluxo de Informações
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856386"
---
# <a name="information-stream"></a><span data-ttu-id="57d20-103">Fluxo de Informações</span><span class="sxs-lookup"><span data-stu-id="57d20-103">Information Stream</span></span>

<span data-ttu-id="57d20-104">PowerShell 5.0 adiciona um novo estruturado **informações** stream para transmitir dados estruturados entre um script e seu host.</span><span class="sxs-lookup"><span data-stu-id="57d20-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="57d20-105">`Write-Host` também foi atualizado para emitir sua saída para o **informações** stream, onde pode agora capturar ou silence-lo.</span><span class="sxs-lookup"><span data-stu-id="57d20-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="57d20-106">A nova `Write-Information` cmdlet utilizado com **InformationVariable** e **InformationAction** parâmetros comuns de permite mais flexibilidade e capacidade.</span><span class="sxs-lookup"><span data-stu-id="57d20-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="57d20-107">A função seguinte utiliza os cmdlets que tiram partido dos novos **informações** stream.</span><span class="sxs-lookup"><span data-stu-id="57d20-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

<span data-ttu-id="57d20-108">Os exemplos seguintes mostram os resultados da execução essa função.</span><span class="sxs-lookup"><span data-stu-id="57d20-108">The following examples show the results of running this function.</span></span>

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

<span data-ttu-id="57d20-109">O `$r` variável captura as informações do processo na variável script `$p`.</span><span class="sxs-lookup"><span data-stu-id="57d20-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="57d20-110">Ao contrário do `Write-Host` cmdlet, usando o **InformationVariable** parâmetro de `Write-Information` permite-lhe capturar a saída numa variável.</span><span class="sxs-lookup"><span data-stu-id="57d20-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="57d20-111">Utilizar o **Tag**, pode criar canais separados para a mensagem enviada para o **informações** stream.</span><span class="sxs-lookup"><span data-stu-id="57d20-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

<span data-ttu-id="57d20-112">Quando envia uma mensagem para o **informações** stream com uma etiqueta, essa mensagem não é apresentado no aplicativo host, mas pode ser obtido com o nome da etiqueta.</span><span class="sxs-lookup"><span data-stu-id="57d20-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="57d20-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="57d20-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```