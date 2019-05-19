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
# <a name="information-stream"></a>Fluxo de Informações

PowerShell 5.0 adiciona um novo estruturado **informações** stream para transmitir dados estruturados entre um script e seu host. `Write-Host` também foi atualizado para emitir sua saída para o **informações** stream, onde pode agora capturar ou silence-lo. A nova `Write-Information` cmdlet utilizado com **InformationVariable** e **InformationAction** parâmetros comuns de permite mais flexibilidade e capacidade.

A função seguinte utiliza os cmdlets que tiram partido dos novos **informações** stream.

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

Os exemplos seguintes mostram os resultados da execução essa função.

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

O `$r` variável captura as informações do processo na variável script `$p`.

```powershell
$r.Id
4008
```

Ao contrário do `Write-Host` cmdlet, usando o **InformationVariable** parâmetro de `Write-Information` permite-lhe capturar a saída numa variável. Utilizar o **Tag**, pode criar canais separados para a mensagem enviada para o **informações** stream.

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

Quando envia uma mensagem para o **informações** stream com uma etiqueta, essa mensagem não é apresentado no aplicativo host, mas pode ser obtido com o nome da etiqueta. Por exemplo:

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```