---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 136e16ae74e54f3bc9d0623178257df1e9104aac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="a35b9-102">Fornecer um documento de configuração sem aplicar</span><span class="sxs-lookup"><span data-stu-id="a35b9-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="a35b9-103">O [publicar DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copia um ficheiro MOF de configuração para um nó de destino, mas não se aplica a configuração.</span><span class="sxs-lookup"><span data-stu-id="a35b9-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="a35b9-104">Esta configuração é aplicada durante a próxima passagem de consistência ou ao executar o [atualização DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a35b9-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>