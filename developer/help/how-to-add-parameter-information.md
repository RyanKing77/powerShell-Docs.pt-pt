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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083370"
---
# <a name="how-to-add-parameter-information"></a>How to Add Parameter Information (Como Adicionar Informações de Parâmetro)

Esta secção descreve como adicionar o conteúdo que é apresentado na secção parâmetros do tópico de ajuda do cmdlet. A secção de parâmetros do tópico de ajuda lista cada um dos parâmetros do cmdlet e fornece uma descrição detalhada de cada parâmetro.

O conteúdo da secção de parâmetros deve ser consistente com o conteúdo da seção de sintaxe de tópico de ajuda. É da responsabilidade do autor ajuda para se certificar de que a sintaxe e os parâmetros de nó contêm elementos similares do XML.

> [!NOTE]
> Para obter uma visão completa de um arquivo de ajuda, abra de um dos ficheiros dll Help.xml localizado no diretório de instalação do Windows PowerShell. Por exemplo, o ficheiro de Microsoft.PowerShell.Commands.Management.dll Help.xml contém conteúdo para vários dos cmdlets do Windows PowerShell.

### <a name="to-add-parameters"></a>Para adicionar parâmetros

1. Abra o ficheiro de ajuda do cmdlet e localize o nó de comando para o cmdlet que está documentando. Se estiver a adicionar um novo cmdlet terá de criar um novo nó de comando. O ficheiro de ajuda conterá um nó de comando para cada cmdlet que está a fornecer conteúdo de ajuda. Eis um exemplo de um nó de comando em branco.

    ```xml
    <command:command>
    </command:command>
    ```

2. No nó de comando, localize o nó de descrição e adicionar um nó de parâmetros, conforme mostrado abaixo. É permitido apenas um nó de parâmetros e imediatamente deve seguir o nó de sintaxe.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. No nó de parâmetros, adicione um nó de parâmetro para cada parâmetro do cmdlet, conforme mostrado abaixo.

   Neste exemplo, é adicionado um nó de parâmetro para três parâmetros.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Uma vez que estas são as mesmas etiquetas XML que são utilizadas no nó de sintaxe e porque os parâmetros especificados aqui tem de coincidir com os parâmetros especificados pelo nó de sintaxe, pode copiar os nós de parâmetro a partir do nó de sintaxe e cole-os para o nó de parâmetros. No entanto, certifique-se de que apenas uma instância de um nó de parâmetro de copiar, mesmo que o parâmetro for especificado no parâmetro vários define na sintaxe.

4. Para cada nó de parâmetro, defina os valores de atributos que definem as características de cada parâmetro. Esses atributos incluem o seguinte: obrigatório, globbing pipelineinput e posição.

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

5. Para cada nó de parâmetro, adicione o nome do parâmetro. Eis um exemplo do nome do parâmetro adicionado ao nó de parâmetro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Para cada nó de parâmetro, adicione a descrição do parâmetro. Eis um exemplo da descrição do parâmetro adicionado ao nó de parâmetro.

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

7. Para cada nó de parâmetro, adicione o tipo de .NET Framework do parâmetro. O tipo de parâmetro é apresentado juntamente com o nome do parâmetro.

   Eis um exemplo do tipo de .NET Framework parâmetro adicionado ao nó de parâmetro.

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

8. Para cada nó de parâmetro, adicione o valor predefinido do parâmetro. A seguinte sentença é adicionada para a descrição do parâmetro quando o conteúdo é apresentado: "DefaultValue" é a predefinição.

   Eis um exemplo do valor predefinido do parâmetro é adicionado ao nó de parâmetro.

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

9. Para cada parâmetro que tem vários valores, adicione um nó de valores possíveis.

   Eis um exemplo do de um nó de valores possíveis que define dois valores possíveis para o parâmetro

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

Eis algumas coisas a serem lembradas ao adicionar parâmetros.

- Os atributos do parâmetro não são apresentados em todas as vistas do tópico de ajuda do cmdlet. No entanto, elas são exibidas numa tabela a seguir a descrição de parâmetro quando o usuário solicitar o completo (Get-Help \<cmdletname >-completa) ou parâmetro (Get-Help \<cmdletname >-parâmetro) modo de exibição do tópico.

- A descrição do parâmetro é uma das partes mais importantes de um tópico de ajuda do cmdlet. A descrição deve ser breve, bem como completa. Além disso, lembre-se de que se a descrição do parâmetro ficar demasiado longa, por exemplo, quando os dois parâmetros interagem entre si, pode adicionar mais conteúdos na secção de notas do tópico de ajuda do cmdlet.

  A descrição do parâmetro fornece dois tipos de informações.

- O que o cmdlet faz quando o parâmetro é utilizado.

- É que um valor válido para o parâmetro.

- Uma vez que os valores de parâmetro são expressos como objetos do .NET Framework, os utilizadores precisam de mais informações sobre estes valores do que fariam numa ajuda de linha de comando tradicional. Informar ao usuário que tipo de dados, o parâmetro foi concebido para aceitar e incluem exemplos.

O valor predefinido do parâmetro é o valor que é utilizado se o parâmetro não for especificado na linha de comandos. Tenha em atenção que o valor predefinido é opcional e não é necessária para alguns parâmetros, tais como parâmetros necessários. No entanto, deve especificar um valor predefinido para a maioria dos parâmetros opcionais.

O valor predefinido ajuda o usuário para compreender o efeito de não utilizar o parâmetro. Descreva muito especificamente, o valor predefinido, como o "diretório atual" ou "Windows PowerShell diretório de instalação ($pshome)" para um caminho opcional. Também pode escrever uma sentença que descreve o padrão, como a seguinte sentença usada para o `PassThru` parâmetro: "Se não for especificado PassThru, o cmdlet não passa objetos pelo pipeline."  Além disso, uma vez que o valor é apresentado oposta ao nome do campo "**valor predefinido**", não é necessário incluir o termo "valor predefinido" na entrada.

O valor predefinido do parâmetro não é apresentado em todas as vistas do tópico de ajuda do cmdlet. No entanto, é apresentado numa tabela (juntamente com os atributos de parâmetro) a seguir a descrição de parâmetro quando o usuário solicitar o completo (Get-Help \<cmdletname >-completa) ou o parâmetro (Get-Help \<cmdletname >-parâmetro) vista o tópico.

O XML a seguir mostra um par de `<dev:defaultValue>` marcas adicionadas para o `<command:parameter>` nó. Tenha em atenção que o valor predefinido segue imediatamente após o fecho `</command:parameterValue>` tag (quando o valor do parâmetro for especificado) ou o fechamento `</maml:description>` etiqueta da descrição do parâmetro. nome.

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

Adicione os valores para tipos enumerados

Se o parâmetro tem vários valores ou valores de um tipo enumerado, pode usar opcional \<dev:possibleValues > nó. Este nó permite-lhe especificar um nome e descrição para valores múltiplos.

Lembre-se de que as descrições dos valores enumerados não aparecem em qualquer uma da predefinição apresentados pelo modos de exibição da ajuda a `Get-Help` cmdlet, mas outros visualizadores de ajuda podem ser apresentado este conteúdo em suas exibições.

O XML a seguir mostra um `<dev:possibleValues>` nó com dois valores especificados.

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