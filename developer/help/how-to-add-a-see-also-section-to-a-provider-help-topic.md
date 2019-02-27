---
title: Como adicionar uma Veja também seção um tópico de ajuda do Provedor | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848455"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="6e36b-102">How to Add a See Also Section to a Provider Help Topic (Como Adicionar uma Secção Consulte Também ao Tópico de Ajuda de um Fornecedor)</span><span class="sxs-lookup"><span data-stu-id="6e36b-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="6e36b-103">Esta secção explica como preencher os **ver também** seção um tópico de ajuda do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="6e36b-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="6e36b-104">O **ver também** secção consiste numa lista de tópicos que estão relacionadas com o fornecedor ou poderá ajudar o utilizador a compreender melhor e a utilizar o fornecedor.</span><span class="sxs-lookup"><span data-stu-id="6e36b-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="6e36b-105">A lista de tópico pode incluir a ajuda do cmdlet, ajuda do provedor e conceitual ("sobre") tópicos de ajuda do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e36b-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="6e36b-106">Ele também pode incluir referências a livros, papel e tópicos online, incluindo uma versão online do tópico de ajuda do fornecedor atual.</span><span class="sxs-lookup"><span data-stu-id="6e36b-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="6e36b-107">Quando consulte online tópicos, forneça o URI ou um termo de pesquisa em texto simples.</span><span class="sxs-lookup"><span data-stu-id="6e36b-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="6e36b-108">O `Get-Help` cmdlet não ligar ou redirecionar para qualquer um dos tópicos na lista.</span><span class="sxs-lookup"><span data-stu-id="6e36b-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="6e36b-109">Além disso, o `Online` parâmetro do `Get-Help` cmdlet não funciona com a ajuda do provedor.</span><span class="sxs-lookup"><span data-stu-id="6e36b-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="6e36b-110">A secção Consulte também é criada a partir do `RelatedLinks` elemento e as etiquetas que ele contém.</span><span class="sxs-lookup"><span data-stu-id="6e36b-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="6e36b-111">O XML a seguir mostra como adicionar as etiquetas.</span><span class="sxs-lookup"><span data-stu-id="6e36b-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="6e36b-112">Para adicionar "Consulte também" Tópicos</span><span class="sxs-lookup"><span data-stu-id="6e36b-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="6e36b-113">Na *AssemblyName*help.xml. dll do ficheiro, dentro da `providerHelp` elemento, adicionar um `RelatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="6e36b-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="6e36b-114">O `RelatedLinks` elemento deve ser o último elemento no `providerHelp` elemento.</span><span class="sxs-lookup"><span data-stu-id="6e36b-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="6e36b-115">Apenas um `RelatedLinks` elemento é permitido em cada tópico de ajuda do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="6e36b-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="6e36b-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6e36b-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="6e36b-117">Para cada tópico na **Consulte também** secção, dentro do `RelatedLinks` elemento, adicionar um `navigationLink` elemento.</span><span class="sxs-lookup"><span data-stu-id="6e36b-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="6e36b-118">Em seguida, dentro de cada `navigationLink` elemento, adicione uma `linkText` e um elemento `uri` elemento.</span><span class="sxs-lookup"><span data-stu-id="6e36b-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="6e36b-119">Se não estiver a utilizar o `uri` elemento, pode adicioná-lo como um elemento vazio (\<uri / >).</span><span class="sxs-lookup"><span data-stu-id="6e36b-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="6e36b-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6e36b-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="6e36b-121">Escreva o nome de tópico entre o `linkText` etiquetas.</span><span class="sxs-lookup"><span data-stu-id="6e36b-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="6e36b-122">Se está a fornecer um URI, escreva-entre o `uri` etiquetas.</span><span class="sxs-lookup"><span data-stu-id="6e36b-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="6e36b-123">Para indicar a versão online do tópico de ajuda do fornecedor atual, entre o `linkText` etiquetas, tipo "versão Online:" em vez do nome de tópico.</span><span class="sxs-lookup"><span data-stu-id="6e36b-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="6e36b-124">Normalmente, a "versão Online:" link é o primeiro tópico na lista de tópico Consulte também.</span><span class="sxs-lookup"><span data-stu-id="6e36b-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="6e36b-125">O exemplo seguinte inclui três tópicos Consulte também.</span><span class="sxs-lookup"><span data-stu-id="6e36b-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="6e36b-126">A primeira referem-se para a versão online do tópico atual.</span><span class="sxs-lookup"><span data-stu-id="6e36b-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="6e36b-127">O segundo refere-se para um tópico de ajuda do cmdlet Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e36b-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="6e36b-128">A terceira refere-se para outro tópico online.</span><span class="sxs-lookup"><span data-stu-id="6e36b-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```