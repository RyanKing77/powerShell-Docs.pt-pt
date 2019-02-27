---
title: Como atualizar os arquivos de ajuda | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846481"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="2169c-102">How to Update Help Files (Como Atualizar Ficheiros de Ajuda)</span><span class="sxs-lookup"><span data-stu-id="2169c-102">How to Update Help Files</span></span>

<span data-ttu-id="2169c-103">Este tópico explica como atualizar os arquivos de ajuda para um módulo que oferece suporte a ajuda Atualizável.</span><span class="sxs-lookup"><span data-stu-id="2169c-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="2169c-104">A atualizar os arquivos de ajuda</span><span class="sxs-lookup"><span data-stu-id="2169c-104">Updating Help Files</span></span>

<span data-ttu-id="2169c-105">Existem muitas razões para atualizar os arquivos de ajuda, como corrigir erros, esclarecendo um conceito, responder uma pergunta de perguntas mais frequentes, adicionando novos ficheiros ou adicionar novos e melhores exemplos.</span><span class="sxs-lookup"><span data-stu-id="2169c-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="2169c-106">Para atualizar um arquivo de ajuda:</span><span class="sxs-lookup"><span data-stu-id="2169c-106">To update a help file:</span></span>

1. <span data-ttu-id="2169c-107">Altere os arquivos.</span><span class="sxs-lookup"><span data-stu-id="2169c-107">Change the files.</span></span>

2. <span data-ttu-id="2169c-108">Traduza os ficheiros em outras culturas de interface do Usuário.</span><span class="sxs-lookup"><span data-stu-id="2169c-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="2169c-109">Recolha todos os arquivos de ajuda (nova, alterados e inalterados) para o módulo de cada cultura da interface do Usuário.</span><span class="sxs-lookup"><span data-stu-id="2169c-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="2169c-110">Valide os ficheiros no esquema de XML.</span><span class="sxs-lookup"><span data-stu-id="2169c-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="2169c-111">Recompile os arquivos CAB para cada cultura da interface do Usuário.</span><span class="sxs-lookup"><span data-stu-id="2169c-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="2169c-112">No ficheiro XML de HelpInfo, incremente os números de versão do ficheiro CAB para cada cultura da interface do Usuário.</span><span class="sxs-lookup"><span data-stu-id="2169c-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="2169c-113">Carregar os novos ficheiros CAB para o local especificado pelo valor de **HelpContentUri** elemento no arquivo XML de HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="2169c-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="2169c-114">Substitua os arquivos CAB mais antigos por novos ficheiros CAB.</span><span class="sxs-lookup"><span data-stu-id="2169c-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="2169c-115">Carregar o ficheiro XML de HelpInfo atualizado para a localização especificada pelos **HelpInfoUri** chave no manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="2169c-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="2169c-116">Substitua o ficheiro de HelpInfo XML mais antigo com o novo ficheiro.</span><span class="sxs-lookup"><span data-stu-id="2169c-116">Replace the older HelpInfo XML file with the new file.</span></span>