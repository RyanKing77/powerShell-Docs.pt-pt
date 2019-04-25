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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083438"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="e4a40-102">How to Add Input Types to a Cmdlet Help Topic (Como Adicionar Tipos de Introdução ao Tópico de Ajuda de um Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="e4a40-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="e4a40-103">Esta secção descreve como adicionar uma seção de entradas para um tópico de ajuda do cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="e4a40-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="e4a40-104">A secção de entradas lista as classes do .NET de objetos que o cmdlet aceita como entrada do pipeline, pelo valor ou pelo nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e4a40-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="e4a40-105">Não existe nenhum limite para o número de classes que pode adicionar a uma secção de entradas.</span><span class="sxs-lookup"><span data-stu-id="e4a40-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="e4a40-106">Os tipos de entrada encontram-se entre uma \<comando: inputTypes > nó, com cada classe deve estar entre um \<comando: inputType > elemento.</span><span class="sxs-lookup"><span data-stu-id="e4a40-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="e4a40-107">O esquema inclui dois \<maml:description > elementos em cada \<comando: inputType > elemento.</span><span class="sxs-lookup"><span data-stu-id="e4a40-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="e4a40-108">No entanto, o `Get-Help` cmdlet apresenta apenas o conteúdo do \<comando: inputType > /\<maml:description >) elemento.</span><span class="sxs-lookup"><span data-stu-id="e4a40-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="e4a40-109">A partir do Windows PowerShell 3.0, o `Get-Help` cmdlet apresenta o conteúdo do \<maml:uri > elemento.</span><span class="sxs-lookup"><span data-stu-id="e4a40-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="e4a40-110">Esse elemento permite-lhe direcionar os utilizadores para tópicos que descrevem a classe do .NET.</span><span class="sxs-lookup"><span data-stu-id="e4a40-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="e4a40-111">O XML a seguir mostra o \<maml:inputTypes > nó.</span><span class="sxs-lookup"><span data-stu-id="e4a40-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="e4a40-112">O XML a seguir mostra um exemplo de como utilizar o \<maml:inputTypes > nó documentar um tipo de entrada.</span><span class="sxs-lookup"><span data-stu-id="e4a40-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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