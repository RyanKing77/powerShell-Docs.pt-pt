---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Perfil de regra de ScriptAnalyzer para Galeria
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683857"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="53b1d-103">Perfil de regra de ScriptAnalyzer para Galeria</span><span class="sxs-lookup"><span data-stu-id="53b1d-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="53b1d-104">Para garantir a qualidade dos pacotes publicados galeria do PowerShell, executamos [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regras para determinar se existem quaisquer violações nos scripts de submetido.</span><span class="sxs-lookup"><span data-stu-id="53b1d-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="53b1d-105">Pode encontrar a lista de regras que estão em execução no ScriptAnalyzer [página do GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="53b1d-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="53b1d-106">Se tiver alguma dúvida sobre as regras que estão em execução, contacte os administradores de galeria do PowerShell ou abra um problema para ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="53b1d-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="53b1d-107">ScriptAnalyzer resultados serão apresentados em cada página individual de pacote na galeria no próximo lançamento.</span><span class="sxs-lookup"><span data-stu-id="53b1d-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="53b1d-108">Nós o encorajamos os proprietários de pacote para verificar os pacotes para se certificar de que existem não existem erros graves no pacotes publicados.</span><span class="sxs-lookup"><span data-stu-id="53b1d-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
