---
title: Como adicionar notas a um tópico de ajuda do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083421"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="4daf9-102">How to Add Notes to a Cmdlet Help Topic (Como Adicionar Notas ao Tópico de Ajuda de um Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="4daf9-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="4daf9-103">Esta secção descreve como adicionar uma secção de notas a um tópico de ajuda do cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="4daf9-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="4daf9-104">A secção de notas é utilizada para explicar os detalhes que não se adequarão facilmente as outras secções estruturadas, como uma explicação mais detalhada de um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4daf9-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="4daf9-105">Este conteúdo pode incluir comentários sobre como o cmdlet funciona com um provedor específico, alguns usos exclusivos, embora o mais importantes, do cmdlet ou formas de evitar condições de erro possíveis.</span><span class="sxs-lookup"><span data-stu-id="4daf9-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="4daf9-106">Não há nenhum limite para o número de notas que podem ser adicionados a uma secção de notas.</span><span class="sxs-lookup"><span data-stu-id="4daf9-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="4daf9-107">Para cada observação, adicionar um par de \<maml:alert > com as etiquetas para o \<maml:alertset > nó.</span><span class="sxs-lookup"><span data-stu-id="4daf9-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="4daf9-108">O conteúdo de cada nota é adicionado num conjunto de \<maml:para > etiquetas.</span><span class="sxs-lookup"><span data-stu-id="4daf9-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="4daf9-109">Utilize zero \<maml:para > etiquetas para espaçamento.</span><span class="sxs-lookup"><span data-stu-id="4daf9-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="4daf9-110">O XML a seguir mostra um \<maml:alertset > nó com dois notas.</span><span class="sxs-lookup"><span data-stu-id="4daf9-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="4daf9-111">Tenha em atenção que cada nota tem opcional \<maml:title > etiqueta (títulos podem ser utilizados para agrupar qualquer conjunto de \<maml:alert > etiquetas), e que cada nota tem uma linha em branco, seguindo o conteúdo para o espaçamento.</span><span class="sxs-lookup"><span data-stu-id="4daf9-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



