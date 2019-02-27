---
title: Como adicionar tipos de entrada para um tópico de ajuda do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850177"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>How to Add Input Types to a Cmdlet Help Topic (Como Adicionar Tipos de Introdução ao Tópico de Ajuda de um Cmdlet)

Esta secção descreve como adicionar uma seção de entradas para um tópico de ajuda do cmdlet Windows PowerShell®. A secção de entradas lista as classes do .NET de objetos que o cmdlet aceita como entrada do pipeline, pelo valor ou pelo nome de propriedade.

Não existe nenhum limite para o número de classes que pode adicionar a uma secção de entradas. Os tipos de entrada encontram-se entre uma \<comando: inputTypes > nó, com cada classe deve estar entre um \<comando: inputType > elemento.

O esquema inclui dois \<maml:description > elementos em cada \<comando: inputType > elemento. No entanto, o `Get-Help` cmdlet apresenta apenas o conteúdo do \<comando: inputType > /\<maml:description >) elemento.

A partir do Windows PowerShell 3.0, o `Get-Help` cmdlet apresenta o conteúdo do \<maml:uri > elemento. Esse elemento permite-lhe direcionar os utilizadores para tópicos que descrevem a classe do .NET.

O XML a seguir mostra o \<maml:inputTypes > nó.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

O XML a seguir mostra um exemplo de como utilizar o \<maml:inputTypes > nó documentar um tipo de entrada.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```