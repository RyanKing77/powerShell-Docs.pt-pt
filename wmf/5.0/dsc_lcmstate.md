---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="c83cd-102">Informações detalhadas sobre o estado de MMC</span><span class="sxs-lookup"><span data-stu-id="c83cd-102">Detailed information about LCM state</span></span>

<span data-ttu-id="c83cd-103">Efetuamos melhorias no expor os detalhes sobre o estado do MMC.</span><span class="sxs-lookup"><span data-stu-id="c83cd-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="c83cd-104">LCMState que é devolvido pelo Get-DscLocalConfigurationManager agora pode conter os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="c83cd-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="c83cd-105">**Inativo**</span><span class="sxs-lookup"><span data-stu-id="c83cd-105">**Idle**</span></span>
* <span data-ttu-id="c83cd-106">**Ocupado**</span><span class="sxs-lookup"><span data-stu-id="c83cd-106">**Busy**</span></span>
* <span data-ttu-id="c83cd-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="c83cd-107">**PendingReboot**</span></span>
* <span data-ttu-id="c83cd-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="c83cd-108">**PendingConfiguration**</span></span>

<span data-ttu-id="c83cd-109">Adicionámos tem também uma propriedade de LCMStateDetail contém mais informações sobre o estado.</span><span class="sxs-lookup"><span data-stu-id="c83cd-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

