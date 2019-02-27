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
# <a name="defining-default-member-sets-for-objects"></a>Defining Default Member Sets for Objects (Predefinir Conjuntos de Membros para Objetos)

O conjunto de membro de PSStandardMembers é utilizado pelo Windows PowerShell para definir os conjuntos de propriedade padrão para um objeto. Os conjuntos de propriedade padrão podem ser utilizados por comandos, como os cmdlets de formatação para exibir somente as propriedades que são definidas pela propriedade definida. Os conjuntos de propriedade padrão incluem DefaultDisplayProperty DefaultDisplayPropertySet e DefaultKeyPropertySet. Windows PowerShell ignora todos os outros conjuntos de membro e outros conjuntos de propriedade adicionados ao conjunto de membro PSStandardMembers.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Conjunto de membro para Diagnostics

No exemplo a seguir, o conjunto de membro PSStandardMembers define a propriedade de DefaultDisplayPropertySet definida para [Diagnostics](/dotnet/api/System.Diagnostics.Process) objetos. Este conjunto de propriedade é utilizado pelos [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.
No exemplo a seguir, o conjunto de membro PSStandardMembers define a propriedade de DefaultDisplayPropertySet definida para [Diagnostics](/dotnet/api/System.Diagnostics.Process) objetos. Este conjunto de propriedade é utilizado pelos [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.

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

O resultado seguinte mostra as propriedades padrão retornadas pela [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet. Apenas os `Id`, `Handles`, `CPU`, e `Name` propriedades são devolvidas para cada objeto de processo.
O resultado seguinte mostra as propriedades padrão retornadas pela [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet. Apenas os `Id`, `Handles`, `CPU`, e `Name` propriedades são devolvidas para cada objeto de processo.

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

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
