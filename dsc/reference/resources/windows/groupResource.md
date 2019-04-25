---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso do grupo de DSC
ms.openlocfilehash: 123e09b54a923af942a15f80fa7291c555b4235f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077352"
---
# <a name="dsc-group-resource"></a>Recurso do grupo de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso de grupo no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir grupos locais no nó de destino.

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
| Credencial| As credenciais necessárias para aceder a recursos remotos. **Tenha em atenção**: Esta conta tem de ter as permissões adequadas do Active Directory para adicionar todas as contas de não-local para o grupo; caso contrário, ocorrerá um erro quando a configuração é executada no nó de destino.
| Descrição| A descrição do grupo.|
| Certifique-se| Indica se o grupo existe. Defina esta propriedade como "Ausente", certifique-se de que o grupo não existe. Defini-la para "Apresentar" (o valor predefinido) garante que o grupo existe.|
| Membros| Use essa propriedade para substituir a associação do grupo atual com os membros especificados. O valor desta propriedade é uma matriz de cadeias de caracteres do formulário *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilizar o **MembersToExclude** ou **MembersToInclude** propriedade. Isso gera um erro.|
| MembersToExclude| Use essa propriedade para remover membros da associação existente do grupo. O valor desta propriedade é uma matriz de cadeias de caracteres do formulário *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilize o **membros** propriedade. Isso gera um erro.|
| MembersToInclude| Use essa propriedade para adicionar membros para a associação existente do grupo. O valor desta propriedade é uma matriz de cadeias de caracteres do formulário *domínio*\\*UserName*. Se definir esta propriedade numa configuração, não utilize o **membros** propriedade. Se o fizer, irá gerar um erro.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é "DependsOn ="[ ResourceName ResourceType]"'.|

## <a name="example-1"></a>Exemplo 1

O exemplo seguinte mostra como Certifique-se de que um grupo chamado "Grupoteste" está ausente.

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

O exemplo seguinte mostra como adicionar um utilizador do Active Directory para o grupo de administradores locais como parte de uma compilação de laboratório de máquina multi onde já estiver a utilizar uma PSCredential para a conta de administrador Local.
Como também é utilizado para a conta de administrador de domínio (após a promoção de domínio), em seguida, precisamos converter este PSCredential existente para uma credencial de domínio amigável.
Em seguida, podemos adicionar um utilizador de domínio para o grupo de administradores Local no servidor membro.

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
Configuration SecureTigerTeamSource {
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