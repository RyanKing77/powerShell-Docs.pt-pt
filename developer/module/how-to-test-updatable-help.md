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
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794268"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="db7c9-102">How to Test Updatable Help (Como Testar a Ajuda Atualizável)</span><span class="sxs-lookup"><span data-stu-id="db7c9-102">How to Test Updatable Help</span></span>

<span data-ttu-id="db7c9-103">Este tópico descreve abordagens para ajuda Atualizável de teste para um módulo.</span><span class="sxs-lookup"><span data-stu-id="db7c9-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="db7c9-104">Utilização detalhada para detectar erros</span><span class="sxs-lookup"><span data-stu-id="db7c9-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="db7c9-105">Depois de carregar o ficheiro XML de HelpInfo e ficheiros CAB para seu módulo, os ficheiros de teste ao executar uma [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) comando com o **verboso** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="db7c9-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="db7c9-106">O **verboso** parâmetro direciona `Update-Help` para comunicar as etapas fundamentais em suas ações, de leitura a **HelpInfoUri** chave no manifesto do módulo para validar os tipos de ficheiro no ficheiro CAB descompactado e o posicionamento dos ficheiros no diretório de módulo de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="db7c9-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="db7c9-107">Quando todas as mensagens verbosas são resolvidas, executar uma `Update-Help` comando com o **depurar** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="db7c9-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="db7c9-108">Este parâmetro deve detetar problemas restantes com os arquivos de ajuda Atualizável.</span><span class="sxs-lookup"><span data-stu-id="db7c9-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>