---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Pipeline de objeto
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 3fa41cc744cf3ab66fc5ef186ead8eb919429a76
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="object-pipeline"></a>Pipeline de objeto
Pipelines atuam como uma série de segmentos ligados do pipe. Itens de mover pelo pipeline passaram cada segmento. Para criar um pipeline no Windows PowerShell, ligar os comandos juntamente com o operador de pipe "|". O resultado de cada comando é utilizado como entrada para o comando seguinte.

Pipelines são possivelmente o conceito mais importante utilizado em interfaces de linha de comandos. Utilizado corretamente, pipelines não só reduzir o esforço envolvido na introduzir comandos complexos, mas também o tornam mais fácil ver o fluxo de trabalho nos comandos. Uma característica relacionada útil de pipelines é que uma vez que operam em cada item em separado, não dispõe de modificá-las com base em se terá de zero, um ou muitos itens no pipeline. Além disso, cada comando num pipeline (denominado um elemento de pipeline), normalmente, transmite o resultado para o seguinte comando no pipeline item-por-item. Normalmente, esta reduz a necessidade de recurso dos comandos complexas e permite-lhe iniciar imediatamente a obter o resultado.

Neste capítulo, será descrevem como pipeline do Windows PowerShell difere de acordo com os pipelines de shells mais populares e, em seguida, demonstrar algumas ferramentas básicas que pode utilizar para ajudar a saída do pipeline de controlo e também para ver como funciona o pipeline.

