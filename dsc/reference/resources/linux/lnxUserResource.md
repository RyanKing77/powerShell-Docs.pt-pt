---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxUser recursos
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077658"
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC para Linux nxUser recursos

O **nxUser** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir utilizadores locais num nó de Linux.

## <a name="syntax"></a>Sintaxe

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriedades

|  Propriedade |  Indica o nome da conta para o qual pretende garantir um estado específico. |
|---|---|
| UserName| Especifica a localização onde pretende garantir que o estado para um ficheiro ou diretório.|
| Certifique-se| Especifica se a conta existe. Definir esta propriedade para "Presente" para se certificar de que a conta existe e defini-lo como "Ausente", certifique-se de que a conta não existe.|
| FullName| Uma cadeia que contém o nome completo para utilizar para a conta de utilizador.|
| Descrição| A descrição da conta de utilizador.|
| Palavra-passe| O hash da palavra-passe de utilizadores no formato adequado para o computador Linux. Normalmente, este é um SALT SHA-256, ou hash SHA-512. No Debian e Ubuntu Linux, este valor pode ser gerado com o comando mkpasswd. Para outras distribuições do Linux, o método crypt da biblioteca de Crypt do Python pode ser utilizado para gerar o hash.|
| Desativada| Indica se a conta está ativada. Defina esta propriedade como **$true** para se certificar de que esta conta está desativada e defini-lo como **$false** para se certificar de que está ativada.|
| PasswordChangeRequired| Indica se o utilizador pode alterar a palavra-passe. Defina esta propriedade como **$true** para se certificar de que o utilizador não é possível alterar a palavra-passe e defini-lo como **$false** para permitir que o utilizador altere a palavra-passe. O valor predefinido é **$false**. Esta propriedade é avaliada apenas se a conta de utilizador não existia anteriormente e está a ser criada.|
| HomeDirectory| O diretório de raiz para o utilizador.|
| GroupID| O ID de grupo principal para o utilizador.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID do bloco de script de configuração de recursos que pretende executar primeiro é "ResourceName" e seu tipo é "ResourceType", a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

O exemplo seguinte garante que o utilizador "monuser" existe e é um membro do grupo "DBusers".

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