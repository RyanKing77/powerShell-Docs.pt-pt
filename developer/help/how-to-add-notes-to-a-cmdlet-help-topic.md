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
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>How to Add Notes to a Cmdlet Help Topic (Como Adicionar Notas ao Tópico de Ajuda de um Cmdlet)

Esta secção descreve como adicionar uma secção de notas a um tópico de ajuda do cmdlet Windows PowerShell®. A secção de notas é utilizada para explicar os detalhes que não se adequarão facilmente as outras secções estruturadas, como uma explicação mais detalhada de um parâmetro. Este conteúdo pode incluir comentários sobre como o cmdlet funciona com um provedor específico, alguns usos exclusivos, embora o mais importantes, do cmdlet ou formas de evitar condições de erro possíveis.

Não há nenhum limite para o número de notas que podem ser adicionados a uma secção de notas. Para cada observação, adicionar um par de \<maml:alert > com as etiquetas para o \<maml:alertset > nó. O conteúdo de cada nota é adicionado num conjunto de \<maml:para > etiquetas. Utilize zero \<maml:para > etiquetas para espaçamento.

O XML a seguir mostra um \<maml:alertset > nó com dois notas. Tenha em atenção que cada nota tem opcional \<maml:title > etiqueta (títulos podem ser utilizados para agrupar qualquer conjunto de \<maml:alert > etiquetas), e que cada nota tem uma linha em branco, seguindo o conteúdo para o espaçamento.

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



