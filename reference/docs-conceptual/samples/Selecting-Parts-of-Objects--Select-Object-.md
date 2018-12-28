---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Selecionar partes de objetos selecionar objeto
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405557"
---
# <a name="selecting-parts-of-objects-select-object"></a>Selecionar partes de objetos (Select-Object)

Pode utilizar o **Select-Object** cmdlet para criar objetos de Windows PowerShell novo, personalizados que contêm propriedades selecionadas os objetos que utilizou para criá-los. Escreva o seguinte comando para criar um novo objeto, que inclui apenas as propriedades Name e FreeSpace da classe Win32_LogicalDisk WMI:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Não é possível ver o tipo de dados após a emissão do comando, mas se encaminhar o resultado para Get-Member depois de Select-Object, pode dizer que tem um novo tipo de objeto, um PSCustomObject:

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

Select-Object de várias formas. Um deles está a replicar os dados que, em seguida, pode modificar. Agora podemos manipular o problema que ocorreu na secção anterior. Podemos atualizar o valor de FreeSpace em nossos objetos recém-criados e o resultado incluirá a etiqueta descritiva:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```