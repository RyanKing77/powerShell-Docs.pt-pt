---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Pipeline de Objeto
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 6102ec6e8fbf38fdc2bc5fa9c583244ef639dec8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="object-pipeline"></a>Pipeline de Objeto
Pipelines atuam como uma série de segmentos ligados do pipe. Itens de mover pelo pipeline passaram cada segmento. Para criar um pipeline no Windows PowerShell, ligar os comandos juntamente com o operador de pipe "|". O resultado de cada comando é utilizado como entrada para o comando seguinte.

Pipelines são possivelmente o conceito mais importante utilizado em interfaces de linha de comandos. Utilizado corretamente, pipelines não só reduzir o esforço envolvido na introduzir comandos complexos, mas também o tornam mais fácil ver o fluxo de trabalho nos comandos. Uma característica relacionada útil de pipelines é que uma vez que operam em cada item em separado, não dispõe de modificá-las com base em se terá de zero, um ou muitos itens no pipeline. Além disso, cada comando num pipeline (denominado um elemento de pipeline), normalmente, transmite o resultado para o seguinte comando no pipeline item-por-item. Normalmente, esta reduz a necessidade de recurso dos comandos complexas e permite-lhe iniciar imediatamente a obter o resultado.

Neste capítulo, será descrevem como pipeline do Windows PowerShell difere de acordo com os pipelines de shells mais populares e, em seguida, demonstrar algumas ferramentas básicas que pode utilizar para ajudar a saída do pipeline de controlo e também para ver como funciona o pipeline.