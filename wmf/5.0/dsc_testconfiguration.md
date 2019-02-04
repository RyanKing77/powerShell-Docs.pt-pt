---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4008a7f91af41150f26c4147135b30aa8835281c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688561"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="c8824-102">Suporta o cmdlet Test-dscconfiguration para configurações de referência</span><span class="sxs-lookup"><span data-stu-id="c8824-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="c8824-103">O cmdlet Test-dscconfiguration para foi atualizado para permitir que o teste de estado de configuração pretendida de um ou mais nós de destino, especificando um documento de configuração de referência de comparação.</span><span class="sxs-lookup"><span data-stu-id="c8824-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="c8824-104">Os seguintes conjuntos de parâmetro novo utilizam configurações de DSC no caminho especificado para teste apenas e nunca aplicam cada configuração de nó de destino especificado (s).</span><span class="sxs-lookup"><span data-stu-id="c8824-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="c8824-105">Tal como acontece com início-dscconfiguration para e os outros cmdlets de DSC, o nome de cada MOF é utilizado para determinar o nó de destino para testar a configuração no.</span><span class="sxs-lookup"><span data-stu-id="c8824-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

```powershell
Test-DscConfiguration   [-Path] <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```

<span data-ttu-id="c8824-106">Os seguintes conjuntos de parâmetro novo usar uma única configuração de DSC para apenas testar e nunca aplicar a configuração do nó de destino especificado (s).</span><span class="sxs-lookup"><span data-stu-id="c8824-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```
