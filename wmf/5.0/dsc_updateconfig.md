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
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="5bc2f-102">SOLICITAÇÃO a Pedido das Configurações do DSC</span><span class="sxs-lookup"><span data-stu-id="5bc2f-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="5bc2f-103">O novo cmdlet Update-dscconfiguration para aciona uma solicitação de servidor ou servidores pull definidos na configuração do meta.</span><span class="sxs-lookup"><span data-stu-id="5bc2f-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="5bc2f-104">O comportamento é frequentemente referido como "Obter agora".</span><span class="sxs-lookup"><span data-stu-id="5bc2f-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="5bc2f-105">Quando acionado, a solicitação se comporta exatamente como seria necessário quando acionada durante a frequência normal:</span><span class="sxs-lookup"><span data-stu-id="5bc2f-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="5bc2f-106">A soma de verificação para a configuração atual é comparada com a soma de verificação para a configuração no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="5bc2f-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="5bc2f-107">Se eles forem iguais, for concluído com êxito sem aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="5bc2f-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="5bc2f-108">Se forem diferentes, a configuração é obtida do servidor de solicitação e aplicada.</span><span class="sxs-lookup"><span data-stu-id="5bc2f-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="5bc2f-109">**Nota:** Se o RefreshMode de Meta-configuração = 'Push' é devolvido um erro por este cmdlet, para que este cmdlet sempre não fará nada quando um nó de destino está no modo de 'Push'.</span><span class="sxs-lookup"><span data-stu-id="5bc2f-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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
