---
title: Como adicionar Links relacionados a um tópico de ajuda do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083353"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="41d49-102">How to Add Related Links to a Cmdlet Help Topic (Como Adicionar Ligações Relacionadas ao Tópico de Ajuda de um Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="41d49-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="41d49-103">Esta secção descreve como adicionar referências a outros conteúdos que está relacionado a um tópico de ajuda do cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="41d49-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="41d49-104">Uma vez que estas referências for apresentada uma janela de comando, eles não associar diretamente para os conteúdos referenciados.</span><span class="sxs-lookup"><span data-stu-id="41d49-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="41d49-105">Nos tópicos de ajuda cmdlet que estão incluídas no Windows PowerShell®, estas ligações referenciam outros cmdlets, conteúdo concetual ("about_") e outros documentos e arquivos de ajuda que não estão relacionadas com Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="41d49-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="41d49-106">O XML a seguir mostra como adicionar um nó de RelatedLinks que contém duas referências a tópicos relacionados.</span><span class="sxs-lookup"><span data-stu-id="41d49-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```



