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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847734"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>How to Add Examples to a Cmdlet Help Topic (Como Adicionar Exemplos ao Tópico de Ajuda de um Cmdlet)

- [Que precisa saber sobre exemplos de ajuda do Cmdlet](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [As vistas que apresentam exemplos de ajuda](#Help-Views-that-Display-Examples)

- [Adicionar um nó de exemplos](#Adding-an-Examples-Node)

- [Adicionar precedem](#Adding-Preceding-Characters)

- [Adicionar o comando](#Adding-the-Command)

- [Adicionar uma descrição](#Adding-a-Description)

- [Adicionar a saída de exemplo](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Que precisa saber sobre exemplos de ajuda do Cmdlet

- Liste todos os nomes de parâmetros no comando, mesmo quando os nomes de parâmetros são opcionais. Isto ajuda o usuário interpretar o comando facilmente.

- Evite aliases e nomes de parâmetro parcial, mesmo que trabalham em Windows PowerShell®.

- A descrição de exemplo, explico o rational para a construção do comando. Explique por que escolheu particulares parâmetros e valores, e como utilizar variáveis.

- Se o comando utilizar expressões, explicaremos em detalhes.

- Se o comando utiliza as propriedades e métodos de objetos, especialmente as propriedades que não aparecem na exibição padrão, utilize o exemplo de como uma oportunidade informar ao usuário sobre o objeto.

## <a name="help-views-that-display-examples"></a>As vistas que apresentam exemplos de ajuda

Exemplos aparecem apenas em modos de exibição detalhado e completo de ajuda do cmdlet.

## <a name="adding-an-examples-node"></a>Adicionar um nó de exemplos

O XML a seguir mostra como adicionar um nó de exemplos que contém um único nó de exemplo. Adicione nós de exemplo adicionais para cada exemplos que pretende incluir no tópico.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Adicionar um título de exemplo

O XML a seguir mostra como adicionar um título para o exemplo. O título é usado para definir o exemplo para além dos outros exemplos. Windows PowerShell® utiliza um padrão cabeçalho que inclui um conjunto de exemplo seqüencial.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Adicionar precedem

O XML a seguir mostra como adicionar caracteres, como a linha de comandos do Windows PowerShell, que são apresentados imediatamente antes do comando de exemplo (sem espaços intervenientes). Windows PowerShell® utiliza a linha de comandos do Windows PowerShell: C:\PS>.

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

## <a name="adding-the-command"></a>Adicionar o comando

O XML a seguir mostra como adicionar o comando real do exemplo. Ao adicionar o comando, digite o nome completo (não utilize alias) dos cmdlets e parâmetros. Além disso, utilize carateres minúsculos, sempre que possível.

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

## <a name="adding-a-description"></a>Adicionar uma descrição

O XML a seguir mostra como adicionar uma descrição para o exemplo. Windows PowerShell® utiliza um único conjunto de \<maml:para > com as etiquetas para a descrição, mesmo que vários \<maml:para > as etiquetas podem ser utilizadas.

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

## <a name="adding-example-output"></a>Adicionar a saída de exemplo

O XML a seguir mostra como adicionar a saída do comando. As informações de resultados do comando são opcionais, mas em alguns casos é útil demonstrar o efeito do uso de parâmetros específicos. Windows PowerShell® utiliza dois conjuntos de aplicação em branco \<maml:para > etiquetas para separar a saída do comando do comando.

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