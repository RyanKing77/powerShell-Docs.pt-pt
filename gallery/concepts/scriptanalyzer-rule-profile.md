---
ms.date: 06/12/2017
contributor: JKeithB
keywords: cmdlet do powershell do galeria, psgallery
title: Perfil de regra ScriptAnalyzer para da Galeria
ms.openlocfilehash: 54100f7a530cbc769e4a0e2dbff18dbc5de88fa6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225747"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Perfil de regra ScriptAnalyzer para da Galeria

Para garantir a qualidade dos itens de galeria do PowerShell publicado, iremos executar [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regras para determinar se existem quaisquer violações em scripts submetidos.

Pode encontrar a lista de regras em execução no ScriptAnalyzer [página do GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Se tiver alguma dúvida sobre as regras em execução, contacte os administradores de galeria do PowerShell ou abra um problema para ScriptAnalzyer.

ScriptAnalyzer resultados serão apresentados em cada página item individuais na galeria na versão próximas. Aconselhamo-os proprietários de item marque os itens para se certificar de que não existirem erros graves nos itens publicados.
