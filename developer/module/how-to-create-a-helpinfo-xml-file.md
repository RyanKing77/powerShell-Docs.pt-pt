---
title: Como criar um arquivo XML de HelpInfo | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082418"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="e7c8b-102">How to Create a HelpInfo XML File (Como Criar um Ficheiro XML HelpInfo)</span><span class="sxs-lookup"><span data-stu-id="e7c8b-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="e7c8b-103">Este tópico nesta secção explica como criar e preencher um arquivo de informações de ajuda, comumente conhecido como um "HelpInfo arquivo XML," para a funcionalidade de ajuda Atualizável do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="e7c8b-104">Visão geral de arquivos HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="e7c8b-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="e7c8b-105">O ficheiro XML de HelpInfo é a principal fonte de informações sobre Ajuda Atualizável para o módulo.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="e7c8b-106">Ele inclui a localização dos ficheiros de ajuda para os módulos, as culturas suportadas da interface do Usuário e os números de versão que ajuda Atualizável utiliza para determinar se o utilizador tem os ficheiros de ajuda mais recentes.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="e7c8b-107">Cada módulo tem apenas um arquivo de XML de HelpInfo, mesmo que o módulo inclui vários arquivos de ajuda para várias culturas de interface do Usuário.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="e7c8b-108">O autor de módulos cria o arquivo XML de HelpInfo e o coloca na localização de Internet que é especificada pela **HelpInfoUri** chave no manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="e7c8b-109">Quando os arquivos de ajuda do módulo são atualizados e carregados, o autor do módulo atualiza o ficheiro XML de HelpInfo e substitui o ficheiro XML de HelpInfo original com a nova versão.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="e7c8b-110">É fundamental que o ficheiro XML de HelpInfo cuidadosamente é mantido.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="e7c8b-111">Se carregar novos ficheiros, mas se esqueça de incrementar os números de versão, ajuda Atualizável não transferirá os novos ficheiros nos computadores dos usuários.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="e7c8b-112">Se adicionar arquivos de ajuda para uma nova cultura da interface do Usuário, mas não atualizar o ficheiro XML de HelpInfo ou coloque-o na localização correta, a ajuda Atualizável não irá transferir os ficheiros novos.</span><span class="sxs-lookup"><span data-stu-id="e7c8b-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e7c8b-113">Nesta secção</span><span class="sxs-lookup"><span data-stu-id="e7c8b-113">In this section</span></span>

<span data-ttu-id="e7c8b-114">Esta secção inclui os tópicos seguintes:</span><span class="sxs-lookup"><span data-stu-id="e7c8b-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="e7c8b-115">Esquema HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="e7c8b-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="e7c8b-116">Ficheiro de exemplo do XML de HelpInfo</span><span class="sxs-lookup"><span data-stu-id="e7c8b-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="e7c8b-117">Como atribuir um nome um arquivo XML de HelpInfo</span><span class="sxs-lookup"><span data-stu-id="e7c8b-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="e7c8b-118">Como configurar números de versão HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="e7c8b-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="e7c8b-119">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e7c8b-119">See Also</span></span>

[<span data-ttu-id="e7c8b-120">Apoio ajuda Atualizável</span><span class="sxs-lookup"><span data-stu-id="e7c8b-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)