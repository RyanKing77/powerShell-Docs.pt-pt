---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Selecionar partes de objetos selecione o objeto
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 8c9633e80f63e1d474c46fa772108aee4f79751d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="9915b-103">Selecionar partes de objetos (selecionar-objeto)</span><span class="sxs-lookup"><span data-stu-id="9915b-103">Selecting Parts of Objects (Select-Object)</span></span>
<span data-ttu-id="9915b-104">Pode utilizar o **Select-Object** cmdlet para criar novos e personalizados objetos do Windows PowerShell que contém as propriedades selecionadas os objetos que utilizar para criá-los.</span><span class="sxs-lookup"><span data-stu-id="9915b-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="9915b-105">Escreva o seguinte comando para criar um novo objeto que inclua apenas os nome e FreeSpace as propriedades da classe Win32_LogicalDisk WMI:</span><span class="sxs-lookup"><span data-stu-id="9915b-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="9915b-106">Não é possível ver o tipo de dados após a emissão esse comando, mas se encaminhar o resultado a Get-membro após Select-Object, pode indicar que tem um novo tipo de objeto, um PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="9915b-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="9915b-107">Select-Object tem várias utilizações.</span><span class="sxs-lookup"><span data-stu-id="9915b-107">Select-Object has many uses.</span></span> <span data-ttu-id="9915b-108">Uma delas está a replicar os dados que, em seguida, pode modificar.</span><span class="sxs-lookup"><span data-stu-id="9915b-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="9915b-109">Iremos agora pode processar o problema que executamos na secção anterior.</span><span class="sxs-lookup"><span data-stu-id="9915b-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="9915b-110">Iremos pode atualizar o valor de FreeSpace no nosso objetos criados recentemente e o resultado incluirá a etiqueta descritiva:</span><span class="sxs-lookup"><span data-stu-id="9915b-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```

