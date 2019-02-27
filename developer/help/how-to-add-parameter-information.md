---
title: Como adicionar informações de parâmetro | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851941"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="cc8ac-102">How to Add Parameter Information (Como Adicionar Informações de Parâmetro)</span><span class="sxs-lookup"><span data-stu-id="cc8ac-102">How to Add Parameter Information</span></span>

<span data-ttu-id="cc8ac-103">Esta secção descreve como adicionar o conteúdo que é apresentado na secção parâmetros do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="cc8ac-104">A secção de parâmetros do tópico de ajuda lista cada um dos parâmetros do cmdlet e fornece uma descrição detalhada de cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="cc8ac-105">O conteúdo da secção de parâmetros deve ser consistente com o conteúdo da seção de sintaxe de tópico de ajuda.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="cc8ac-106">É da responsabilidade do autor ajuda para se certificar de que a sintaxe e os parâmetros de nó contêm elementos similares do XML.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="cc8ac-107">Para obter uma visão completa de um arquivo de ajuda, abra de um dos ficheiros dll Help.xml localizado no diretório de instalação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="cc8ac-108">Por exemplo, o ficheiro de Microsoft.PowerShell.Commands.Management.dll Help.xml contém conteúdo para vários dos cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="cc8ac-109">Para adicionar parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc8ac-109">To Add Parameters</span></span>

1. <span data-ttu-id="cc8ac-110">Abra o ficheiro de ajuda do cmdlet e localize o nó de comando para o cmdlet que está documentando.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="cc8ac-111">Se estiver a adicionar um novo cmdlet terá de criar um novo nó de comando.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="cc8ac-112">O ficheiro de ajuda conterá um nó de comando para cada cmdlet que está a fornecer conteúdo de ajuda.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="cc8ac-113">Eis um exemplo de um nó de comando em branco.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="cc8ac-114">No nó de comando, localize o nó de descrição e adicionar um nó de parâmetros, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="cc8ac-115">É permitido apenas um nó de parâmetros e imediatamente deve seguir o nó de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="cc8ac-116">No nó de parâmetros, adicione um nó de parâmetro para cada parâmetro do cmdlet, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="cc8ac-117">Neste exemplo, é adicionado um nó de parâmetro para três parâmetros.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="cc8ac-118">Uma vez que estas são as mesmas etiquetas XML que são utilizadas no nó de sintaxe e porque os parâmetros especificados aqui tem de coincidir com os parâmetros especificados pelo nó de sintaxe, pode copiar os nós de parâmetro a partir do nó de sintaxe e cole-os para o nó de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="cc8ac-119">No entanto, certifique-se de que apenas uma instância de um nó de parâmetro de copiar, mesmo que o parâmetro for especificado no parâmetro vários define na sintaxe.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="cc8ac-120">Para cada nó de parâmetro, defina os valores de atributos que definem as características de cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="cc8ac-121">Esses atributos incluem o seguinte: obrigatório, globbing pipelineinput e posição.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. <span data-ttu-id="cc8ac-122">Para cada nó de parâmetro, adicione o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="cc8ac-123">Eis um exemplo do nome do parâmetro adicionado ao nó de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="cc8ac-124">Para cada nó de parâmetro, adicione a descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="cc8ac-125">Eis um exemplo da descrição do parâmetro adicionado ao nó de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-125">Here is an example of the parameter description added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. <span data-ttu-id="cc8ac-126">Para cada nó de parâmetro, adicione o tipo de .NET Framework do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="cc8ac-127">O tipo de parâmetro é apresentado juntamente com o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="cc8ac-128">Eis um exemplo do tipo de .NET Framework parâmetro adicionado ao nó de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. <span data-ttu-id="cc8ac-129">Para cada nó de parâmetro, adicione o valor predefinido do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="cc8ac-130">A seguinte sentença é adicionada para a descrição do parâmetro quando o conteúdo é apresentado: "DefaultValue" é a predefinição.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="cc8ac-131">Eis um exemplo do valor predefinido do parâmetro é adicionado ao nó de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. <span data-ttu-id="cc8ac-132">Para cada parâmetro que tem vários valores, adicione um nó de valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="cc8ac-133">Eis um exemplo do de um nó de valores possíveis que define dois valores possíveis para o parâmetro</span><span class="sxs-lookup"><span data-stu-id="cc8ac-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

