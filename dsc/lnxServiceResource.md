---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxService recursos
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267784"
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC para Linux nxService recursos

O **nxService** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir os serviços num nó de Linux.

## <a name="syntax"></a>Sintaxe

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Propriedades

| Propriedade | Descrição |
|---|---|
| Nome| O nome do serviço/daemon para configurar.|
| Controlador| O tipo de controlador de serviço a utilizar quando configurar o serviço.|
| Ativado| Indica se o serviço é iniciado no arranque.|
| Estado| Indica se o serviço está em execução. Defina esta propriedade a "Stopped" para se certificar de que o serviço não está em execução. Defini-lo como "Em execução" para se certificar de que o serviço não está em execução.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Informações Adicionais

O **nxService** recursos não criará uma definição de serviço ou um script para o serviço se não existir. Pode usar o do PowerShell Desired State Configuration **nxFile** recursos de recursos para gerir a existência ou o conteúdo do ficheiro de definição de serviço ou script.

## <a name="example"></a>Exemplo

O exemplo seguinte mostra a configuração do serviço "httpd" (para o Apache HTTP Server), registrada com o **SystemD** controlador de serviço.

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```