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
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="c52d6-102">How to Add Input Types to a Cmdlet Help Topic (Como Adicionar Tipos de Introdução ao Tópico de Ajuda de um Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="c52d6-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="c52d6-103">Esta secção descreve como adicionar uma seção de entradas para um tópico de ajuda do cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="c52d6-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="c52d6-104">A secção de entradas lista as classes do .NET de objetos que o cmdlet aceita como entrada do pipeline, pelo valor ou pelo nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c52d6-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="c52d6-105">Não existe nenhum limite para o número de classes que pode adicionar a uma secção de entradas.</span><span class="sxs-lookup"><span data-stu-id="c52d6-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="c52d6-106">Os tipos de entrada encontram-se entre uma \<comando: inputTypes > nó, com cada classe deve estar entre um \<comando: inputType > elemento.</span><span class="sxs-lookup"><span data-stu-id="c52d6-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="c52d6-107">O esquema inclui dois \<maml:description > elementos em cada \<comando: inputType > elemento.</span><span class="sxs-lookup"><span data-stu-id="c52d6-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="c52d6-108">No entanto, o `Get-Help` cmdlet apresenta apenas o conteúdo do \<comando: inputType > /\<maml:description >) elemento.</span><span class="sxs-lookup"><span data-stu-id="c52d6-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="c52d6-109">A partir do Windows PowerShell 3.0, o `Get-Help` cmdlet apresenta o conteúdo do \<maml:uri > elemento.</span><span class="sxs-lookup"><span data-stu-id="c52d6-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="c52d6-110">Esse elemento permite-lhe direcionar os utilizadores para tópicos que descrevem a classe do .NET.</span><span class="sxs-lookup"><span data-stu-id="c52d6-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="c52d6-111">O XML a seguir mostra o \<maml:inputTypes > nó.</span><span class="sxs-lookup"><span data-stu-id="c52d6-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="c52d6-112">O XML a seguir mostra um exemplo de como utilizar o \<maml:inputTypes > nó documentar um tipo de entrada.</span><span class="sxs-lookup"><span data-stu-id="c52d6-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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