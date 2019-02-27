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
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="52c24-102">How to Add Return Values to a Cmdlet Help Topic (Como Adicionar Valores Devolvidos ao Tópico de Ajuda de um Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="52c24-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="52c24-103">Esta secção descreve como adicionar uma secção de saídas para um tópico de ajuda do cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="52c24-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="52c24-104">A secção de saídas lista as classes do .NET de objetos que o cmdlet Devolve ou passa pelo pipeline.</span><span class="sxs-lookup"><span data-stu-id="52c24-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="52c24-105">Não existe nenhum limite para o número de classes que podem ser adicionados para a secção de saídas.</span><span class="sxs-lookup"><span data-stu-id="52c24-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="52c24-106">Os tipos de retornados de um cmdlet encontram-se entre uma \<comando: returnValues > nó, com cada classe deve estar entre um \<comando: returnValue > elemento.</span><span class="sxs-lookup"><span data-stu-id="52c24-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="52c24-107">Se um cmdlet não gera quaisquer dados, utilize esta secção para indicar que não existe nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="52c24-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="52c24-108">Por exemplo, em vez do nome de classe, escrever "None" e fornecer uma breve explicação.</span><span class="sxs-lookup"><span data-stu-id="52c24-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="52c24-109">Se o cmdlet gera saída condicionalmente, utilize este nó para explicar as condições e descrever o resultado condicional.</span><span class="sxs-lookup"><span data-stu-id="52c24-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="52c24-110">O esquema inclui dois \<maml:description > elementos em cada \<comando: returnValue > elemento.</span><span class="sxs-lookup"><span data-stu-id="52c24-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="52c24-111">No entanto, o `Get-Help` cmdlet apresenta apenas o conteúdo do \<comando: returnValue > /\<maml:description > elemento.</span><span class="sxs-lookup"><span data-stu-id="52c24-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="52c24-112">A partir do Windows PowerShell 3.0, o `Get-Help` cmdlet apresenta o conteúdo do \<maml:uri > elemento.</span><span class="sxs-lookup"><span data-stu-id="52c24-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="52c24-113">Esse elemento permite-lhe direcionar os utilizadores para tópicos que descrevem a classe do .NET.</span><span class="sxs-lookup"><span data-stu-id="52c24-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="52c24-114">O XML a seguir mostra o \<maml:returnValues > nó.</span><span class="sxs-lookup"><span data-stu-id="52c24-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="52c24-115">O XML a seguir mostra um exemplo de como utilizar o \<maml:returnValues > nó documentar um tipo de saída.</span><span class="sxs-lookup"><span data-stu-id="52c24-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

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



