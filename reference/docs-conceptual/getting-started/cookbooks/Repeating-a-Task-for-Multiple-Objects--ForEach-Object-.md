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
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Repetir uma tarefa para múltiplos objetos (ForEach-Object)

O **ForEach-Object** cmdlet utiliza blocos de script e o descritor de _ $ para o objeto de pipeline atual para permitem-lhe executar um comando em cada objeto no pipeline. Isto pode ser utilizado para efetuar algumas tarefas complicadas.

Uma situação em que isto pode ser útil é manipulação de dados para o tornar mais útil. Por exemplo, a classe de Win32_LogicalDisk do WMI pode ser utilizada para devolver informações de espaço livre para cada disco local. Os dados são devolvidos em termos de bytes, no entanto, que torna difícil de leitura:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Pode converter o valor de FreeSpace em megabytes, dividindo cada valor por 1024 duas vezes; após a divisão ter primeiro, os dados estão em quilobytes e, após a divisão segundo é megabytes. Pode fazê-lo num bloco de script ForEach-Object, escrevendo:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Infelizmente, o resultado é agora dados com nenhuma etiqueta associado. Porque as propriedades WMI como esta são só de leitura, não é possível converter diretamente FreeSpace. Se escrever este:

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Receber uma mensagem de erro:

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Pode reorganizar os dados utilizando algumas técnicas avançadas, mas uma abordagem mais simples consiste em criar um novo objeto, utilizando **Select-Object**.