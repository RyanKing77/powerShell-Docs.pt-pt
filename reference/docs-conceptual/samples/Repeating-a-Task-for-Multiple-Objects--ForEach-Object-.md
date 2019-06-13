---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Repetir uma tarefa para múltiplos objetos de ForEach de objetos
ms.openlocfilehash: 1442507c4213476f65df3401c1021f8d0fc31956
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030810"
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
