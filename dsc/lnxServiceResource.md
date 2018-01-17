---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: DSC de Linux nxService recursos
ms.openlocfilehash: 4273ad59f15eedd08b07888ebb6ee51d039b72b3
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC de Linux nxService recursos

O **nxService** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir serviços num nó de Linux.

## <a name="syntax"></a>Sintaxe

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriedades
|  Propriedade |  Descrição | 
|---|---|
| Nome| O nome do serviço daemon para configurar.| 
| Controlador| O tipo de controlador de serviço para utilizar quando configurar o serviço.| 
| Ativado| Indica se o serviço for iniciado no arranque.| 
| Estado| Indica se o serviço está em execução. Defina esta propriedade para "Stopped" para se certificar de que o serviço não está em execução. Defina-o para "Em execução" para se certificar de que o serviço não está em execução.| 
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.| 


## <a name="additional-information"></a>Informações Adicionais

O **nxService** recursos não irão criar uma definição de serviço ou script para o serviço se não existir. Pode utilizar a configuração de estado pretendido do PowerShell **nxFile** recursos de recursos para gerir a existência de ou o conteúdo do ficheiro de definição de serviço ou script.

## <a name="example"></a>Exemplo

O exemplo seguinte mostra a configuração do serviço "httpd" (para Apache HTTP Server), registada com o **SystemD** controlador do serviço.

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```

