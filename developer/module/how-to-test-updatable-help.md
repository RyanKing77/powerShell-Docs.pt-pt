---
title: Como testar ajuda Atualizável | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845928"
---
# <a name="how-to-test-updatable-help"></a>How to Test Updatable Help (Como Testar a Ajuda Atualizável)

Este tópico descreve abordagens para ajuda Atualizável de teste para um módulo.

## <a name="using-verbose-to-detect-errors"></a>Utilização detalhada para detectar erros

Depois de carregar o ficheiro XML de HelpInfo e ficheiros CAB para seu módulo, os ficheiros de teste ao executar uma [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) comando com o **verboso** parâmetro. O **verboso** parâmetro direciona `Update-Help` para comunicar as etapas fundamentais em suas ações, de leitura a **HelpInfoUri** chave no manifesto do módulo para validar os tipos de ficheiro no ficheiro CAB descompactado e o posicionamento dos ficheiros no diretório de módulo de idioma específico.
Depois de carregar o ficheiro XML de HelpInfo e ficheiros CAB para seu módulo, os ficheiros de teste ao executar uma [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) comando com o **verboso** parâmetro. O **verboso** parâmetro direciona `Update-Help` para comunicar as etapas fundamentais em suas ações, de leitura a **HelpInfoUri** chave no manifesto do módulo para validar os tipos de ficheiro no ficheiro CAB descompactado e o posicionamento dos ficheiros no diretório de módulo de idioma específico.

Quando todas as mensagens verbosas são resolvidas, executar uma `Update-Help` comando com o **depurar** parâmetro. Este parâmetro deve detetar problemas restantes com os arquivos de ajuda Atualizável.