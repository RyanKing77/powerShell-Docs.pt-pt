---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 6d37fbc5091d69925d60349f3acbdecc92da1b95
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="on-demand-pull-of-dsc-configurations"></a>SOLICITAÇÃO a Pedido das Configurações do DSC

O novo cmdlet Update-DscConfiguration aciona uma solicitação de servidores a solicitação definidos na configuração de metadados. O comportamento é frequentemente referido como 'Pull agora'.


Quando acionado, a solicitação se comporta exatamente da mesma porque iria tem quando acionado durante a frequência regular:

1. A soma de verificação para a configuração atual é comparado com a soma de verificação para a configuração no servidor de solicitação.
2. Se forem iguais, concluir com êxito sem aplicar a configuração.
3. Se forem diferentes, a configuração é solicitada para baixo a partir do servidor de solicitação e aplicada.

**Nota:** se a configuração Meta RefreshMode = 'Push' é devolvido um erro por este cmdlet, pelo que este cmdlet sempre não fará nada quando um nó de destino estiver no modo "Push".

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
