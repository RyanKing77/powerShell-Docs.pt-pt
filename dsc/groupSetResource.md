---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
description: "Fornece um mecanismo para gerir grupos locais no nó de destino."
title: Recursos do DSC GroupSet
ms.openlocfilehash: 158cb28747c5fe1987eb62b2cc0f6d6f6fb14332
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-groupset-resource"></a>Recursos do DSC GroupSet

> Aplica-se a: Windows do Windows PowerShell 5.0

O **GroupSet** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir grupos locais no nó de destino. Este recurso se encontra um [recursos composto](authoringResourceComposite.md) que chama o [grupo recursos](groupResource.md) para cada grupo especificado no `GroupName` parâmetro.

Utilize este recurso quando se pretende adicionar e/ou remover a mesma lista de membros de mais de um grupo, remover mais do que um grupo ou adicione mais de um grupo com a mesma lista de membros.

##<a name="syntax"></a>Sintaxe # #
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
| GroupName| Os nomes dos grupos para os quais pretender certificar-se num estado específico.| 
| MembersToExclude| Utilize esta propriedade para remover membros da associação dos grupos. O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilize o **membros** propriedade. Se o fizer, irá gerar um erro.| 
| credencial| As credenciais necessárias para aceder a recursos remotos. **Tenha em atenção**: esta conta tem de ter as permissões adequadas do Active Directory para adicionar todas as contas não local ao grupo; caso contrário, ocorrerá um erro.
| Certifique-se| Indica se os grupos de existirem. Defina esta propriedade para "Ausente", certifique-se de que os grupos não existir. Defini-la para "Apresentar" (o valor predefinido) assegura que os grupos de existirem.| 
| Membros| Utilize esta propriedade para substituir a associação do grupo atual com os membros especificados. O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilizar o **MembersToExclude** ou **MembersToInclude** propriedade. Se o fizer, irá gerar um erro.| 
| MembersToInclude| Utilize esta propriedade para adicionar membros à associação do grupo existente. O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilize o **membros** propriedade. Se o fizer, irá gerar um erro.| 
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.| 

## <a name="example-1"></a>Exemplo 1

O exemplo seguinte mostra como Certifique-se de que existem dois grupos chamado "myGroup" e "myOtherGroup". 

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

>**Nota:** este exemplo utiliza credenciais de texto simples de simplicidade. Para obter informações sobre como encriptar as credenciais no ficheiro MOF configuração, consulte [proteger o ficheiro MOF](secureMOF.md).


