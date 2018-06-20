---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187566"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Cmdlet de teste DscConfiguration suporta configurações de referência

O cmdlet de teste DscConfiguration foi atualizado para permitir testes de estado de configuração pretendido de um ou mais nós de destino, especificando um documento de configuração de referência de comparação.

Os seguintes conjuntos de parâmetro novo utilizam configurações de DSC no caminho especificado para o teste apenas e nunca aplicam a cada configuração em nós de destino especificado. Tal como acontece com outros cmdlets de DSC e DscConfiguration de início, o nome de cada MOF é utilizado para determinar o nó de destino para testar a configuração.

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

Os seguintes conjuntos de parâmetro novo utilizam uma configuração de DSC única para apenas a testar e nunca aplicar a configuração em nós de destino especificado.

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
