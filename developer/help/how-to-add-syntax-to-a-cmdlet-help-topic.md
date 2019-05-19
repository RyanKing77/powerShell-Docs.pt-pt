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
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855140"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>How to Add Syntax to a Cmdlet Help Topic (Como Adicionar Sintaxe ao Tópico de Ajuda de um Cmdlet)

Antes de começar a programar o XML para o diagrama da sintaxe no ficheiro de ajuda do cmdlet, leia esta secção para obter uma visão clara do tipo de dados que tem de fornecer, como os atributos de parâmetro e como esses dados são apresentados no diagrama de sintaxe....

### <a name="parameter-attributes"></a>Atributos de parâmetro

- Necessária

  - Se for VERDADEIRO, o parâmetro tem de aparecer em todos os comandos que utilizam o conjunto de parâmetros.

  - Se for FALSO, o parâmetro é opcional em todos os comandos que utilizam o conjunto de parâmetros.

- Posição

  - Se o nome, é necessário o nome de parâmetro.

  - Se posicionais, o nome do parâmetro é opcional. Quando ele for omitido, o valor do parâmetro tem de ser na posição especificada no comando. Por exemplo, se o valor for posição = "1", o valor do parâmetro tem de ser o primeiro ou o único sem nome de valor do parâmetro no comando.

- Entrada de pipeline

  - Se for VERDADEIRO (ByValue), pode encaminhar a entrada para o parâmetro. A entrada é associada com ("limite de") o parâmetro, mesmo se o nome da propriedade e o tipo de objeto não corresponde ao tipo esperado. O Windows PowerShell? componentes de enlace de parâmetro tentam converter a entrada para o tipo correto e falhar o comando apenas quando não é possível converter o tipo. Apenas um parâmetro num conjunto de parâmetros pode ser associado por valor.

  - Se for VERDADEIRO (ByPropertyName), pode encaminhar a entrada para o parâmetro. No entanto, a entrada é associada com o parâmetro apenas quando o nome do parâmetro corresponde ao nome de uma propriedade do objeto de entrada. Por exemplo, se o nome do parâmetro é `Path`, objetos enviado por pipe ao cmdlet estão associados esse parâmetro apenas quando o objeto tem uma propriedade chamada caminho.

  - Se true (ByValue, ByPropertyName), pode encaminhar entrada para o parâmetro por nome de propriedade ou por valor. Apenas um parâmetro num conjunto de parâmetros pode ser associado por valor.

  - Se for FALSO, não é possível encaminhar entrada para este parâmetro.

- Globbing

  - Se for VERDADEIRO, o texto que o utilizador escreve para o valor do parâmetro pode incluir carateres universais.

  - Se for FALSO, o texto que o utilizador escreve para o valor do parâmetro não pode incluir carateres universais.

### <a name="parameter-value-attributes"></a>Atributos de valor de parâmetro

- Necessária

  - Se for VERDADEIRO, o valor especificado tem de ser utilizado sempre que com o parâmetro de um comando.

  - Se for FALSO, o valor do parâmetro é opcional. Normalmente, um valor é opcional, apenas quando ele é um dos vários valores válidos para um parâmetro, tal como num tipo enumerado.

O atributo necessário de um valor de parâmetro é diferente do atributo necessário de um parâmetro.

O atributo necessário de um parâmetro indica se o parâmetro (e o respetivo valor) tem de ser incluídos ao invocar o cmdlet. Por outro lado, o atributo necessário de um valor de parâmetro é utilizado apenas quando o parâmetro está incluído no comando. Indica se esse valor específico deve ser utilizada com o parâmetro.

Normalmente, os valores de parâmetros que são espaços reservados são necessários e os valores de parâmetros que são literais não são necessários, porque eles são um dos vários valores que podem ser usadas com o parâmetro.

### <a name="gathering-syntax-information"></a>Coletando informações de sintaxe

1. Comece com o nome do cmdlet.

   ```
   SYNTAX
       Get-Tech
   ```

