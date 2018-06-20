---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Configurações de aninhamento
ms.openlocfilehash: 7ab58f3c59788be47312c460a626caa8a9922262
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218999"
---
# <a name="nesting-dsc-configurations"></a>Aninhamento de configurações de DSC

Uma configuração aninhada (também denominada configuração composta) é uma configuração que é chamada dentro de outra configuração, como se fosse um recurso.
Ambas as configurações tem de ser definidas no mesmo ficheiro.

Vamos ver um exemplo simples:

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }

}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

Neste exemplo, `FileConfig` demora dois parâmetros obrigatórios, **CopyFrom** e **CopyTo**, que são utilizados como valores para o **SourcePath** e  **DestinationPath** propriedades no `File` blocos de recursos.
O `NestedConfig` chamadas de configuração `FileConfig` como se fosse um recurso.
As propriedades no `NestedConfig` blocos de recursos (**CopyFrom** e **CopyTo**) são os parâmetros do `FileConfig` configuração.

## <a name="see-also"></a>Consulte Também

- [Recursos compostos - através de uma configuração de DSC como um recurso](authoringResourceComposite.md)