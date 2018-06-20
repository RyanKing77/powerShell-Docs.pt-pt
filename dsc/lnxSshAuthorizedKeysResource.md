---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxSshAuthorizedKeys recursos
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222042"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC de Linux nxSshAuthorizedKeys recursos

O **nxAuthorizedKeys** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir autorizado ssh chaves para um utilizador especificado.

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
| KeyComment| Um comentário exclusivo para a chave. Isto é utilizado para identificar exclusivamente chaves.|
| Certifique-se| Especifica se a chave está definida. Defina esta propriedade para "Ausente", certifique-se de que a chave não existe no ficheiro de chaves autorizados do utilizador. Defina-o para "Presente" para garantir que a chave está definida no ficheiro de chave autorizados do utilizador.|
| Nome de utilizador| O nome de utilizador para gerir ssh autorizado chaves para. Se não definido, o utilizador predefinido é de "raiz".|
| Tecla| O conteúdo da chave. Isto é necessário se **Certifique-se** está definido como "Apresente".|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

O exemplo seguinte define um público ssh autorizado chave para o utilizador "monuser".

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