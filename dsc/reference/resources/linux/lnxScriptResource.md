---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxScript recursos
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077828"
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC para Linux nxScript recursos

O **nxScript** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para executar scripts do Linux num nó de Linux.

## <a name="syntax"></a>Sintaxe

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriedades

|  Propriedade |  Descrição |
|---|---|
| GetScript| Fornece um script que é executado quando invoca o [Get-dscconfiguration para](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet. O script tem de começar com um shebang, tais como #! / bin/bash.|
| SetScript| Fornece um script. Quando invoca o [Start-dscconfiguration para](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, o **TestScript** é executado primeiro. Se o **TestScript** bloco devolve um código de saída diferente de 0, o **SetScript** bloco será executado. Se o **TestScript** devolve um código de saída 0, o **SetScript** não será executado. O script tem de começar com um shebang, tais como `#!/bin/bash`.|
| TestScript| Fornece um script. Quando invoca o [Start-dscconfiguration para](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, este script é executado. Se ela retornar um código de saída diferente de 0, o SetScript será executado. Se ele retorna um código de saída 0, o **SetScript** não será executado. O **TestScript** também é executada quando invoca o [Test-dscconfiguration para](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet. No entanto, no caso, o **SetScript** não será executado, não importa qual código de saída é retornado do **TestScript**. O **TestScript** tem de devolver um código de saída 0 se a configuração real corresponde a configuração atual do estado pretendido e uma saída de código que 0 se não corresponde. (A configuração atual do estado pretendido é a última configuração elaborada no nó que está a utilizar o DSC). O script tem de começar com um shebang, tais como 1#!/bin/bash.1|
| Utilizador| O utilizador para executar o script como.|
| Grupo| O grupo para executar o script como.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

O exemplo seguinte demonstra o uso do **nxScript** recursos para executar o gerenciamento de configuração adicionais.

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```