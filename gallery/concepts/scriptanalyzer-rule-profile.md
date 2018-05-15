---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: Perfil de regra ScriptAnazlyer para da Galeria
ms.openlocfilehash: 74eab49e4c4a546655451ef21b30cfcafaeb9584
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a><span data-ttu-id="32775-103">Perfil de regra ScriptAnazlyer para da Galeria</span><span class="sxs-lookup"><span data-stu-id="32775-103">ScriptAnazlyer rule profile for Gallery</span></span>

<span data-ttu-id="32775-104">Para garantir a qualidade dos itens de galeria do PowerShell publicado, iremos executar [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regras para determinar se existem quaisquer violações em scripts submetidos.</span><span class="sxs-lookup"><span data-stu-id="32775-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="32775-105">Pode encontrar a lista de regras em execução no ScriptAnalyzer [página do GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="32775-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="32775-106">Se tiver alguma dúvida sobre as regras em execução, contacte os administradores de galeria do PowerShell ou abra um problema para ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="32775-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="32775-107">ScriptAnalyzer resultados serão apresentados em cada página item individuais na galeria na versão próximas.</span><span class="sxs-lookup"><span data-stu-id="32775-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="32775-108">Aconselhamo-os proprietários de item marque os itens para se certificar de que não existirem erros graves nos itens publicados.</span><span class="sxs-lookup"><span data-stu-id="32775-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>