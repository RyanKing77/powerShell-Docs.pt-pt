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
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="65144-102">A pedido SOLICITAÇÃO das configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="65144-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="65144-103">O novo cmdlet Update-DscConfiguration aciona uma solicitação de servidores a solicitação definidos na configuração de metadados.</span><span class="sxs-lookup"><span data-stu-id="65144-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="65144-104">O comportamento é frequentemente referido como 'Pull agora'.</span><span class="sxs-lookup"><span data-stu-id="65144-104">The behavior is often referred to as 'Pull Now'.</span></span> 


<span data-ttu-id="65144-105">Quando acionado, a solicitação se comporta exatamente da mesma porque iria tem quando acionado durante a frequência regular:</span><span class="sxs-lookup"><span data-stu-id="65144-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="65144-106">A soma de verificação para a configuração atual é comparado com a soma de verificação para a configuração no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="65144-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span> 
2. <span data-ttu-id="65144-107">Se forem iguais, concluir com êxito sem aplicar a configuração.</span><span class="sxs-lookup"><span data-stu-id="65144-107">If they are the same, it completes successfully without applying the configuration.</span></span> 
3. <span data-ttu-id="65144-108">Se forem diferentes, a configuração é solicitada para baixo a partir do servidor de solicitação e aplicada.</span><span class="sxs-lookup"><span data-stu-id="65144-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="65144-109">**Nota:** se a configuração Meta RefreshMode = 'Push' é devolvido um erro por este cmdlet, pelo que este cmdlet sempre não fará nada quando um nó de destino estiver no modo "Push".</span><span class="sxs-lookup"><span data-stu-id="65144-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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

