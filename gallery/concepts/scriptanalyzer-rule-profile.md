---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Perfil de regra de ScriptAnalyzer para Galeria
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002501"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Perfil de regra de ScriptAnalyzer para Galeria

Para garantir a qualidade dos pacotes publicados galeria do PowerShell, executamos [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regras para determinar se existem quaisquer violações nos scripts de submetido.

Pode encontrar a lista de regras que estão em execução no ScriptAnalyzer [página do GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Se tiver alguma dúvida sobre as regras que estão em execução, contacte os administradores de galeria do PowerShell ou abra um problema para ScriptAnalzyer.

ScriptAnalyzer resultados serão apresentados em cada página individual de pacote na galeria no próximo lançamento. Nós o encorajamos os proprietários de pacote para verificar os pacotes para se certificar de que existem não existem erros graves no pacotes publicados.
