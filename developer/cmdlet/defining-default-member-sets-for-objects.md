---
title: Definir define o membro predefinido de objetos | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: e8185eb7221a3be0445eddc537dbca89478c74f2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849470"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="a2c1c-102">Defining Default Member Sets for Objects (Predefinir Conjuntos de Membros para Objetos)</span><span class="sxs-lookup"><span data-stu-id="a2c1c-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="a2c1c-103">O conjunto de membro de PSStandardMembers é utilizado pelo Windows PowerShell para definir os conjuntos de propriedade padrão para um objeto.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="a2c1c-104">Os conjuntos de propriedade padrão podem ser utilizados por comandos, como os cmdlets de formatação para exibir somente as propriedades que são definidas pela propriedade definida.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="a2c1c-105">Os conjuntos de propriedade padrão incluem DefaultDisplayProperty DefaultDisplayPropertySet e DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="a2c1c-106">Windows PowerShell ignora todos os outros conjuntos de membro e outros conjuntos de propriedade adicionados ao conjunto de membro PSStandardMembers.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="a2c1c-107">Conjunto de membro para Diagnostics</span><span class="sxs-lookup"><span data-stu-id="a2c1c-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="a2c1c-108">No exemplo a seguir, o conjunto de membro PSStandardMembers define a propriedade de DefaultDisplayPropertySet definida para [Diagnostics](/dotnet/api/System.Diagnostics.Process) objetos.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="a2c1c-109">Este conjunto de propriedade é utilizado pelos [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>
<span data-ttu-id="a2c1c-110">No exemplo a seguir, o conjunto de membro PSStandardMembers define a propriedade de DefaultDisplayPropertySet definida para [Diagnostics](/dotnet/api/System.Diagnostics.Process) objetos.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-110">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="a2c1c-111">Este conjunto de propriedade é utilizado pelos [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-111">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

<span data-ttu-id="a2c1c-112">O resultado seguinte mostra as propriedades padrão retornadas pela [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-112">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="a2c1c-113">Apenas os `Id`, `Handles`, `CPU`, e `Name` propriedades são devolvidas para cada objeto de processo.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-113">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>
<span data-ttu-id="a2c1c-114">O resultado seguinte mostra as propriedades padrão retornadas pela [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-114">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="a2c1c-115">Apenas os `Id`, `Handles`, `CPU`, e `Name` propriedades são devolvidas para cada objeto de processo.</span><span class="sxs-lookup"><span data-stu-id="a2c1c-115">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a><span data-ttu-id="a2c1c-116">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a2c1c-116">See Also</span></span>

[<span data-ttu-id="a2c1c-117">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a2c1c-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
