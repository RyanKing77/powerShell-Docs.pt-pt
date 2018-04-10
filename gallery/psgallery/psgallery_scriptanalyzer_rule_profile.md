---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgallery_scriptanalyzer_rule_profile
ms.openlocfilehash: ff575ab56f07312658d111bccd7793b64ac071ea
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a><span data-ttu-id="e0b34-103">Perfil de regra de ScriptAnazlyer de galeria</span><span class="sxs-lookup"><span data-stu-id="e0b34-103">ScriptAnazlyer Rule Profile for Gallery</span></span>
<span data-ttu-id="e0b34-104">Para garantir a qualidade dos itens de galeria do PowerShell publicado, iremos executar [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regras para determinar se existem quaisquer violações em scripts submetidos.</span><span class="sxs-lookup"><span data-stu-id="e0b34-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="e0b34-105">Pode encontrar a lista de regras em execução no ScriptAnalyzer [página do GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="e0b34-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="e0b34-106">Se tiver alguma dúvida sobre as regras em execução, contacte os administradores de galeria do PowerShell ou abra um problema para ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="e0b34-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="e0b34-107">ScriptAnalyzer resultados serão apresentados em cada página item individuais na galeria na versão próximas.</span><span class="sxs-lookup"><span data-stu-id="e0b34-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="e0b34-108">Aconselhamo-os proprietários de item marque os itens para se certificar de que não existirem erros graves nos itens publicados.</span><span class="sxs-lookup"><span data-stu-id="e0b34-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>