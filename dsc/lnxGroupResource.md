---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxGroup recursos
ms.openlocfilehash: 750b7c38a38fb8a7781585a3a7776f832ee62495
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC de Linux nxGroup recursos

O **nxGroup** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir grupos locais num nó de Linux.

## <a name="syntax"></a>Sintaxe

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a>Propriedades

|  Propriedade |  Descrição |
|---|---|
| GroupName| Especifica o nome do grupo para o qual pretende garantir um estado específico.|
| Certifique-se| Determina se deve verificar se o grupo existe. Defina esta propriedade para "Presente" para garantir que o grupo existe. Defina-o para "Ausente", certifique-se de que o grupo não existe. O valor predefinido é "Presente".|
| Membros| Especifica os membros que formam o grupo.|
| MembersToInclude| Especifica os utilizadores que pretende para se certificar de que são membros do grupo.|
| MembersToExclude| Especifica os utilizadores que pretende para se certificar de que não são membros do grupo.|
| PreferredGroupID| Define o id de grupo para o valor fornecido se possível. Se o id de grupo está a ser utilizada, o seguinte id de grupo disponível é utilizado.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

O exemplo seguinte assegura que o utilizador "monuser" existe e se é um membro do grupo "DBusers".

```
Import-DSCResource -Module nx

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```