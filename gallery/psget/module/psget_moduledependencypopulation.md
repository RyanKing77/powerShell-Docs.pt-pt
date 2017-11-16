---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: psget_moduledependencypopulation
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a>Lógica para preparar as dependências de módulo durante a operação de publicação
1.  Módulos listados como parte do RequiredModules são considerados como dependências.
2.  Módulos listados como parte do NestedModules, cujo base do módulo não está na base de módulo especificado, são considerados como dependências.

3.  Acima dependências devem estar disponíveis no mesmo repositório de destino, caso contrário, publicar operação resultará num erro.
    Por exemplo: se 'SnippetPx' não está disponível no repositório, abaixo erro será emitida.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  Algumas dependências de módulo podem ser geridas externamente, caso em que devem ser adicionados a entrada de ExternalModuleDependencies na secção PSData do manifesto do módulo.
    Abaixo parte na mensagem de erro acima
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*Durante a instalação do módulo, acima dependências preparadas lista é utilizada para instalar as dependências.*

*Certifique-se de que estão disponíveis em $env dependências do módulo: PSModulePath no seu sistema durante a operação de publicar.*

