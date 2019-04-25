---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Selecionar partes de objetos selecionar objeto
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 323c57ba4462e20d9713fb74732989584f5a993f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057903"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="5c420-103">Selecionar partes de objetos (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="5c420-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="5c420-104">Pode utilizar o **Select-Object** cmdlet para criar objetos de Windows PowerShell novo, personalizados que contêm propriedades selecionadas os objetos que utilizou para criá-los.</span><span class="sxs-lookup"><span data-stu-id="5c420-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="5c420-105">Escreva o seguinte comando para criar um novo objeto, que inclui apenas as propriedades Name e FreeSpace da classe Win32_LogicalDisk WMI:</span><span class="sxs-lookup"><span data-stu-id="5c420-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="5c420-106">Não é possível ver o tipo de dados após a emissão do comando, mas se encaminhar o resultado para Get-Member depois de Select-Object, pode dizer que tem um novo tipo de objeto, um PSCustomObject:</span><span class="sxs-lookup"><span data-stu-id="5c420-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="5c420-107">Select-Object de várias formas.</span><span class="sxs-lookup"><span data-stu-id="5c420-107">Select-Object has many uses.</span></span> <span data-ttu-id="5c420-108">Um deles está a replicar os dados que, em seguida, pode modificar.</span><span class="sxs-lookup"><span data-stu-id="5c420-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="5c420-109">Agora podemos manipular o problema que ocorreu na secção anterior.</span><span class="sxs-lookup"><span data-stu-id="5c420-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="5c420-110">Podemos atualizar o valor de FreeSpace em nossos objetos recém-criados e o resultado incluirá a etiqueta descritiva:</span><span class="sxs-lookup"><span data-stu-id="5c420-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```