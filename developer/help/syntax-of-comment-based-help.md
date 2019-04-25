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
# <a name="syntax-of-comment-based-help"></a>Syntax of Comment-Based Help (Sintaxe de Ajuda Baseada em Comentários)

Esta secção descreve a sintaxe da ajuda baseada no comentário.

## <a name="syntax-diagram"></a>Diagrama da sintaxe

 A sintaxe para obter ajuda baseada no comentário é o seguinte:

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Descrição de sintaxe

 Ajuda baseada no comentário é escrita como uma série de comentários. Pode digitar um símbolo de comentário (#) antes de cada linha de comentários, ou pode utilizar o "\<#" e "#>" símbolos para criar um bloco de comentários. Todas as linhas dentro do bloco de comentário são interpretadas como comentários.

 Cada secção da ajuda baseada no comentário é definida por uma palavra-chave e cada palavra-chave é precedida por um ponto (.). As palavras-chave podem aparecer em qualquer ordem. Os nomes de palavra-chave não diferenciam maiúsculas de minúsculas.

 Um bloco de comentários tem de conter pelo menos uma palavra-chave de ajuda. Algumas das palavras-chave, como exemplo, podem aparecer várias vezes no mesmo bloco de comentário. O conteúdo de ajuda para cada palavra-chave começa na linha depois da palavra-chave e pode distribuir várias linhas.

 Todas as linhas num tópico de ajuda baseada no comentário têm de ser contíguas. Se um tópico de ajuda baseada no comentário segue um comentário que não faz parte do tópico de ajuda, tem de existir pelo menos uma linha em branco entre a última linha de comentário não-Help e o início da ajuda baseada no comentário.

 Por exemplo, o seguinte tópico da ajuda baseada no comentário contém o. Palavra-chave de descrição e o respetivo valor, o que é uma descrição de uma função ou script.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```