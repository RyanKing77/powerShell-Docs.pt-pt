---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685747"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="77a38-102">Informações detalhadas sobre o estado LCM</span><span class="sxs-lookup"><span data-stu-id="77a38-102">Detailed information about LCM state</span></span>

<span data-ttu-id="77a38-103">Fizemos melhorias em expor detalhes sobre o estado do LCM.</span><span class="sxs-lookup"><span data-stu-id="77a38-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="77a38-104">O que é devolvido pelo Get-dsclocalconfigurationmanager para LCMState agora pode conter os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="77a38-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="77a38-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="77a38-105">**Idle**</span></span>
* <span data-ttu-id="77a38-106">**Ocupado**</span><span class="sxs-lookup"><span data-stu-id="77a38-106">**Busy**</span></span>
* <span data-ttu-id="77a38-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="77a38-107">**PendingReboot**</span></span>
* <span data-ttu-id="77a38-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="77a38-108">**PendingConfiguration**</span></span>

<span data-ttu-id="77a38-109">Também adicionámos uma propriedade de LCMStateDetail que contém mais informações sobre o estado.</span><span class="sxs-lookup"><span data-stu-id="77a38-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
