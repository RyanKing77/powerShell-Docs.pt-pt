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
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Suporta o cmdlet Test-dscconfiguration para configurações de referência

O cmdlet Test-dscconfiguration para foi atualizado para permitir que o teste de estado de configuração pretendida de um ou mais nós de destino, especificando um documento de configuração de referência de comparação.

Os seguintes conjuntos de parâmetro novo utilizam configurações de DSC no caminho especificado para teste apenas e nunca aplicam cada configuração de nó de destino especificado (s). Tal como acontece com início-dscconfiguration para e os outros cmdlets de DSC, o nome de cada MOF é utilizado para determinar o nó de destino para testar a configuração no.

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

Os seguintes conjuntos de parâmetro novo usar uma única configuração de DSC para apenas testar e nunca aplicar a configuração do nó de destino especificado (s).

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
