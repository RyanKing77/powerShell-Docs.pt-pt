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
# <a name="scriptanazlyer-rule-profile-for-gallery"></a>Perfil de regra de ScriptAnazlyer de galeria
Para garantir a qualidade dos itens de galeria do PowerShell publicado, iremos executar [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regras para determinar se existem quaisquer violações em scripts submetidos.

Pode encontrar a lista de regras em execução no ScriptAnalyzer [página do GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Se tiver alguma dúvida sobre as regras em execução, contacte os administradores de galeria do PowerShell ou abra um problema para ScriptAnalzyer.

ScriptAnalyzer resultados serão apresentados em cada página item individuais na galeria na versão próximas. Aconselhamo-os proprietários de item marque os itens para se certificar de que não existirem erros graves nos itens publicados.