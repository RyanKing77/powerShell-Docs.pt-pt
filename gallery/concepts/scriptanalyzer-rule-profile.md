---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: Perfil de regra ScriptAnalyzer para da Galeria
ms.openlocfilehash: 22b95f0901fe95d5ad79df0e23e675ab52313fee
ms.sourcegitcommit: f8a37df92db22b9368469fb07378399b2ab90cea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/14/2018
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Perfil de regra ScriptAnalyzer para da Galeria

Para garantir a qualidade dos itens de galeria do PowerShell publicado, iremos executar [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regras para determinar se existem quaisquer violações em scripts submetidos.

Pode encontrar a lista de regras em execução no ScriptAnalyzer [página do GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Se tiver alguma dúvida sobre as regras em execução, contacte os administradores de galeria do PowerShell ou abra um problema para ScriptAnalzyer.

ScriptAnalyzer resultados serão apresentados em cada página item individuais na galeria na versão próximas. Aconselhamo-os proprietários de item marque os itens para se certificar de que não existirem erros graves nos itens publicados.
