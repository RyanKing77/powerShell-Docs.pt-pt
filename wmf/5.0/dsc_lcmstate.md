---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="dd0aa-102">Informações detalhadas sobre o estado de MMC</span><span class="sxs-lookup"><span data-stu-id="dd0aa-102">Detailed information about LCM state</span></span>

<span data-ttu-id="dd0aa-103">Efetuamos melhorias no expor os detalhes sobre o estado do MMC.</span><span class="sxs-lookup"><span data-stu-id="dd0aa-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="dd0aa-104">LCMState que é devolvido pelo Get-DscLocalConfigurationManager agora pode conter os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="dd0aa-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="dd0aa-105">**Inativo**</span><span class="sxs-lookup"><span data-stu-id="dd0aa-105">**Idle**</span></span>
* <span data-ttu-id="dd0aa-106">**Ocupado**</span><span class="sxs-lookup"><span data-stu-id="dd0aa-106">**Busy**</span></span>
* <span data-ttu-id="dd0aa-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="dd0aa-107">**PendingReboot**</span></span>
* <span data-ttu-id="dd0aa-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="dd0aa-108">**PendingConfiguration**</span></span>

<span data-ttu-id="dd0aa-109">Adicionámos tem também uma propriedade de LCMStateDetail contém mais informações sobre o estado.</span><span class="sxs-lookup"><span data-stu-id="dd0aa-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
