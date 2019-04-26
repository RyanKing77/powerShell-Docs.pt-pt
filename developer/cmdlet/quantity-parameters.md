---
title: Parâmetros de quantidade | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067540"
---
# <a name="quantity-parameters"></a>Quantity Parameters (Parâmetros de Quantidade)

A tabela seguinte lista os nomes recomendados e a funcionalidade para os parâmetros de quantidade.

|Parâmetro|Funcionalidade|
|---|---|
|**Todos**<br>Tipo de dados: Booleano|Implementar este parâmetro, de modo que `true` indica que todos os recursos devem ser utilizados em vez de um subconjunto de padrão de recursos. Implementar este parâmetro, de modo que `false` indica um subconjunto dos recursos.|
|**Alocação**<br>Tipo de dados: Int32|Implemente este parâmetro para que o utilizador pode especificar o número de itens para alocar.|
|**BlockCount**<br>Tipo de dados: Int64|Implemente este parâmetro para que o utilizador pode especificar a contagem de bloco.|
|**Contagem**<br>Tipo de dados: Int64|Implemente este parâmetro para que o utilizador pode especificar a contagem.|
|**Âmbito**<br>Tipo de dados: Palavra-chave|Implemente este parâmetro para que o utilizador pode especificar o âmbito a trabalhar.|

## <a name="see-also"></a>Veja Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
