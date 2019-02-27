---
title: Escrever ajuda para Cmdlets do PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848112"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="69d9e-102">Escrever ajuda para Cmdlets do PowerShell</span><span class="sxs-lookup"><span data-stu-id="69d9e-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="69d9e-103">Cmdlets do PowerShell pode ser útil, mas, a menos que os tópicos de ajuda explicar claramente o que o cmdlet faz e como usá-lo, o cmdlet não pode ser usado ou, ainda pior, ele pode frustrar utilizadores.</span><span class="sxs-lookup"><span data-stu-id="69d9e-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="69d9e-104">O formato de arquivo de ajuda do cmdlet baseado em XML melhora a consistência, mas necessita de grande ajuda muito mais.</span><span class="sxs-lookup"><span data-stu-id="69d9e-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="69d9e-105">Se nunca escreveu a ajuda do cmdlet, reveja as seguintes diretrizes.</span><span class="sxs-lookup"><span data-stu-id="69d9e-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="69d9e-106">O esquema XML necessário para criar o tópico de ajuda do cmdlet é descrito na secção seguinte.</span><span class="sxs-lookup"><span data-stu-id="69d9e-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="69d9e-107">Começar com [criando o arquivo de ajuda do Cmdlet](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="69d9e-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="69d9e-108">Esse tópico inclui uma descrição de nós XML de nível superior.</span><span class="sxs-lookup"><span data-stu-id="69d9e-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="69d9e-109">Diretrizes de escrita para a ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69d9e-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="69d9e-110">Escrever bem</span><span class="sxs-lookup"><span data-stu-id="69d9e-110">Write well</span></span>
<span data-ttu-id="69d9e-111">Nada substitui um tópico bem escrito.</span><span class="sxs-lookup"><span data-stu-id="69d9e-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="69d9e-112">Se não for um escritor profissional, localize um escritor ou o editor para ajudá-lo.</span><span class="sxs-lookup"><span data-stu-id="69d9e-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="69d9e-113">Outra alternativa é copiar o texto de ajuda no Microsoft Word e utilizar a gramática e ortografia verifica para melhorar o seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="69d9e-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="69d9e-114">Escrever simplesmente</span><span class="sxs-lookup"><span data-stu-id="69d9e-114">Write simply</span></span>
<span data-ttu-id="69d9e-115">Utilize palavras simples e expressões.</span><span class="sxs-lookup"><span data-stu-id="69d9e-115">Use simple words and phrases.</span></span>
<span data-ttu-id="69d9e-116">Evite jargão.</span><span class="sxs-lookup"><span data-stu-id="69d9e-116">Avoid jargon.</span></span>
<span data-ttu-id="69d9e-117">Considere que muitos leitores são equipados apenas com um dicionário em idiomas estrangeiros e seu tópico de ajuda.</span><span class="sxs-lookup"><span data-stu-id="69d9e-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="69d9e-118">Escrita de forma consistente</span><span class="sxs-lookup"><span data-stu-id="69d9e-118">Write consistently</span></span>
<span data-ttu-id="69d9e-119">Ajuda de cmdlets relacionados deve ser semelhantes (por exemplo, get-x e set-x).</span><span class="sxs-lookup"><span data-stu-id="69d9e-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="69d9e-120">Utiliza as descrições de standard para os parâmetros padrão, como **força** e **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="69d9e-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="69d9e-121">(Copiá-los de ajuda para os cmdlets de núcleo.) Utilize termos padrão.</span><span class="sxs-lookup"><span data-stu-id="69d9e-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="69d9e-122">Por exemplo, utilize "parâmetro", não ". o argumento" e utilização "cmdlet" não "comando" ou "command-let."</span><span class="sxs-lookup"><span data-stu-id="69d9e-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="69d9e-123">Inicie o sinopse com um verbo</span><span class="sxs-lookup"><span data-stu-id="69d9e-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="69d9e-124">O campo de sinopse informa o utilizador que o cmdlet não, o que é ou como ele funciona.</span><span class="sxs-lookup"><span data-stu-id="69d9e-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="69d9e-125">Verbos criar uma instrução baseado em tarefas que informa os utilizadores se este cmdlet cumpre os seus requisitos.</span><span class="sxs-lookup"><span data-stu-id="69d9e-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="69d9e-126">Utilize verbos de simples como "get", "Criar" e "alterar".</span><span class="sxs-lookup"><span data-stu-id="69d9e-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="69d9e-127">Evitar "set", que pode ser vaga e palavras bonitas como "Modificar".</span><span class="sxs-lookup"><span data-stu-id="69d9e-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="69d9e-128">Concentre-se em objetos</span><span class="sxs-lookup"><span data-stu-id="69d9e-128">Focus on objects</span></span>
<span data-ttu-id="69d9e-129">A maioria "get" cmdlets apresentar algo, mas sua função principal é obter um objeto.</span><span class="sxs-lookup"><span data-stu-id="69d9e-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="69d9e-130">Na sua ajuda, concentre-se no objeto, para que os utilizadores compreendam que a exibição padrão é uma das muitas e que pode utilizar os métodos e propriedades do objeto que obteve da-los de formas diferentes.</span><span class="sxs-lookup"><span data-stu-id="69d9e-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="69d9e-131">Escrever descrições detalhadas</span><span class="sxs-lookup"><span data-stu-id="69d9e-131">Write detailed descriptions</span></span>
<span data-ttu-id="69d9e-132">Liste resumidamente tudo o que o cmdlet pode fazer na descrição detalhada.</span><span class="sxs-lookup"><span data-stu-id="69d9e-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="69d9e-133">Se a função principal é alterar uma propriedade, mas o cmdlet pode alterar todas as propriedades, liste isso na descrição detalhada.</span><span class="sxs-lookup"><span data-stu-id="69d9e-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="69d9e-134">Utilize sintaxe convencional</span><span class="sxs-lookup"><span data-stu-id="69d9e-134">Use conventional syntax</span></span>
<span data-ttu-id="69d9e-135">Utilize o formato de Backus-Naur padrão que é comum para obter ajuda de linha de comando de UNIX e Windows.</span><span class="sxs-lookup"><span data-stu-id="69d9e-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="69d9e-136">Utilizar tipos de Microsoft .NET Framework para valores de parâmetro</span><span class="sxs-lookup"><span data-stu-id="69d9e-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="69d9e-137">Os marcadores de posição para valores de parâmetro (nas descrições de sintaxe e parâmetros) mostram os tipos do .NET Framework os objetos que o parâmetro aceitará.</span><span class="sxs-lookup"><span data-stu-id="69d9e-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="69d9e-138">A equipe de PowerShell desenvolveu essa convenção para o ajudar a ensinar aos utilizadores como o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69d9e-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="69d9e-139">Escrever descrições de parâmetros concluída</span><span class="sxs-lookup"><span data-stu-id="69d9e-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="69d9e-140">Descrições de parâmetros devem informar os utilizadores de duas coisas: o que o parâmetro não (seu efeito) e o que eles tem de escrever para os valores de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="69d9e-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="69d9e-141">Exemplos práticos de escrita</span><span class="sxs-lookup"><span data-stu-id="69d9e-141">Write practical examples</span></span>
<span data-ttu-id="69d9e-142">Os exemplos devem mostram como utilizar todos os parâmetros, mas o mais importante é mostrar como utilizar o cmdlet no mundo real de tarefas.</span><span class="sxs-lookup"><span data-stu-id="69d9e-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="69d9e-143">Começar com um exemplo simples e escrever os exemplos de cada vez mais complexos.</span><span class="sxs-lookup"><span data-stu-id="69d9e-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="69d9e-144">O exemplo final, mostre como utilizar o cmdlet num pipeline.</span><span class="sxs-lookup"><span data-stu-id="69d9e-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="69d9e-145">Utilize o campo de notas</span><span class="sxs-lookup"><span data-stu-id="69d9e-145">Use the Notes field</span></span>
<span data-ttu-id="69d9e-146">Utilize o campo de notas para explicar conceitos que os utilizadores precisam compreender o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="69d9e-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="69d9e-147">Também pode utilizar notas para ajudar os utilizadores a evitar erros comuns.</span><span class="sxs-lookup"><span data-stu-id="69d9e-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="69d9e-148">Evite URLs, à medida que eles mudam.</span><span class="sxs-lookup"><span data-stu-id="69d9e-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="69d9e-149">Em vez disso, forneça os termos de utilizadores a procurar.</span><span class="sxs-lookup"><span data-stu-id="69d9e-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="69d9e-150">Testar a sua ajuda</span><span class="sxs-lookup"><span data-stu-id="69d9e-150">Test your Help</span></span>
<span data-ttu-id="69d9e-151">Teste a ajuda, tal como testar o seu código.</span><span class="sxs-lookup"><span data-stu-id="69d9e-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="69d9e-152">Tenho amigos e colegas ler o conteúdo de ajuda e fornecem comentários.</span><span class="sxs-lookup"><span data-stu-id="69d9e-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="69d9e-153">Também pode solicitar comentários dos grupos de notícias.</span><span class="sxs-lookup"><span data-stu-id="69d9e-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="69d9e-154">Veja Também</span><span class="sxs-lookup"><span data-stu-id="69d9e-154">See Also</span></span>

 [<span data-ttu-id="69d9e-155">Como criar o ficheiro de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69d9e-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="69d9e-156">Como adicionar o nome do Cmdlet e o resumo para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69d9e-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="69d9e-157">Como adicionar a descrição detalhada para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69d9e-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="69d9e-158">Como adicionar a sintaxe para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69d9e-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="69d9e-159">Como adicionar parâmetros a um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69d9e-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="69d9e-160">Como adicionar tipos de entrada para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69d9e-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="69d9e-161">Como adicionar valores de retorno para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69d9e-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="69d9e-162">Como adicionar notas a um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69d9e-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="69d9e-163">Como adicionar exemplos para um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69d9e-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="69d9e-164">Como adicionar Links relacionados a um tópico de ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="69d9e-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="69d9e-165">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="69d9e-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)