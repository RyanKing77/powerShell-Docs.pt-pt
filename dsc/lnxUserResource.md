---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxUser recursos
ms.openlocfilehash: 222bd2191cf5c5f0a90ba947275ffde47d22ec86
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC de Linux nxUser recursos

O **nxUser** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir utilizadores locais num nó de Linux.

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

|  Propriedade |  Indica o nome de conta para o qual pretende garantir um estado específico. |
|---|---|
| UserName| Especifica a localização onde pretende garantir o estado de um ficheiro ou diretório.|
| Certifique-se| Especifica se a conta existe. Definir esta propriedade para "Presente" para garantir que a conta existe e defina-o para "Ausente", certifique-se de que a conta não existe.|
| FullName| Uma cadeia que contém o nome completo a utilizar para a conta de utilizador.|
| Descrição| A descrição da conta de utilizador.|
| Palavra-passe| O hash da palavra-passe de utilizadores no formato adequado para o computador Linux. Normalmente, trata-se um salted SHA-256, ou um hash SHA-512. Debian e Ubuntu Linux, este valor pode ser gerado com o comando mkpasswd. Para outros distros Linux, o método de crypt da biblioteca de Crypt do Python pode ser utilizado para gerar o hash.|
| Desativado| Indica se a conta está ativada. Defina esta propriedade como **$true** para se certificar de que esta conta está desativada e defina-o como **$false** para se certificar de que está ativada.|
| PasswordChangeRequired| Indica se o utilizador pode alterar a palavra-passe. Defina esta propriedade como **$true** para se certificar de que o utilizador não é possível alterar a palavra-passe e defina-o como **$false** para permitir ao utilizador alterar a palavra-passe. O valor predefinido é **$false**. Esta propriedade é avaliada apenas se a conta de utilizador não existia anteriormente e está a ser criada.|
| HomeDirectory| O diretório de raiz para o utilizador.|
| GroupID| O ID do grupo principal para o utilizador.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID do bloco de script de configuração de recursos que pretende executar primeiro é "ResourceName" e o respetivo tipo é "ResourceType", a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

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