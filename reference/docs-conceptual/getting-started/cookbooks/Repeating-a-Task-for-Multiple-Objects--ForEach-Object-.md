---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Repetir uma tarefa para múltiplos objetos de ForEach de objetos
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587266"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="12b83-103">Repetir uma tarefa para múltiplos objetos (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="12b83-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="12b83-104">O **ForEach-Object** cmdlet utiliza blocos de script e o `$_` descritor do objeto de pipeline atual ao permitem-lhe executar um comando em cada objeto no pipeline.</span><span class="sxs-lookup"><span data-stu-id="12b83-104">The **ForEach-Object** cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="12b83-105">Isto pode ser utilizado para efetuar algumas tarefas complicadas.</span><span class="sxs-lookup"><span data-stu-id="12b83-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="12b83-106">Uma situação em que isso pode ser útil é manipulação de dados para torná-lo mais útil.</span><span class="sxs-lookup"><span data-stu-id="12b83-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="12b83-107">Por exemplo, pode servir-se a classe Win32_LogicalDisk do WMI para retornar informações de espaço livre para cada disco local.</span><span class="sxs-lookup"><span data-stu-id="12b83-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="12b83-108">Os dados são retornados em termos de bytes, no entanto, que torna difícil de ler:</span><span class="sxs-lookup"><span data-stu-id="12b83-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="12b83-109">Para podermos converter o valor de FreeSpace megabytes dividindo cada valor por 1024 duas vezes; após a divisão do primeiro, os dados estão em quilobytes e, após a segundo divisão é megabytes.</span><span class="sxs-lookup"><span data-stu-id="12b83-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="12b83-110">Pode fazê-lo num bloco de script de ForEach-Object, digitando:</span><span class="sxs-lookup"><span data-stu-id="12b83-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="12b83-111">Infelizmente, o resultado é agora dados com nenhuma etiqueta associado.</span><span class="sxs-lookup"><span data-stu-id="12b83-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="12b83-112">Como as propriedades WMI como este são só de leitura, não é possível converter diretamente FreeSpace.</span><span class="sxs-lookup"><span data-stu-id="12b83-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="12b83-113">Se digitar isso:</span><span class="sxs-lookup"><span data-stu-id="12b83-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="12b83-114">Obtém uma mensagem de erro:</span><span class="sxs-lookup"><span data-stu-id="12b83-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="12b83-115">Pode reorganizar os dados através da utilização de algumas técnicas avançadas, mas uma abordagem mais simples é criar um novo objeto, utilizando **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="12b83-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>