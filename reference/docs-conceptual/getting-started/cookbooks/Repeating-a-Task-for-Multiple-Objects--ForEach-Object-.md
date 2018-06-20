---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Repetir uma tarefa para o objeto de ForEach múltiplos objetos
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 8b8002af3ade0905421760ce29cdc84b084236e9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954284"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="4add4-103">Repetir uma tarefa para múltiplos objetos (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="4add4-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="4add4-104">O **ForEach-Object** cmdlet utiliza blocos de script e o descritor de _ $ para o objeto de pipeline atual para permitem-lhe executar um comando em cada objeto no pipeline.</span><span class="sxs-lookup"><span data-stu-id="4add4-104">The **ForEach-Object** cmdlet uses script blocks and the $_ descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="4add4-105">Isto pode ser utilizado para efetuar algumas tarefas complicadas.</span><span class="sxs-lookup"><span data-stu-id="4add4-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="4add4-106">Uma situação em que isto pode ser útil é manipulação de dados para o tornar mais útil.</span><span class="sxs-lookup"><span data-stu-id="4add4-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="4add4-107">Por exemplo, a classe de Win32_LogicalDisk do WMI pode ser utilizada para devolver informações de espaço livre para cada disco local.</span><span class="sxs-lookup"><span data-stu-id="4add4-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="4add4-108">Os dados são devolvidos em termos de bytes, no entanto, que torna difícil de leitura:</span><span class="sxs-lookup"><span data-stu-id="4add4-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="4add4-109">Pode converter o valor de FreeSpace em megabytes, dividindo cada valor por 1024 duas vezes; após a divisão ter primeiro, os dados estão em quilobytes e, após a divisão segundo é megabytes.</span><span class="sxs-lookup"><span data-stu-id="4add4-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="4add4-110">Pode fazê-lo num bloco de script ForEach-Object, escrevendo:</span><span class="sxs-lookup"><span data-stu-id="4add4-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="4add4-111">Infelizmente, o resultado é agora dados com nenhuma etiqueta associado.</span><span class="sxs-lookup"><span data-stu-id="4add4-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="4add4-112">Porque as propriedades WMI como esta são só de leitura, não é possível converter diretamente FreeSpace.</span><span class="sxs-lookup"><span data-stu-id="4add4-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="4add4-113">Se escrever este:</span><span class="sxs-lookup"><span data-stu-id="4add4-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="4add4-114">Receber uma mensagem de erro:</span><span class="sxs-lookup"><span data-stu-id="4add4-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="4add4-115">Pode reorganizar os dados utilizando algumas técnicas avançadas, mas uma abordagem mais simples consiste em criar um novo objeto, utilizando **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="4add4-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>