<span data-ttu-id="cc8ac-134">Eis algumas coisas a serem lembradas ao adicionar parâmetros.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="cc8ac-135">Os atributos do parâmetro não são apresentados em todas as vistas do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="cc8ac-136">No entanto, elas são exibidas numa tabela a seguir a descrição de parâmetro quando o usuário solicitar o completo (Get-Help \<cmdletname >-completa) ou parâmetro (Get-Help \<cmdletname >-parâmetro) modo de exibição do tópico.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="cc8ac-137">A descrição do parâmetro é uma das partes mais importantes de um tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="cc8ac-138">A descrição deve ser breve, bem como completa.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="cc8ac-139">Além disso, lembre-se de que se a descrição do parâmetro ficar demasiado longa, por exemplo, quando os dois parâmetros interagem entre si, pode adicionar mais conteúdos na secção de notas do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="cc8ac-140">A descrição do parâmetro fornece dois tipos de informações.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="cc8ac-141">O que o cmdlet faz quando o parâmetro é utilizado.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="cc8ac-142">É que um valor válido para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="cc8ac-143">Uma vez que os valores de parâmetro são expressos como objetos do .NET Framework, os utilizadores precisam de mais informações sobre estes valores do que fariam numa ajuda de linha de comando tradicional.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="cc8ac-144">Informar ao usuário que tipo de dados, o parâmetro foi concebido para aceitar e incluem exemplos.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="cc8ac-145">O valor predefinido do parâmetro é o valor que é utilizado se o parâmetro não for especificado na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="cc8ac-146">Tenha em atenção que o valor predefinido é opcional e não é necessária para alguns parâmetros, tais como parâmetros necessários.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="cc8ac-147">No entanto, deve especificar um valor predefinido para a maioria dos parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="cc8ac-148">O valor predefinido ajuda o usuário para compreender o efeito de não utilizar o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="cc8ac-149">Descreva muito especificamente, o valor predefinido, como o "diretório atual" ou "Windows PowerShell diretório de instalação ($pshome)" para um caminho opcional.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="cc8ac-150">Também pode escrever uma sentença que descreve o padrão, como a seguinte sentença usada para o `PassThru` parâmetro: "Se não for especificado PassThru, o cmdlet não passa objetos pelo pipeline."</span><span class="sxs-lookup"><span data-stu-id="cc8ac-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="cc8ac-151">Além disso, uma vez que o valor é apresentado oposta ao nome do campo "**valor predefinido**", não é necessário incluir o termo "valor predefinido" na entrada.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="cc8ac-152">O valor predefinido do parâmetro não é apresentado em todas as vistas do tópico de ajuda do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="cc8ac-153">No entanto, é apresentado numa tabela (juntamente com os atributos de parâmetro) a seguir a descrição de parâmetro quando o usuário solicitar o completo (Get-Help \<cmdletname >-completa) ou o parâmetro (Get-Help \<cmdletname >-parâmetro) vista o tópico.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="cc8ac-154">O XML a seguir mostra um par de `<dev:defaultValue>` marcas adicionadas para o `<command:parameter>` nó.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="cc8ac-155">Tenha em atenção que o valor predefinido segue imediatamente após o fecho `</command:parameterValue>` tag (quando o valor do parâmetro for especificado) ou o fechamento `</maml:description>` etiqueta da descrição do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="cc8ac-156">nome.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-156">name.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

<span data-ttu-id="cc8ac-157">Adicione os valores para tipos enumerados</span><span class="sxs-lookup"><span data-stu-id="cc8ac-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="cc8ac-158">Se o parâmetro tem vários valores ou valores de um tipo enumerado, pode usar opcional \<dev:possibleValues > nó.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="cc8ac-159">Este nó permite-lhe especificar um nome e descrição para valores múltiplos.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="cc8ac-160">Lembre-se de que as descrições dos valores enumerados não aparecem em qualquer uma da predefinição apresentados pelo modos de exibição da ajuda a `Get-Help` cmdlet, mas outros visualizadores de ajuda podem ser apresentado este conteúdo em suas exibições.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="cc8ac-161">O XML a seguir mostra um `<dev:possibleValues>` nó com dois valores especificados.</span><span class="sxs-lookup"><span data-stu-id="cc8ac-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```