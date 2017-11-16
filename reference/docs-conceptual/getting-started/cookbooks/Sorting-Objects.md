---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "A ordenação de objetos"
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 2df45c64656e74dc8b72957ce59f2a5e5ee663b6
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="sorting-objects"></a><span data-ttu-id="25437-103">A ordenação de objetos</span><span class="sxs-lookup"><span data-stu-id="25437-103">Sorting Objects</span></span>
<span data-ttu-id="25437-104">Iremos pode organizar os dados apresentados para facilitar a análise utilizando o **Sort-Object** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="25437-104">We can organize displayed data to make it easier to scan by using the **Sort-Object** cmdlet.</span></span> <span data-ttu-id="25437-105">**Objeto de ordenação** utiliza o nome de um ou mais propriedades para ordenar e devolve dados ordenados pelos valores dessas propriedades.</span><span class="sxs-lookup"><span data-stu-id="25437-105">**Sort-Object** takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

<span data-ttu-id="25437-106">Considere o problema de listagem Win32_SystemDriver instâncias.</span><span class="sxs-lookup"><span data-stu-id="25437-106">Consider the problem of listing Win32_SystemDriver instances.</span></span> <span data-ttu-id="25437-107">Se quisermos ordenar por **estado** e, em seguida, **nome**, iremos pode fazê-lo escrevendo:</span><span class="sxs-lookup"><span data-stu-id="25437-107">If we want to sort by **State** and then by **Name**, we can do it by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

<span data-ttu-id="25437-108">Embora seja uma apresentação demorada, pode ver os itens com o mesmo Estado agrupado:</span><span class="sxs-lookup"><span data-stu-id="25437-108">Although this is a lengthy display, you can see items with the same state grouped together:</span></span>

```
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

<span data-ttu-id="25437-109">Pode também ordenar os objetos na ordem inversa, especificando o **Descending** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="25437-109">You can also sort the objects in reverse order by specifying the **Descending** parameter.</span></span> <span data-ttu-id="25437-110">Isto Inverte a sequência de ordenação para que os nomes são ordenados por ordem alfabética inversa e os números são ordenados por descendente tamanho.</span><span class="sxs-lookup"><span data-stu-id="25437-110">This reverses the sort order so that names are sorted in reverse alphabetical order and numbers are sorted by descending size.</span></span>

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

