---
ms.date: 06/12/2017
keywords: DSC, PowerShell, configuração, instalação
title: Recurso de nxScript do DSC para Linux
ms.openlocfilehash: 0ad0530f1de7b86ff48c4eb1f79870f6682894a1
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372158"
---
# <a name="dsc-for-linux-nxscript-resource"></a>Recurso de nxScript do DSC para Linux

O recurso **nxScript** na configuração de estado desejado (DSC) do PowerShell fornece um mecanismo para executar scripts do Linux em um nó do Linux.

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
| GetScript| Fornece um script para retornar o status atual do computador.  Esse script é executado quando você invoca o script [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) . O script deve começar com um shebang, como #!/bin/bash.|
| SetScript| Fornece um script que coloca o computador no estado correto. Quando você invoca o script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) , o **TestScript** é executado primeiro. Se o bloco **TestScript** retornar um código de saída diferente de 0, o bloco setscript será executado. Se o **TestScript** retornar um código de saída de 0,  o setscript não será executado. O script deve começar com um shebang, `#!/bin/bash`como.|
| TestScript| Fornece um script que avalia se o nó está atualmente no estado correto. Quando você invoca o script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) , esse script é executado. Se ele retornar um código de saída diferente de 0, o setscript será executado. Se ele retornar um código de saída de 0,  o setscript não será executado. O **TestScript** também é executado quando você invoca o script [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) . No entanto, nesse caso,  o setscript não será executado, independentemente do código de saída retornado do **TestScript**. O **TestScript** deve conter conteúdo e deve retornar um código de saída de 0 se a configuração real corresponder à configuração de estado atual desejado e um código de saída diferente de 0 se não corresponder. (A configuração de estado atual desejada é a última configuração aplicada no nó que está usando a DSC). O script deve começar com um shebang, como 1 #!/bin/bash.1|
| Utilizador| O usuário para executar o script como.|
| Grupo| O grupo para o qual executar o script.|
| DependsOn | Indica que a configuração de outro recurso deve ser executada antes que este recurso seja configurado. Por exemplo, se a **ID** do bloco de script de configuração de recurso que você deseja executar primeiro  for resourceName e seu tipo for **ResourceType**, a sintaxe para usar `DependsOn = "[ResourceType]ResourceName"`essa propriedade será.|

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra o uso do recurso **nxScript** para executar o gerenciamento de configuração adicional.

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
