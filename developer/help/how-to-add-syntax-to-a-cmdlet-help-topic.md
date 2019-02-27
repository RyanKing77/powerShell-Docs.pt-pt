---
title: Como adicionar a sintaxe para um tópico de ajuda do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 947d0c0188df5bba3a9fb617fe5abf0b3b28eb51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848210"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="1a6f1-102">How to Add Syntax to a Cmdlet Help Topic (Como Adicionar Sintaxe ao Tópico de Ajuda de um Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="1a6f1-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="1a6f1-103">Atributos de parâmetro</span><span class="sxs-lookup"><span data-stu-id="1a6f1-103">Parameter Attributes</span></span>](#Parameter-Attributes)

- [<span data-ttu-id="1a6f1-104">Atributos de valor de parâmetro</span><span class="sxs-lookup"><span data-stu-id="1a6f1-104">Parameter Value Attributes</span></span>](#Parameter-Value-Attributes)

- [<span data-ttu-id="1a6f1-105">Coletando informações de sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a6f1-105">Gathering Syntax Information</span></span>](#Gathering-Syntax-Information)

- [<span data-ttu-id="1a6f1-106">O diagrama da sintaxe XML de codificação</span><span class="sxs-lookup"><span data-stu-id="1a6f1-106">Coding the Syntax Diagram XML</span></span>](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a><span data-ttu-id="1a6f1-107">Que precisa saber sobre o diagrama de sintaxe na ajuda do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1a6f1-107">Things to Know About the Syntax Diagram in Cmdlet Help</span></span>

<span data-ttu-id="1a6f1-108">Antes de começar a programar o XML para o diagrama da sintaxe no ficheiro de ajuda do cmdlet, leia esta secção para obter uma visão clara do tipo de dados que tem de fornecer, como os atributos de parâmetro e como esses dados são apresentados no diagrama de sintaxe....</span><span class="sxs-lookup"><span data-stu-id="1a6f1-108">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="1a6f1-109">Atributos de parâmetro</span><span class="sxs-lookup"><span data-stu-id="1a6f1-109">Parameter Attributes</span></span>

- <span data-ttu-id="1a6f1-110">Necessária</span><span class="sxs-lookup"><span data-stu-id="1a6f1-110">Required</span></span>

  - <span data-ttu-id="1a6f1-111">Se for VERDADEIRO, o parâmetro tem de aparecer em todos os comandos que utilizam o conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-111">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="1a6f1-112">Se for FALSO, o parâmetro é opcional em todos os comandos que utilizam o conjunto de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-112">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="1a6f1-113">Posição</span><span class="sxs-lookup"><span data-stu-id="1a6f1-113">Position</span></span>

  - <span data-ttu-id="1a6f1-114">Se o nome, é necessário o nome de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-114">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="1a6f1-115">Se posicionais, o nome do parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-115">If positional, the parameter name is optional.</span></span> <span data-ttu-id="1a6f1-116">Quando ele for omitido, o valor do parâmetro tem de ser na posição especificada no comando.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-116">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="1a6f1-117">Por exemplo, se o valor for posição = "1", o valor do parâmetro tem de ser o primeiro ou o único sem nome de valor do parâmetro no comando.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-117">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="1a6f1-118">Entrada de pipeline</span><span class="sxs-lookup"><span data-stu-id="1a6f1-118">Pipeline Input</span></span>

  - <span data-ttu-id="1a6f1-119">Se for VERDADEIRO (ByValue), pode encaminhar a entrada para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-119">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="1a6f1-120">A entrada é associada com ("limite de") o parâmetro, mesmo se o nome da propriedade e o tipo de objeto não corresponde ao tipo esperado.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-120">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="1a6f1-121">O Windows PowerShell? componentes de enlace de parâmetro tentam converter a entrada para o tipo correto e falhar o comando apenas quando não é possível converter o tipo.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-121">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="1a6f1-122">Apenas um parâmetro num conjunto de parâmetros pode ser associado por valor.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="1a6f1-123">Se for VERDADEIRO (ByPropertyName), pode encaminhar a entrada para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-123">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="1a6f1-124">No entanto, a entrada é associada com o parâmetro apenas quando o nome do parâmetro corresponde ao nome de uma propriedade do objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-124">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="1a6f1-125">Por exemplo, se o nome do parâmetro é `Path`, objetos enviado por pipe ao cmdlet estão associados esse parâmetro apenas quando o objeto tem uma propriedade chamada caminho.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-125">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="1a6f1-126">Se true (ByValue, ByPropertyName), pode encaminhar entrada para o parâmetro por nome de propriedade ou por valor.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-126">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="1a6f1-127">Apenas um parâmetro num conjunto de parâmetros pode ser associado por valor.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-127">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="1a6f1-128">Se for FALSO, não é possível encaminhar entrada para este parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-128">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="1a6f1-129">Globbing</span><span class="sxs-lookup"><span data-stu-id="1a6f1-129">Globbing</span></span>

  - <span data-ttu-id="1a6f1-130">Se for VERDADEIRO, o texto que o utilizador escreve para o valor do parâmetro pode incluir carateres universais.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-130">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="1a6f1-131">Se for FALSO, o texto que o utilizador escreve para o valor do parâmetro não pode incluir carateres universais.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-131">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="1a6f1-132">Atributos de valor de parâmetro</span><span class="sxs-lookup"><span data-stu-id="1a6f1-132">Parameter Value Attributes</span></span>

- <span data-ttu-id="1a6f1-133">Necessária</span><span class="sxs-lookup"><span data-stu-id="1a6f1-133">Required</span></span>

  - <span data-ttu-id="1a6f1-134">Se for VERDADEIRO, o valor especificado tem de ser utilizado sempre que com o parâmetro de um comando.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-134">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="1a6f1-135">Se for FALSO, o valor do parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-135">If false, the parameter value is optional.</span></span> <span data-ttu-id="1a6f1-136">Normalmente, um valor é opcional, apenas quando ele é um dos vários valores válidos para um parâmetro, tal como num tipo enumerado.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-136">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="1a6f1-137">O atributo necessário de um valor de parâmetro é diferente do atributo necessário de um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-137">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="1a6f1-138">O atributo necessário de um parâmetro indica se o parâmetro (e o respetivo valor) tem de ser incluídos ao invocar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-138">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="1a6f1-139">Por outro lado, o atributo necessário de um valor de parâmetro é utilizado apenas quando o parâmetro está incluído no comando.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-139">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="1a6f1-140">Indica se esse valor específico deve ser utilizada com o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-140">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="1a6f1-141">Normalmente, os valores de parâmetros que são espaços reservados são necessários e os valores de parâmetros que são literais não são necessários, porque eles são um dos vários valores que podem ser usadas com o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-141">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="1a6f1-142">Coletando informações de sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a6f1-142">Gathering Syntax Information</span></span>

1. <span data-ttu-id="1a6f1-143">Comece com o nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-143">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="1a6f1-144">Liste todos os parâmetros do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-144">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="1a6f1-145">Escreva um travessão (também conhecido como "dash" ou "sinal de subtração" (ASCII 45) antes de cada nome de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-145">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="1a6f1-146">Separe os parâmetros em conjuntos de parâmetros (alguns cmdlets pode ter apenas um parâmetro definido).</span><span class="sxs-lookup"><span data-stu-id="1a6f1-146">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="1a6f1-147">Neste exemplo, Get-Tech cmdlet tem dois conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-147">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="1a6f1-148">Inicie cada parâmetro definido com o nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-148">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="1a6f1-149">Liste o parâmetro de padrão definido pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-149">List the default parameter set first.</span></span> <span data-ttu-id="1a6f1-150">O parâmetro predefinido é especificado pela classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-150">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="1a6f1-151">Para cada conjunto de parâmetros, liste o parâmetro exclusivo em primeiro lugar, a menos que haja parâmetros posicionais que devem aparecer primeiro.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-151">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="1a6f1-152">No exemplo anterior, os parâmetros de nome e ID são parâmetros exclusivos para os dois conjuntos de parâmetro (cada conjunto de parâmetros tem de ter um parâmetro que é exclusivo para esse conjunto de parâmetros).</span><span class="sxs-lookup"><span data-stu-id="1a6f1-152">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="1a6f1-153">Isto torna mais fácil para os utilizadores a identificar quais parâmetro que precisam fornecer para o parâmetro definido.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-153">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="1a6f1-154">Liste os parâmetros na ordem em que devem ser apresentadas no comando.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-154">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="1a6f1-155">Se a ordem não importa, lista os parâmetros relacionados em conjunto ou lista os parâmetros mais usados pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-155">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="1a6f1-156">Certifique-se de que lista os parâmetros WhatIf e confirmar se o cmdlet oferece suporte a ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-156">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="1a6f1-157">Não é liste os parâmetros comuns (por exemplo, verboso, depuração e ErrorAction) no seu diagrama da sintaxe.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-157">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="1a6f1-158">O `Get-Help` cmdlet adiciona essa informação para quando ele exibe o tópico de ajuda.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-158">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="1a6f1-159">Adicione os valores de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-159">Add the parameter values.</span></span> <span data-ttu-id="1a6f1-160">No Windows PowerShell?, os valores de parâmetro são representados por tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-160">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="1a6f1-161">No entanto, o nome do tipo pode ser abreviado, como "string" para System. String.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-161">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="1a6f1-162">Abreviar tipos, desde que seu significado é claro, como "string" para System. String e "int" para System.Int32.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-162">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="1a6f1-163">Listar todos os valores de enumerações, tais como o - parâmetro de tipo no exemplo anterior, o pode ser definido como "básico" ou "avançada".</span><span class="sxs-lookup"><span data-stu-id="1a6f1-163">List all values of enumerations, such as the -type parameter in the previous example, wich can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="1a6f1-164">Comutador de parâmetros, como - lista no exemplo anterior, não têm valores.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-164">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="1a6f1-165">Adicione os colchetes angulares a valores de parâmetros que são o marcador de posição, em comparação com os valores de parâmetros que são literais.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-165">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="1a6f1-166">Coloque os parâmetros opcionais e seus valores em parênteses Retos.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-166">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="1a6f1-167">Coloque os nomes de parâmetros opcionais (para parâmetros posicionais) entre parêntesis Retos.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-167">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="1a6f1-168">O nome para os parâmetros que são posicional, como o parâmetro de nome no exemplo a seguir, tem de ser incluído no comando.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-168">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="1a6f1-169">Se um valor de parâmetro pode conter vários valores, como uma lista de nomes no parâmetro Name, adicione um par de colchetes, logo a seguir o valor do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-169">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="1a6f1-170">Se o utilizador pode escolher entre os valores de parâmetro ou parâmetros, como o parâmetro de tipo, coloque as opções de colchetes e separá-los com o symbol(;) OR exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-170">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="1a6f1-171">Se o valor do parâmetro tem de utilizar formatação específicas, como aspas ou parênteses, mostram o formato na sintaxe.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-171">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="1a6f1-172">O diagrama da sintaxe XML de codificação</span><span class="sxs-lookup"><span data-stu-id="1a6f1-172">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="1a6f1-173">O nó de sintaxe do XML começa imediatamente após o nó de descrição, que termina com o \</maml:description > etiqueta.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-173">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="1a6f1-174">Para obter informações sobre a recolha de dados utilizados no diagrama da sintaxe, consulte [recolha informações de sintaxe](#Gathering-Syntax-Information).</span><span class="sxs-lookup"><span data-stu-id="1a6f1-174">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#Gathering-Syntax-Information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="1a6f1-175">Adicionar um nó de sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a6f1-175">Adding a Syntax Node</span></span>

<span data-ttu-id="1a6f1-176">O diagrama da sintaxe apresentado no tópico de ajuda do cmdlet é gerado a partir de dados no nó de sintaxe do XML.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-176">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="1a6f1-177">O nó de sintaxe está entre um par se \<: sintaxe de comando > etiquetas.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-177">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="1a6f1-178">Com cada conjunto de parâmetros do cmdlet deve estar entre um par de \<comando: syntaxitem > etiquetas.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-178">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="1a6f1-179">Não há limite para o número de \<comando: syntaxitem > etiquetas que podem ser adicionados.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-179">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="1a6f1-180">O exemplo seguinte mostra um nó de sintaxe connosco de item de sintaxe para dois conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-180">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="1a6f1-181">Adicionar o nome do Cmdlet para o parâmetro de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="1a6f1-181">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="1a6f1-182">Cada conjunto de parâmetros do cmdlet é especificado num nó de item de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-182">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="1a6f1-183">Cada nó de item de sintaxe começa com um par de \<maml:name > etiquetas que incluem o nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-183">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="1a6f1-184">O exemplo seguinte inclui um nó de sintaxe connosco de item de sintaxe para dois conjuntos de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-184">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a><span data-ttu-id="1a6f1-185">Adicionar parâmetros</span><span class="sxs-lookup"><span data-stu-id="1a6f1-185">Adding Parameters</span></span>

<span data-ttu-id="1a6f1-186">Cada parâmetro adicionado ao nó de item de sintaxe é especificado dentro de um par de \<: parâmetro de comando > etiquetas.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-186">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="1a6f1-187">Precisa de um par de \<: parâmetro de comando > etiquetas para cada parâmetro incluído no conjunto de parâmetros, com exceção dos parâmetros comuns que são fornecidos pelo Windows PowerShell?.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-187">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="1a6f1-188">Os atributos da abertura \<: parâmetro de comando > etiqueta determinar como o parâmetro é exibido no diagrama de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-188">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="1a6f1-189">Para obter informações sobre os atributos de parâmetro, consulte [atributos de parâmetro](#Parameter-Attributes).</span><span class="sxs-lookup"><span data-stu-id="1a6f1-189">For information on parameter attributes, see [Parameter Attributes](#Parameter-Attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="1a6f1-190">O \<: parâmetro de comando > etiqueta suporta um elemento subordinado \<maml:description > cujo conteúdo jamais é exibido.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-190">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="1a6f1-191">As descrições de parâmetro são especificadas no nó de parâmetro do XML.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-191">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="1a6f1-192">Para evitar inconsistências entre as informações no item de sintaxe bodes e o nó de parâmetro, omita o (\<maml:description > ou deixe vazio.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-192">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="1a6f1-193">O exemplo seguinte inclui um nó de item de sintaxe para um parâmetro definido com dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="1a6f1-193">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
