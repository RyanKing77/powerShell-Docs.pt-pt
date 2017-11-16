---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: ce60b240045acf538edae1a08007971e538588ca
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2017
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

