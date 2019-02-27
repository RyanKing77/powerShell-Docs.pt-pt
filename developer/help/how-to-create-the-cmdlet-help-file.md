---
title: Como criar o ficheiro de ajuda do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848896"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="3827d-102">How to Create the Cmdlet Help File (Como Criar um Ficheiro de Ajuda de Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="3827d-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="3827d-103">Esta secção descreve como criar um ficheiro XML válido, que contém conteúdos para tópicos de ajuda do cmdlet Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3827d-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="3827d-104">Esta secção descreve como nomear o arquivo de ajuda, como adicionar os cabeçalhos XML apropriados e como adicionar nós que irão conter as diferentes seções do conteúdo da ajuda cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="3827d-105">Para obter uma visão completa de um arquivo de ajuda, abra de um dos ficheiros dll Help.xml localizado no diretório de instalação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3827d-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="3827d-106">Por exemplo, o ficheiro de Microsoft.PowerShell.Commands.Management.dll Help.xml contém conteúdo para vários dos cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3827d-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="3827d-107">Como criar um ficheiro de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3827d-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="3827d-108">Crie um arquivo de texto e guarde-o com codificação UTF8.</span><span class="sxs-lookup"><span data-stu-id="3827d-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="3827d-109">O nome do ficheiro tem de ter o seguinte formato para que o Windows PowerShell pode detetá-lo como um arquivo de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="3827d-110">Adicione os seguintes cabeçalhos XML para o arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="3827d-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="3827d-111">Lembre-se de que o ficheiro vai ser validado no esquema de linguagem de modelagem de agente multi (MAML).</span><span class="sxs-lookup"><span data-stu-id="3827d-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="3827d-112">Atualmente, o Windows PowerShell não fornece quaisquer ferramentas para validar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="3827d-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="3827d-113">Adicione um nó de comando para o ficheiro de ajuda do cmdlet para cada cmdlet no assembly.</span><span class="sxs-lookup"><span data-stu-id="3827d-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="3827d-114">Cada nó no nó de comando está relacionado com as diferentes secções do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="3827d-115">A tabela seguinte lista o elemento XML para cada nó, seguido de uma descrição de cada nó.</span><span class="sxs-lookup"><span data-stu-id="3827d-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="3827d-116">Nó</span><span class="sxs-lookup"><span data-stu-id="3827d-116">Node</span></span>|<span data-ttu-id="3827d-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3827d-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="3827d-118">Adiciona o conteúdo para as secções de nome e uma sinopse do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="3827d-119">Para obter mais informações, consulte [como adicionar o nome do Cmdlet e sinopse](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="3827d-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="3827d-120">Adiciona o conteúdo para a seção de descrição do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="3827d-121">Para obter mais informações, consulte [como adicionar a descrição detalhada para um tópico de ajuda do Cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="3827d-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="3827d-122">Adiciona o conteúdo para a secção de sintaxe do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="3827d-123">Para obter mais informações, consulte [como a sintaxe adicionar um tópico de ajuda do Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="3827d-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="3827d-124">Adiciona o conteúdo para a secção de parâmetros do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3827d-125">Para obter mais informações, consulte [como adicionar parâmetros para um tópico de ajuda do Cmdlet](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="3827d-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="3827d-126">Adiciona o conteúdo para a secção de entradas do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3827d-127">Para obter mais informações, consulte [como adicionar tipos de entrada para um tópico de ajuda do Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="3827d-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="3827d-128">Adiciona o conteúdo para a secção de saídas do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3827d-129">Para obter mais informações, consulte [como adicionar retornar valores para um tópico de ajuda do Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="3827d-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="3827d-130">Adiciona o conteúdo para a secção de notas do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="3827d-131">Para obter mais informações, consulte [notas de como adicionar um tópico de ajuda do Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="3827d-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="3827d-132">Adiciona o conteúdo para a secção de exemplos do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="3827d-133">Para obter mais informações, consulte [como adicionar exemplos para um tópico de ajuda do Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="3827d-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="3827d-134">Adiciona o conteúdo para a secção de LINKS relacionados do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3827d-135">Para obter mais informações, consulte [como adicionar Links relacionados para um tópico de ajuda do Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="3827d-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="3827d-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3827d-136">Example</span></span>

 <span data-ttu-id="3827d-137">Eis um exemplo de um nó de comando que inclui os nós para as diversas secções do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3827d-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="3827d-138">Veja Também</span><span class="sxs-lookup"><span data-stu-id="3827d-138">See Also</span></span>

 [<span data-ttu-id="3827d-139">Como adicionar o nome do Cmdlet e sinopse</span><span class="sxs-lookup"><span data-stu-id="3827d-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3827d-140">Como adicionar a descrição detalhada para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3827d-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="3827d-141">Como adicionar a sintaxe para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3827d-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3827d-142">Como adicionar parâmetros a um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3827d-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="3827d-143">Como adicionar tipos de entrada para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3827d-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3827d-144">Como adicionar valores de retorno para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3827d-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3827d-145">Como adicionar notas para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3827d-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3827d-146">Como adicionar exemplos para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3827d-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3827d-147">Como adicionar Links relacionados a um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3827d-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3827d-148">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3827d-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)