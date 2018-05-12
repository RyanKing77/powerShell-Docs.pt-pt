---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: Perfil de regra ScriptAnazlyer para da Galeria
ms.openlocfilehash: 74eab49e4c4a546655451ef21b30cfcafaeb9584
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a>Perfil de regra ScriptAnazlyer para da Galeria

Para garantir a qualidade dos itens de galeria do PowerShell publicado, iremos executar [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regras para determinar se existem quaisquer violações em scripts submetidos.

Pode encontrar a lista de regras em execução no ScriptAnalyzer [página do GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Se tiver alguma dúvida sobre as regras em execução, contacte os administradores de galeria do PowerShell ou abra um problema para ScriptAnalzyer.

ScriptAnalyzer resultados serão apresentados em cada página item individuais na galeria na versão próximas. Aconselhamo-os proprietários de item marque os itens para se certificar de que não existirem erros graves nos itens publicados.