2. Liste todos os parâmetros do cmdlet. Escreva um travessão (também conhecido como "dash" ou "sinal de subtração" (ASCII 45) antes de cada nome de parâmetro. Separe os parâmetros em conjuntos de parâmetros (alguns cmdlets pode ter apenas um parâmetro definido). Neste exemplo, Get-Tech cmdlet tem dois conjuntos de parâmetros.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Inicie cada parâmetro definido com o nome do cmdlet.

   Liste o parâmetro de padrão definido pela primeira vez. O parâmetro predefinido é especificado pela classe cmdlet.

   Para cada conjunto de parâmetros, liste o parâmetro exclusivo em primeiro lugar, a menos que haja parâmetros posicionais que devem aparecer primeiro. No exemplo anterior, os parâmetros de nome e ID são parâmetros exclusivos para os dois conjuntos de parâmetro (cada conjunto de parâmetros tem de ter um parâmetro que é exclusivo para esse conjunto de parâmetros). Isto torna mais fácil para os utilizadores a identificar quais parâmetro que precisam fornecer para o parâmetro definido.

   Liste os parâmetros na ordem em que devem ser apresentadas no comando. Se a ordem não importa, lista os parâmetros relacionados em conjunto ou lista os parâmetros mais usados pela primeira vez.

   Certifique-se de que lista os parâmetros WhatIf e confirmar se o cmdlet oferece suporte a ShouldProcess.

   Não é liste os parâmetros comuns (por exemplo, verboso, depuração e ErrorAction) no seu diagrama da sintaxe. O `Get-Help` cmdlet adiciona essa informação para quando ele exibe o tópico de ajuda.

3. Adicione os valores de parâmetro. No Windows PowerShell?, os valores de parâmetro são representados por tipo .NET. No entanto, o nome do tipo pode ser abreviado, como "string" para System. String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Abreviar tipos, desde que seu significado é claro, como "string" para System. String e "int" para System.Int32.

   Lista de todos os valores de enumerações, como o - parâmetro de tipo no exemplo anterior, que pode ser definido como "básico" ou "avançada".

   Comutador de parâmetros, como - lista no exemplo anterior, não têm valores.

4. Adicione os colchetes angulares a valores de parâmetros que são o marcador de posição, em comparação com os valores de parâmetros que são literais.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Coloque os parâmetros opcionais e seus valores em parênteses Retos.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Coloque os nomes de parâmetros opcionais (para parâmetros posicionais) entre parêntesis Retos. O nome para os parâmetros que são posicional, como o parâmetro de nome no exemplo a seguir, tem de ser incluído no comando.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Se um valor de parâmetro pode conter vários valores, como uma lista de nomes no parâmetro Name, adicione um par de colchetes, logo a seguir o valor do parâmetro.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Se o utilizador pode escolher entre os valores de parâmetro ou parâmetros, como o parâmetro de tipo, coloque as opções de colchetes e separá-los com o symbol(;) OR exclusivo.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Se o valor do parâmetro tem de utilizar formatação específicas, como aspas ou parênteses, mostram o formato na sintaxe.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>O diagrama da sintaxe XML de codificação

O nó de sintaxe do XML começa imediatamente após o nó de descrição, que termina com o \</maml:description > etiqueta. Para obter informações sobre a recolha de dados utilizados no diagrama da sintaxe, consulte [recolha informações de sintaxe](#gathering-syntax-information).

### <a name="adding-a-syntax-node"></a>Adicionar um nó de sintaxe

O diagrama da sintaxe apresentado no tópico de ajuda do cmdlet é gerado a partir de dados no nó de sintaxe do XML. O nó de sintaxe está entre um par se \<: sintaxe de comando > etiquetas. Com cada conjunto de parâmetros do cmdlet deve estar entre um par de \<comando: syntaxitem > etiquetas. Não há limite para o número de \<comando: syntaxitem > etiquetas que podem ser adicionados.

O exemplo seguinte mostra um nó de sintaxe connosco de item de sintaxe para dois conjuntos de parâmetros.

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Adicionar o nome do Cmdlet para o parâmetro de conjunto de dados

Cada conjunto de parâmetros do cmdlet é especificado num nó de item de sintaxe. Cada nó de item de sintaxe começa com um par de \<maml:name > etiquetas que incluem o nome do cmdlet.

O exemplo seguinte inclui um nó de sintaxe connosco de item de sintaxe para dois conjuntos de parâmetros.

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

### <a name="adding-parameters"></a>Adicionar parâmetros

Cada parâmetro adicionado ao nó de item de sintaxe é especificado dentro de um par de \<: parâmetro de comando > etiquetas. Precisa de um par de \<: parâmetro de comando > etiquetas para cada parâmetro incluído no conjunto de parâmetros, com exceção dos parâmetros comuns que são fornecidos pelo Windows PowerShell?.

Os atributos da abertura \<: parâmetro de comando > etiqueta determinar como o parâmetro é exibido no diagrama de sintaxe. Para obter informações sobre os atributos de parâmetro, consulte [atributos de parâmetro](#parameter-attributes).

> [!NOTE]
> O \<: parâmetro de comando > etiqueta suporta um elemento subordinado \<maml:description > cujo conteúdo jamais é exibido. As descrições de parâmetro são especificadas no nó de parâmetro do XML. Para evitar inconsistências entre as informações no item de sintaxe bodes e o nó de parâmetro, omita o (\<maml:description > ou deixe vazio.

O exemplo seguinte inclui um nó de item de sintaxe para um parâmetro definido com dois parâmetros.

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
