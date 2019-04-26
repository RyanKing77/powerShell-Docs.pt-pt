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
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082333"
---
# <a name="how-to-test-updatable-help"></a>How to Test Updatable Help (Como Testar a Ajuda Atualizável)

Este tópico descreve abordagens para ajuda Atualizável de teste para um módulo.

## <a name="using-verbose-to-detect-errors"></a>Utilização detalhada para detectar erros

Depois de carregar o ficheiro XML de HelpInfo e ficheiros CAB para seu módulo, os ficheiros de teste ao executar uma [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) comando com o **verboso** parâmetro. O **verboso** parâmetro direciona `Update-Help` para comunicar as etapas fundamentais em suas ações, de leitura a **HelpInfoUri** chave no manifesto do módulo para validar os tipos de ficheiro no ficheiro CAB descompactado e o posicionamento dos ficheiros no diretório de módulo de idioma específico.

Quando todas as mensagens verbosas são resolvidas, executar uma `Update-Help` comando com o **depurar** parâmetro. Este parâmetro deve detetar problemas restantes com os arquivos de ajuda Atualizável.