---
title: Parâmetros do cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845305"
---
# <a name="cmdlet-parameters"></a>Cmdlet Parameters (Parâmetros de Cmdlets)

Os parâmetros de cmdlet fornecem o mecanismo que permite que um cmdlet aceitar a entrada. Parâmetros podem aceitar entrada diretamente a partir da linha de comandos, ou a partir de objetos transmitidos ao cmdlet através do pipeline, os argumentos (também conhecido como *valores*) desses parâmetros, pode especificar a entrada que o cmdlet aceita, como o cmdlet deve executar suas ações e os dados que o cmdlet devolve para o pipeline.

## <a name="in-this-section"></a>Nesta Secção

[Declaração de propriedades como parâmetros](./declaring-properties-as-parameters.md) fornece informações básicas, tem de compreender antes de declarar os parâmetros de um cmdlet.

[Tipos de parâmetros de Cmdlet](./types-of-cmdlet-parameters.md) descreve os diferentes tipos de parâmetros que pode declarar nos cmdlets.

[Nome do parâmetro de cmdlet e diretrizes de funcionalidade](./standard-cmdlet-parameter-names-and-types.md) Discuses os nomes, recomendado o tipo de dados e a funcionalidade dos parâmetros padrão.

[Aliases de parâmetro](./parameter-aliases.md) discute os aliases que pode definir para os parâmetros.

[Os nomes de parâmetros comuns](./common-parameter-names.md) este tópico descreve os parâmetros que o Windows PowerShell adiciona aos cmdlets.

[Parâmetro de cmdlet define](./cmdlet-parameter-sets.md) discute como conjuntos de parâmetros permitem-lhe escrever um único cmdlet que pode realizar ações diferentes para diferentes cenários.

[Parâmetros de cmdlet dinâmicos](./cmdlet-dynamic-parameters.md) aborda os parâmetros que estão disponíveis para o utilizador sob condições especiais.

[Suporte a caracteres curinga nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md) descreve como fornecer suporte para carateres universais ao conceber um cmdlet que será executado em relação a um grupo de recursos.

[Validação de entrada do parâmetro](./validating-parameter-input.md) descreve a forma como o Windows PowerShell valida os argumentos passados para os parâmetros de cmdlet.

[Parâmetros de filtro de entrada](./input-filter-parameters.md) Discusses a `Filter`, `Include`, e `Exclude` parâmetros filtrar o conjunto de objetos de entrada que afeta o cmdlet.

## <a name="related-sections"></a>Secções Relacionadas

[Como validar a entrada de parâmetro](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>Consulte Também

[Declaração de atributo de parâmetro](./parameter-attribute-declaration.md)

[Cmdlets do Windows PowerShell](./cmdlet-overview.md)
