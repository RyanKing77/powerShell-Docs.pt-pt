---
title: Como adicionar devolver valores para um tópico de ajuda do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849218"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>How to Add Return Values to a Cmdlet Help Topic (Como Adicionar Valores Devolvidos ao Tópico de Ajuda de um Cmdlet)

Esta secção descreve como adicionar uma secção de saídas para um tópico de ajuda do cmdlet Windows PowerShell®. A secção de saídas lista as classes do .NET de objetos que o cmdlet Devolve ou passa pelo pipeline.

Não existe nenhum limite para o número de classes que podem ser adicionados para a secção de saídas. Os tipos de retornados de um cmdlet encontram-se entre uma \<comando: returnValues > nó, com cada classe deve estar entre um \<comando: returnValue > elemento.

Se um cmdlet não gera quaisquer dados, utilize esta secção para indicar que não existe nenhuma saída. Por exemplo, em vez do nome de classe, escrever "None" e fornecer uma breve explicação. Se o cmdlet gera saída condicionalmente, utilize este nó para explicar as condições e descrever o resultado condicional.

O esquema inclui dois \<maml:description > elementos em cada \<comando: returnValue > elemento. No entanto, o `Get-Help` cmdlet apresenta apenas o conteúdo do \<comando: returnValue > /\<maml:description > elemento.

A partir do Windows PowerShell 3.0, o `Get-Help` cmdlet apresenta o conteúdo do \<maml:uri > elemento. Esse elemento permite-lhe direcionar os utilizadores para tópicos que descrevem a classe do .NET.

O XML a seguir mostra o \<maml:returnValues > nó.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

O XML a seguir mostra um exemplo de como utilizar o \<maml:returnValues > nó documentar um tipo de saída.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



