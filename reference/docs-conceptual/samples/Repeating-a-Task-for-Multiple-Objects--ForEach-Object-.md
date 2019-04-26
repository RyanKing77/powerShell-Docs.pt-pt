---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Repetir uma tarefa para múltiplos objetos de ForEach de objetos
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086175"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Repetir uma tarefa para múltiplos objetos (ForEach-Object)

O **ForEach-Object** cmdlet utiliza blocos de script e o `$_` descritor do objeto de pipeline atual ao permitem-lhe executar um comando em cada objeto no pipeline. Isto pode ser utilizado para efetuar algumas tarefas complicadas.

Uma situação em que isso pode ser útil é manipulação de dados para torná-lo mais útil. Por exemplo, pode servir-se a classe Win32_LogicalDisk do WMI para retornar informações de espaço livre para cada disco local. Os dados são retornados em termos de bytes, no entanto, que torna difícil de ler:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Para podermos converter o valor de FreeSpace megabytes dividindo cada valor por 1024 duas vezes; após a divisão do primeiro, os dados estão em quilobytes e, após a segundo divisão é megabytes. Pode fazê-lo num bloco de script de ForEach-Object, digitando:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Infelizmente, o resultado é agora dados com nenhuma etiqueta associado. Como as propriedades WMI como este são só de leitura, não é possível converter diretamente FreeSpace. Se digitar isso:

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Obtém uma mensagem de erro:

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Pode reorganizar os dados através da utilização de algumas técnicas avançadas, mas uma abordagem mais simples é criar um novo objeto, utilizando **Select-Object**.