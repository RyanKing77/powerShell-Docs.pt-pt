---
title: Como adicionar exemplos para um tópico de ajuda do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 5e8d1df6b423bfd2cd6b0a64a8875dea9c3fb4ef
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083472"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="09f1a-102">How to Add Examples to a Cmdlet Help Topic (Como Adicionar Exemplos ao Tópico de Ajuda de um Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="09f1a-102">How to Add Examples to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="09f1a-103">Que precisa saber sobre exemplos de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09f1a-103">Things to Know about Examples in Cmdlet Help</span></span>](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [<span data-ttu-id="09f1a-104">As vistas que apresentam exemplos de ajuda</span><span class="sxs-lookup"><span data-stu-id="09f1a-104">Help Views that Display Examples</span></span>](#Help-Views-that-Display-Examples)

- [<span data-ttu-id="09f1a-105">Adicionar um nó de exemplos</span><span class="sxs-lookup"><span data-stu-id="09f1a-105">Adding an Examples Node</span></span>](#Adding-an-Examples-Node)

- [<span data-ttu-id="09f1a-106">Adicionar precedem</span><span class="sxs-lookup"><span data-stu-id="09f1a-106">Adding Preceding Characters</span></span>](#Adding-Preceding-Characters)

- [<span data-ttu-id="09f1a-107">Adicionar o comando</span><span class="sxs-lookup"><span data-stu-id="09f1a-107">Adding the Command</span></span>](#Adding-the-Command)

- [<span data-ttu-id="09f1a-108">Adicionar uma descrição</span><span class="sxs-lookup"><span data-stu-id="09f1a-108">Adding a Description</span></span>](#Adding-a-Description)

- [<span data-ttu-id="09f1a-109">Adicionar a saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="09f1a-109">Adding Example Output</span></span>](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="09f1a-110">Que precisa saber sobre exemplos de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09f1a-110">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="09f1a-111">Liste todos os nomes de parâmetros no comando, mesmo quando os nomes de parâmetros são opcionais.</span><span class="sxs-lookup"><span data-stu-id="09f1a-111">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="09f1a-112">Isto ajuda o usuário interpretar o comando facilmente.</span><span class="sxs-lookup"><span data-stu-id="09f1a-112">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="09f1a-113">Evite aliases e nomes de parâmetro parcial, mesmo que trabalham em Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="09f1a-113">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="09f1a-114">A descrição de exemplo, explico o rational para a construção do comando.</span><span class="sxs-lookup"><span data-stu-id="09f1a-114">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="09f1a-115">Explique por que escolheu particulares parâmetros e valores, e como utilizar variáveis.</span><span class="sxs-lookup"><span data-stu-id="09f1a-115">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="09f1a-116">Se o comando utilizar expressões, explicaremos em detalhes.</span><span class="sxs-lookup"><span data-stu-id="09f1a-116">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="09f1a-117">Se o comando utiliza as propriedades e métodos de objetos, especialmente as propriedades que não aparecem na exibição padrão, utilize o exemplo de como uma oportunidade informar ao usuário sobre o objeto.</span><span class="sxs-lookup"><span data-stu-id="09f1a-117">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="09f1a-118">As vistas que apresentam exemplos de ajuda</span><span class="sxs-lookup"><span data-stu-id="09f1a-118">Help Views that Display Examples</span></span>

<span data-ttu-id="09f1a-119">Exemplos aparecem apenas em modos de exibição detalhado e completo de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="09f1a-119">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="09f1a-120">Adicionar um nó de exemplos</span><span class="sxs-lookup"><span data-stu-id="09f1a-120">Adding an Examples Node</span></span>

<span data-ttu-id="09f1a-121">O XML a seguir mostra como adicionar um nó de exemplos que contém um único nó de exemplo.</span><span class="sxs-lookup"><span data-stu-id="09f1a-121">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="09f1a-122">Adicione nós de exemplo adicionais para cada exemplos que pretende incluir no tópico.</span><span class="sxs-lookup"><span data-stu-id="09f1a-122">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="09f1a-123">Adicionar um título de exemplo</span><span class="sxs-lookup"><span data-stu-id="09f1a-123">Adding an Example Title</span></span>

<span data-ttu-id="09f1a-124">O XML a seguir mostra como adicionar um título para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="09f1a-124">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="09f1a-125">O título é usado para definir o exemplo para além dos outros exemplos.</span><span class="sxs-lookup"><span data-stu-id="09f1a-125">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="09f1a-126">Windows PowerShell® utiliza um padrão cabeçalho que inclui um conjunto de exemplo seqüencial.</span><span class="sxs-lookup"><span data-stu-id="09f1a-126">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="09f1a-127">Adicionar precedem</span><span class="sxs-lookup"><span data-stu-id="09f1a-127">Adding Preceding Characters</span></span>

<span data-ttu-id="09f1a-128">O XML a seguir mostra como adicionar caracteres, como a linha de comandos do Windows PowerShell, que são apresentados imediatamente antes do comando de exemplo (sem espaços intervenientes).</span><span class="sxs-lookup"><span data-stu-id="09f1a-128">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="09f1a-129">Windows PowerShell® utiliza a linha de comandos do Windows PowerShell: C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="09f1a-129">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a><span data-ttu-id="09f1a-130">Adicionar o comando</span><span class="sxs-lookup"><span data-stu-id="09f1a-130">Adding the Command</span></span>

<span data-ttu-id="09f1a-131">O XML a seguir mostra como adicionar o comando real do exemplo.</span><span class="sxs-lookup"><span data-stu-id="09f1a-131">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="09f1a-132">Ao adicionar o comando, digite o nome completo (não utilize alias) dos cmdlets e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="09f1a-132">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="09f1a-133">Além disso, utilize carateres minúsculos, sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="09f1a-133">Also, use lowercase characters whenever possible.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a><span data-ttu-id="09f1a-134">Adicionar uma descrição</span><span class="sxs-lookup"><span data-stu-id="09f1a-134">Adding a Description</span></span>

<span data-ttu-id="09f1a-135">O XML a seguir mostra como adicionar uma descrição para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="09f1a-135">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="09f1a-136">Windows PowerShell® utiliza um único conjunto de \<maml:para > com as etiquetas para a descrição, mesmo que vários \<maml:para > as etiquetas podem ser utilizadas.</span><span class="sxs-lookup"><span data-stu-id="09f1a-136">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a><span data-ttu-id="09f1a-137">Adicionar a saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="09f1a-137">Adding Example Output</span></span>

<span data-ttu-id="09f1a-138">O XML a seguir mostra como adicionar a saída do comando.</span><span class="sxs-lookup"><span data-stu-id="09f1a-138">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="09f1a-139">As informações de resultados do comando são opcionais, mas em alguns casos é útil demonstrar o efeito do uso de parâmetros específicos.</span><span class="sxs-lookup"><span data-stu-id="09f1a-139">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="09f1a-140">Windows PowerShell® utiliza dois conjuntos de aplicação em branco \<maml:para > etiquetas para separar a saída do comando do comando.</span><span class="sxs-lookup"><span data-stu-id="09f1a-140">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```