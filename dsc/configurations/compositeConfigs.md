---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Configurações de aninhamento
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404743"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="774ca-103">Configurações de DSC de aninhamento</span><span class="sxs-lookup"><span data-stu-id="774ca-103">Nesting DSC configurations</span></span>

<span data-ttu-id="774ca-104">Uma configuração aninhada (também chamada de configuração composta) é uma configuração que é chamada dentro de outra configuração, como se fosse um recurso.</span><span class="sxs-lookup"><span data-stu-id="774ca-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="774ca-105">Ambas as configurações devem ser definidas no mesmo ficheiro.</span><span class="sxs-lookup"><span data-stu-id="774ca-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="774ca-106">Vejamos um exemplo simples:</span><span class="sxs-lookup"><span data-stu-id="774ca-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="774ca-107">Neste exemplo, `FileConfig` usa dois parâmetros obrigatórios, **CopyFrom** e **CopyTo**, que é utilizado como valores para o **SourcePath** e  **DestinationPath** propriedades no `File` bloco de recursos.</span><span class="sxs-lookup"><span data-stu-id="774ca-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="774ca-108">O `NestedConfig` chamadas de configuração `FileConfig` como se fosse um recurso.</span><span class="sxs-lookup"><span data-stu-id="774ca-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="774ca-109">As propriedades a `NestedConfig` bloco de recursos (**CopyFrom** e **CopyTo**) são os parâmetros do `FileConfig` configuração.</span><span class="sxs-lookup"><span data-stu-id="774ca-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="774ca-110">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="774ca-110">See Also</span></span>

- [<span data-ttu-id="774ca-111">Recursos compostos – usando uma configuração de DSC como um recurso</span><span class="sxs-lookup"><span data-stu-id="774ca-111">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)