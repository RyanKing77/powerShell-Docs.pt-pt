---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: f2ddde78f436e6f03f521a9a8246dbda93e7a57a
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2017
---
# <a name="on-demand-pull-of-dsc-configurations"></a>A pedido SOLICITAÇÃO das configurações de DSC

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

