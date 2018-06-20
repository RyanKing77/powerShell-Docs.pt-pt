---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Ordenar Objetos
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 272d550a67b206f9924ebe143eca2f5906c0a304
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949983"
---
# <a name="sorting-objects"></a>Ordenar Objetos

Iremos pode organizar os dados apresentados para facilitar a análise utilizando o **Sort-Object** cmdlet. **Objeto de ordenação** utiliza o nome de um ou mais propriedades para ordenar e devolve dados ordenados pelos valores dessas propriedades.

Considere o problema de listagem Win32_SystemDriver instâncias. Se quisermos ordenar por **estado** e, em seguida, **nome**, iremos pode fazê-lo escrevendo:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Embora seja uma apresentação demorada, pode ver os itens com o mesmo Estado agrupado:

```output
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

Pode também ordenar os objetos na ordem inversa, especificando o **Descending** parâmetro. Isto Inverte a sequência de ordenação para que os nomes são ordenados por ordem alfabética inversa e os números são ordenados por descendente tamanho.

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```