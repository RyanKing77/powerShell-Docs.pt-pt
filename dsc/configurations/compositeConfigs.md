---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Configurações de aninhamento
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080242"
---
# <a name="nesting-dsc-configurations"></a>Configurações de DSC de aninhamento

Uma configuração aninhada (também chamada de configuração composta) é uma configuração que é chamada dentro de outra configuração, como se fosse um recurso.
Ambas as configurações devem ser definidas no mesmo ficheiro.

Vejamos um exemplo simples:

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

Neste exemplo, `FileConfig` usa dois parâmetros obrigatórios, **CopyFrom** e **CopyTo**, que é utilizado como valores para o **SourcePath** e  **DestinationPath** propriedades no `File` bloco de recursos.
O `NestedConfig` chamadas de configuração `FileConfig` como se fosse um recurso.
As propriedades a `NestedConfig` bloco de recursos (**CopyFrom** e **CopyTo**) são os parâmetros do `FileConfig` configuração.

## <a name="see-also"></a>Veja Também

- [Recursos compostos – usando uma configuração de DSC como um recurso](../resources/authoringResourceComposite.md)