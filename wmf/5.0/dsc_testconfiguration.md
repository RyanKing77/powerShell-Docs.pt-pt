---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="1b650-102">Cmdlet de teste DscConfiguration suporta configurações de referência</span><span class="sxs-lookup"><span data-stu-id="1b650-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="1b650-103">O cmdlet de teste DscConfiguration foi atualizado para permitir testes de estado de configuração pretendido de um ou mais nós de destino, especificando um documento de configuração de referência de comparação.</span><span class="sxs-lookup"><span data-stu-id="1b650-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="1b650-104">Os seguintes conjuntos de parâmetro novo utilizam configurações de DSC no caminho especificado para o teste apenas e nunca aplicam a cada configuração em nós de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="1b650-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="1b650-105">Tal como acontece com outros cmdlets de DSC e DscConfiguration de início, o nome de cada MOF é utilizado para determinar o nó de destino para testar a configuração.</span><span class="sxs-lookup"><span data-stu-id="1b650-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

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

<span data-ttu-id="1b650-106">Os seguintes conjuntos de parâmetro novo utilizam uma configuração de DSC única para apenas a testar e nunca aplicar a configuração em nós de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="1b650-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

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
