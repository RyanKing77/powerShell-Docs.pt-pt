---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="f0320-102">Frequências para RefreshMode e ConfigurationMode não precisam de ser em múltiplos de si</span><span class="sxs-lookup"><span data-stu-id="f0320-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="f0320-103">Na versão anterior do DSC, deverá tratar o MMC `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` como múltiplos de si.</span><span class="sxs-lookup"><span data-stu-id="f0320-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="f0320-104">WMF 5.0 RTM, estas propriedades são processadas independentes entre si.</span><span class="sxs-lookup"><span data-stu-id="f0320-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span> 

<span data-ttu-id="f0320-105">Para obter mais informações, consulte [configurar o Gestor de configuração Local](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="f0320-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>

