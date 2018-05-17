---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxScript recursos
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC de Linux nxScript recursos

O **nxScript** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para executar scripts de Linux num nó de Linux.

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
| GetScript| Fornece um script que é executado quando invocar o [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet. O script tem de começar com uma shebang, tais como #! / bin/bash.|
| SetScript| Fornece um script. Quando invocar o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, a **TestScript** executa primeiro. Se o **TestScript** bloco devolve um código de saída diferente de 0, o **SetScript** bloco será executado. Se o **TestScript** devolve um código de saída de 0, o **SetScript** não será executado. O script tem de começar com uma shebang, tais como `#!/bin/bash`.|
| TestScript| Fornece um script. Quando invocar o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, este script é executado. Se devolver um código de saída diferente de 0, o SetScript será executado. Se devolver um código de saída 0, o **SetScript** não será executado. O **TestScript** também é executada quando invocar o [teste DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet. No entanto, neste caso, o **SetScript** não será executado, independentemente do é devolvido o código de saída do **TestScript**. O **TestScript** tem de devolver um código de saída 0 se a configuração real corresponde a configuração atual do estado pretendido e uma saída de código à 0 se não corresponde. (É a última configuração enacted no nó que está a utilizar o DSC da configuração atual do estado pretendido). O script tem de começar com uma shebang, tais como 1#!/bin/bash.1|
| Utilizador| O utilizador para executar o script como.|
| Grupo| O grupo para executar o script como.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

O exemplo seguinte demonstra a utilização do **nxScript** recursos para fazer a gestão de configuração adicionais.

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