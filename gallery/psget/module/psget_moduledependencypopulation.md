---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: psget_moduledependencypopulation
ms.openlocfilehash: c4c9f203e9c526ff532c2388acb6334515d66934
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="f87b7-103">Lógica para preparar as dependências de módulo durante a operação de publicação</span><span class="sxs-lookup"><span data-stu-id="f87b7-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="f87b7-104">Módulos listados como parte do RequiredModules são considerados como dependências.</span><span class="sxs-lookup"><span data-stu-id="f87b7-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="f87b7-105">Módulos listados como parte do NestedModules, cujo base do módulo não está na base de módulo especificado, são considerados como dependências.</span><span class="sxs-lookup"><span data-stu-id="f87b7-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="f87b7-106">Acima dependências devem estar disponíveis no mesmo repositório de destino, caso contrário, publicar operação resultará num erro.</span><span class="sxs-lookup"><span data-stu-id="f87b7-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="f87b7-107">Por exemplo: se 'SnippetPx' não está disponível no repositório, abaixo erro será emitida.</span><span class="sxs-lookup"><span data-stu-id="f87b7-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="f87b7-108">Algumas dependências de módulo podem ser geridas externamente, caso em que devem ser adicionados a entrada de ExternalModuleDependencies na secção PSData do manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="f87b7-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="f87b7-109">Abaixo parte na mensagem de erro acima</span><span class="sxs-lookup"><span data-stu-id="f87b7-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="f87b7-110">*Durante a instalação do módulo, acima dependências preparadas lista é utilizada para instalar as dependências.*</span><span class="sxs-lookup"><span data-stu-id="f87b7-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="f87b7-111">*Certifique-se de que estão disponíveis em $env dependências do módulo: PSModulePath no seu sistema durante a operação de publicar.*</span><span class="sxs-lookup"><span data-stu-id="f87b7-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>