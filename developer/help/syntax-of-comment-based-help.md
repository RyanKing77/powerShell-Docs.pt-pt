---
title: Sintaxe da ajuda baseada no comentário | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083217"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="af272-102">Syntax of Comment-Based Help (Sintaxe de Ajuda Baseada em Comentários)</span><span class="sxs-lookup"><span data-stu-id="af272-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="af272-103">Esta secção descreve a sintaxe da ajuda baseada no comentário.</span><span class="sxs-lookup"><span data-stu-id="af272-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="af272-104">Diagrama da sintaxe</span><span class="sxs-lookup"><span data-stu-id="af272-104">Syntax Diagram</span></span>

 <span data-ttu-id="af272-105">A sintaxe para obter ajuda baseada no comentário é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="af272-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="af272-106">Descrição de sintaxe</span><span class="sxs-lookup"><span data-stu-id="af272-106">Syntax Description</span></span>

 <span data-ttu-id="af272-107">Ajuda baseada no comentário é escrita como uma série de comentários.</span><span class="sxs-lookup"><span data-stu-id="af272-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="af272-108">Pode digitar um símbolo de comentário (#) antes de cada linha de comentários, ou pode utilizar o "\<#" e "#>" símbolos para criar um bloco de comentários.</span><span class="sxs-lookup"><span data-stu-id="af272-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="af272-109">Todas as linhas dentro do bloco de comentário são interpretadas como comentários.</span><span class="sxs-lookup"><span data-stu-id="af272-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="af272-110">Cada secção da ajuda baseada no comentário é definida por uma palavra-chave e cada palavra-chave é precedida por um ponto (.).</span><span class="sxs-lookup"><span data-stu-id="af272-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="af272-111">As palavras-chave podem aparecer em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="af272-111">The keywords can appear in any order.</span></span> <span data-ttu-id="af272-112">Os nomes de palavra-chave não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="af272-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="af272-113">Um bloco de comentários tem de conter pelo menos uma palavra-chave de ajuda.</span><span class="sxs-lookup"><span data-stu-id="af272-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="af272-114">Algumas das palavras-chave, como exemplo, podem aparecer várias vezes no mesmo bloco de comentário.</span><span class="sxs-lookup"><span data-stu-id="af272-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="af272-115">O conteúdo de ajuda para cada palavra-chave começa na linha depois da palavra-chave e pode distribuir várias linhas.</span><span class="sxs-lookup"><span data-stu-id="af272-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="af272-116">Todas as linhas num tópico de ajuda baseada no comentário têm de ser contíguas.</span><span class="sxs-lookup"><span data-stu-id="af272-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="af272-117">Se um tópico de ajuda baseada no comentário segue um comentário que não faz parte do tópico de ajuda, tem de existir pelo menos uma linha em branco entre a última linha de comentário não-Help e o início da ajuda baseada no comentário.</span><span class="sxs-lookup"><span data-stu-id="af272-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="af272-118">Por exemplo, o seguinte tópico da ajuda baseada no comentário contém o. Palavra-chave de descrição e o respetivo valor, o que é uma descrição de uma função ou script.</span><span class="sxs-lookup"><span data-stu-id="af272-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```