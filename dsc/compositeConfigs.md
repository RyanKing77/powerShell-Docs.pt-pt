---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Configurações de aninhamento
ms.openlocfilehash: 7ab58f3c59788be47312c460a626caa8a9922262
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="ca899-103">Aninhamento de configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="ca899-103">Nesting DSC configurations</span></span>

<span data-ttu-id="ca899-104">Uma configuração aninhada (também denominada configuração composta) é uma configuração que é chamada dentro de outra configuração, como se fosse um recurso.</span><span class="sxs-lookup"><span data-stu-id="ca899-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="ca899-105">Ambas as configurações tem de ser definidas no mesmo ficheiro.</span><span class="sxs-lookup"><span data-stu-id="ca899-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="ca899-106">Vamos ver um exemplo simples:</span><span class="sxs-lookup"><span data-stu-id="ca899-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="ca899-107">Neste exemplo, `FileConfig` demora dois parâmetros obrigatórios, **CopyFrom** e **CopyTo**, que são utilizados como valores para o **SourcePath** e  **DestinationPath** propriedades no `File` blocos de recursos.</span><span class="sxs-lookup"><span data-stu-id="ca899-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="ca899-108">O `NestedConfig` chamadas de configuração `FileConfig` como se fosse um recurso.</span><span class="sxs-lookup"><span data-stu-id="ca899-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="ca899-109">As propriedades no `NestedConfig` blocos de recursos (**CopyFrom** e **CopyTo**) são os parâmetros do `FileConfig` configuração.</span><span class="sxs-lookup"><span data-stu-id="ca899-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca899-110">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ca899-110">See Also</span></span>

- [<span data-ttu-id="ca899-111">Recursos compostos - através de uma configuração de DSC como um recurso</span><span class="sxs-lookup"><span data-stu-id="ca899-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)