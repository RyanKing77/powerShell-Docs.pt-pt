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
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="527bf-103">Lógica para preparar as dependências de módulo durante a operação de publicação</span><span class="sxs-lookup"><span data-stu-id="527bf-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="527bf-104">Módulos listados como parte do RequiredModules são considerados como dependências.</span><span class="sxs-lookup"><span data-stu-id="527bf-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="527bf-105">Módulos listados como parte do NestedModules, cujo base do módulo não está na base de módulo especificado, são considerados como dependências.</span><span class="sxs-lookup"><span data-stu-id="527bf-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="527bf-106">Acima dependências devem estar disponíveis no mesmo repositório de destino, caso contrário, publicar operação resultará num erro.</span><span class="sxs-lookup"><span data-stu-id="527bf-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="527bf-107">Por exemplo: se 'SnippetPx' não está disponível no repositório, abaixo erro será emitida.</span><span class="sxs-lookup"><span data-stu-id="527bf-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="527bf-108">Algumas dependências de módulo podem ser geridas externamente, caso em que devem ser adicionados a entrada de ExternalModuleDependencies na secção PSData do manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="527bf-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="527bf-109">Abaixo parte na mensagem de erro acima</span><span class="sxs-lookup"><span data-stu-id="527bf-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="527bf-110">*Durante a instalação do módulo, acima dependências preparadas lista é utilizada para instalar as dependências.*</span><span class="sxs-lookup"><span data-stu-id="527bf-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="527bf-111">*Certifique-se de que estão disponíveis em $env dependências do módulo: PSModulePath no seu sistema durante a operação de publicar.*</span><span class="sxs-lookup"><span data-stu-id="527bf-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>

