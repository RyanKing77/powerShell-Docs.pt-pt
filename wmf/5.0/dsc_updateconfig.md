---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 31fde15e644455dbe77f68bca713bf026544fdc7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057575"
---
# <a name="on-demand-pull-of-dsc-configurations"></a>SOLICITAÇÃO a Pedido das Configurações do DSC

O novo cmdlet Update-dscconfiguration para aciona uma solicitação de servidor ou servidores pull definidos na configuração do meta. O comportamento é frequentemente referido como "Obter agora".


Quando acionado, a solicitação se comporta exatamente como seria necessário quando acionada durante a frequência normal:

1. A soma de verificação para a configuração atual é comparada com a soma de verificação para a configuração no servidor de solicitação.
2. Se eles forem iguais, for concluído com êxito sem aplicar a configuração.
3. Se forem diferentes, a configuração é obtida do servidor de solicitação e aplicada.

**Nota:** Se o RefreshMode de Meta-configuração = 'Push' é devolvido um erro por este cmdlet, para que este cmdlet sempre não fará nada quando um nó de destino está no modo de 'Push'.

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
