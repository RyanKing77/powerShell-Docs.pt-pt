---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Selecionar partes de objetos selecione o objeto
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="selecting-parts-of-objects-select-object"></a>Selecionar partes de objetos (selecionar-objeto)

Pode utilizar o **Select-Object** cmdlet para criar novos e personalizados objetos do Windows PowerShell que contém as propriedades selecionadas os objetos que utilizar para criá-los. Escreva o seguinte comando para criar um novo objeto que inclua apenas os nome e FreeSpace as propriedades da classe Win32_LogicalDisk WMI:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Não é possível ver o tipo de dados após a emissão esse comando, mas se encaminhar o resultado a Get-membro após Select-Object, pode indicar que tem um novo tipo de objeto, um PSCustomObject:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

Select-Object tem várias utilizações. Uma delas está a replicar os dados que, em seguida, pode modificar. Iremos agora pode processar o problema que executamos na secção anterior. Iremos pode atualizar o valor de FreeSpace no nosso objetos criados recentemente e o resultado incluirá a etiqueta descritiva:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```