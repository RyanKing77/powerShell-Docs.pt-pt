---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxGroup recursos
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048786"
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC para Linux nxGroup recursos

O **nxGroup** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir grupos locais num nó de Linux.

## <a name="syntax"></a>Sintaxe

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade |  Descrição |
|---|---|
| GroupName| Especifica o nome do grupo para o qual pretende garantir um estado específico.|
| Certifique-se| Determina se deve verificar se o grupo existe. Defina esta propriedade para "Presente" para garantir que o grupo existe. Defini-lo como "Ausente", certifique-se de que o grupo não existe. O valor predefinido é "Presente".|
| Membros| Especifica os membros que formam o grupo.|
| MembersToInclude| Especifica os utilizadores que pretende garantir que são membros do grupo.|
| MembersToExclude| Especifica os utilizadores que pretende garantir que não são membros do grupo.|
| PreferredGroupID| Define o id de grupo para o valor fornecido se possível. Se o id de grupo está atualmente em utilização, é utilizado o seguinte id de grupo disponíveis.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Exemplo

O exemplo seguinte garante que o utilizador 'monuser' existe e é um membro do grupo 'DBusers'.

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```