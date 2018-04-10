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
---
# <a name="sorting-objects"></a><span data-ttu-id="f1082-103">Ordenar Objetos</span><span class="sxs-lookup"><span data-stu-id="f1082-103">Sorting Objects</span></span>

<span data-ttu-id="f1082-104">Iremos pode organizar os dados apresentados para facilitar a análise utilizando o **Sort-Object** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1082-104">We can organize displayed data to make it easier to scan by using the **Sort-Object** cmdlet.</span></span> <span data-ttu-id="f1082-105">**Objeto de ordenação** utiliza o nome de um ou mais propriedades para ordenar e devolve dados ordenados pelos valores dessas propriedades.</span><span class="sxs-lookup"><span data-stu-id="f1082-105">**Sort-Object** takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

<span data-ttu-id="f1082-106">Considere o problema de listagem Win32_SystemDriver instâncias.</span><span class="sxs-lookup"><span data-stu-id="f1082-106">Consider the problem of listing Win32_SystemDriver instances.</span></span> <span data-ttu-id="f1082-107">Se quisermos ordenar por **estado** e, em seguida, **nome**, iremos pode fazê-lo escrevendo:</span><span class="sxs-lookup"><span data-stu-id="f1082-107">If we want to sort by **State** and then by **Name**, we can do it by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

<span data-ttu-id="f1082-108">Embora seja uma apresentação demorada, pode ver os itens com o mesmo Estado agrupado:</span><span class="sxs-lookup"><span data-stu-id="f1082-108">Although this is a lengthy display, you can see items with the same state grouped together:</span></span>

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

<span data-ttu-id="f1082-109">Pode também ordenar os objetos na ordem inversa, especificando o **Descending** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f1082-109">You can also sort the objects in reverse order by specifying the **Descending** parameter.</span></span> <span data-ttu-id="f1082-110">Isto Inverte a sequência de ordenação para que os nomes são ordenados por ordem alfabética inversa e os números são ordenados por descendente tamanho.</span><span class="sxs-lookup"><span data-stu-id="f1082-110">This reverses the sort order so that names are sorted in reverse alphabetical order and numbers are sorted by descending size.</span></span>

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