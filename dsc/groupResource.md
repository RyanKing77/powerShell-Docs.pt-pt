---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recurso do grupo de DSC
ms.openlocfilehash: 8a2087455a72ec1f368f890b62228b31cf4ec95a
ms.sourcegitcommit: c72c76f6ed77b3e6f26fef3e8784b157bfc19355
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/06/2018
---
# <a name="dsc-group-resource"></a>Recurso do grupo de DSC

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso do grupo no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir grupos locais no nó de destino.

## <a name="syntax"></a>Sintaxe

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| GroupName| O nome do grupo para o qual pretende garantir um estado específico.|
| credencial| As credenciais necessárias para aceder a recursos remotos. **Tenha em atenção**: esta conta tem de ter as permissões adequadas do Active Directory para adicionar todas as contas não local ao grupo; caso contrário, ocorrerá um erro quando a configuração é executada no nó de destino.
| Descrição| A descrição do grupo.|
| Certifique-se| Indica se o grupo existe. Defina esta propriedade para "Ausente", certifique-se de que o grupo não existe. Defini-la para "Apresentar" (o valor predefinido) assegura que o grupo existe.|
| Membros| Utilize esta propriedade para substituir a associação do grupo atual com os membros especificados. O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilizar o **MembersToExclude** ou **MembersToInclude** propriedade. Se o fizer, gera um erro.|
| MembersToExclude| Utilize esta propriedade para remover membros da associação do grupo. O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilize o **membros** propriedade. Se o fizer, gera um erro.|
| MembersToInclude| Utilize esta propriedade para adicionar membros à associação do grupo existente. O valor desta propriedade é uma matriz de cadeias de formato *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilize o **membros** propriedade. Se o fizer, irá gerar um erro.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.|

## <a name="example-1"></a>Exemplo 1

O exemplo seguinte mostra como Certifique-se de que um grupo denominado "TestGroup" está ausente.

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a>Exemplo 2

O exemplo seguinte mostra como adicionar um utilizador do Active Directory para o grupo de administradores locais como parte de uma compilação de laboratório multi máquina em que já estiver a utilizar um PSCredential para a conta de administrador Local.
Como também é utilizado para a conta de administrador de domínio (após a promoção de domínio), em seguida, é necessário converter este PSCredential existente para uma credencial de domínio amigável.
Em seguida, iremos pode adicionar um utilizador de domínio para o grupo de administradores Local no servidor membro.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a>Exemplo 3

O exemplo seguinte mostra como garantir que um grupo local, TigerTeamAdmins, no servidor TigerTeamSource.Contoso.Com não contém uma conta de domínio específico, Contoso\JerryG.

```powershell
Configuration SecureTigerTeamSrouce {
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

  Node TigerTeamSource.Contoso.Com {
    Group TigerTeamAdmins {
       GroupName        = 'TigerTeamAdmins'
       Ensure           = 'Present'
       MembersToExclude = "Contoso\JerryG"
    }
  }
}
```
