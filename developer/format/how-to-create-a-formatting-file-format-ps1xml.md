---
title: Como criar um ficheiro de formatação (. format.ps1xml) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065506"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="1c2cc-102">How to Create a Formatting File (.format.ps1xml) (Como Criar um Ficheiro de Formatação [.format.ps1xml])</span><span class="sxs-lookup"><span data-stu-id="1c2cc-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="1c2cc-103">Este tópico descreve como criar um ficheiro de formatação (. format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="1c2cc-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="1c2cc-104">Também pode criar um ficheiro de formatação fazendo uma cópia de um dos ficheiros fornecidos pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="1c2cc-105">Se fizer uma cópia de um arquivo existente, elimine a assinatura digital existente e adicionar sua própria assinatura para o novo ficheiro.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="1c2cc-106">Para criar um. format.ps1xml ficheiro.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="1c2cc-107">Crie um ficheiro de texto (. txt) com um texto editor como o bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="1c2cc-108">Copie as seguintes linhas no arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="1c2cc-109">O \<configuração >\</Configuration > etiquetas definem raiz `Configuration` nó.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="1c2cc-110">Este nó irão estar entre todas as outras etiquetas XML.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="1c2cc-111">O <ViewDefinitions> </ViewDefinitions> definem etiquetas a `ViewDefinitions` nó.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="1c2cc-112">Todas as vistas são definidas dentro deste nó.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="1c2cc-113">Guarde o ficheiro para a pasta de instalação do Windows PowerShell, para a pasta do módulo ou para uma subpasta da pasta de módulo.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="1c2cc-114">Utilize o seguinte formato de nome quando guardar o ficheiro: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="1c2cc-115">Formatação de ficheiros tem de utilizar o `.format.ps1xml` extensão.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="1c2cc-116">Agora está pronto para adicionar vistas para o ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="1c2cc-117">Não existe nenhum limite para o número de visualizações que podem ser definidos num arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="1c2cc-118">Pode adicionar uma vista única para cada objeto, várias exibições para o mesmo objeto ou uma vista única que é utilizada por vários objetos.</span><span class="sxs-lookup"><span data-stu-id="1c2cc-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c2cc-119">Veja Também</span><span class="sxs-lookup"><span data-stu-id="1c2cc-119">See Also</span></span>

[<span data-ttu-id="1c2cc-120">Escrever do Windows PowerShell, formatação e os tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="1c2cc-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
