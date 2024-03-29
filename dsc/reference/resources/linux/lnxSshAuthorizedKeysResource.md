---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxSshAuthorizedKeys recursos
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077709"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC para Linux nxSshAuthorizedKeys recursos

O **nxAuthorizedKeys** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir autorizado ssh chaves para um utilizador especificado.

## <a name="syntax"></a>Sintaxe

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriedades

|  Propriedade |  Descrição |
|---|---|
| KeyComment| Um comentário exclusivo para a chave. Isto é utilizado para identificar exclusivamente as chaves.|
| Certifique-se| Especifica se a chave está definida. Defina esta propriedade para "Ausente", certifique-se de que a chave não existir no ficheiro de chaves autorizado do utilizador. Defini-lo como "Presente" para garantir que a chave é definida no ficheiro de chave autorizados do utilizador.|
| Nome de utilizador| O nome de utilizador para gerir ssh autorizado chaves para. Se não definido, o utilizador predefinido é "raiz".|
| Tecla| O conteúdo da chave. Isto é necessário se **Certifique-se** está definido como "Presente".|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

O exemplo seguinte define uma pública ssh autorizada chave para o utilizador "monuser".

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```