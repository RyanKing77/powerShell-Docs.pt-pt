---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
description: Fornece um mecanismo para gerir grupos locais no nó de destino.
title: Recurso GroupSet de DSC
ms.openlocfilehash: afe4c4d33ac5620c411481e93d76a1f90c26deb9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077182"
---
# <a name="dsc-groupset-resource"></a>Recurso GroupSet de DSC

> Aplica-se a: Windows PowerShell 5.0

O **GroupSet** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir grupos locais no nó de destino. Este recurso é um [recursos compostos](../../../resources/authoringResourceComposite.md) que chama o [grupo de recursos](groupResource.md) para cada grupo especificado no `GroupName` parâmetro.

Utilize este recurso quando deseja adicionar e/ou remova a mesma lista de membros de mais de um grupo, remover mais de um grupo ou adicionar mais de um grupo com a mesma lista de membros.

## <a name="syntax"></a>Sintaxe

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| GroupName| Os nomes dos grupos para o qual pretende garantir um estado específico.|
| MembersToExclude| Use essa propriedade para remover membros da associação existente dos grupos. O valor desta propriedade é uma matriz de cadeias de caracteres do formulário *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilize o **membros** propriedade. Se o fizer, irá gerar um erro.|
| Credencial| As credenciais necessárias para aceder a recursos remotos. **Tenha em atenção**: Esta conta tem de ter as permissões adequadas do Active Directory para adicionar todas as contas de não-local para o grupo; caso contrário, ocorrerá um erro.
| Certifique-se| Indica se os grupos de existem. Defina esta propriedade para "Ausente", certifique-se de que os grupos não existem. Defini-la para "Apresentar" (o valor predefinido) garante que os grupos de existam.|
| Membros| Use essa propriedade para substituir a associação do grupo atual com os membros especificados. O valor desta propriedade é uma matriz de cadeias de caracteres do formulário *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilizar o **MembersToExclude** ou **MembersToInclude** propriedade. Se o fizer, irá gerar um erro.|
| MembersToInclude| Use essa propriedade para adicionar membros para a associação existente do grupo. O valor desta propriedade é uma matriz de cadeias de caracteres do formulário *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilize o **membros** propriedade. Se o fizer, irá gerar um erro.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é "DependsOn ="[ ResourceName ResourceType]"'.|

## <a name="example-1-ensuring-groups-are-present"></a>Exemplo 1: Grupos de garantir que estão presentes

O exemplo seguinte mostra como Certifique-se de que existem dois grupos, chamado "myGroup" e "myOtherGroup".

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> Este exemplo utiliza credenciais de texto sem formatação para manter a simplicidade. Para obter informações sobre como encriptar as credenciais no arquivo MOF de configuração, consulte [proteger o ficheiro MOF](../../../pull-server/secureMOF.md).
