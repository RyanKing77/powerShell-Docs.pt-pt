---
title: Atributos de cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068611"
---
# <a name="cmdlet-attributes"></a>Cmdlet Attributes (Atributos de Cmdlet)

Windows PowerShell define vários atributos que pode usar para adicionar funcionalidade comum a seus cmdlets sem implementar essa funcionalidade dentro de seu próprio código. Isto inclui o atributo de Cmdlet que identifica uma classe de Microsoft .NET Framework como uma classe cmdlet, o atributo OutputType que especifica os tipos do .NET Framework devolvidos pelo cmdlet, o atributo de parâmetro que identifica as propriedades públicas como cmdlet parâmetros e muito mais.

## <a name="in-this-section"></a>Nesta Secção

[Atributos no código de Cmdlet](./attributes-in-cmdlet-code.md) descreve a vantagem de usar atributos no código de cmdlet.

[Os tipos de atributo](./attribute-types.md) descreve os atributos diferentes que podem decorar uma classe cmdlet.

[Declaração de atributo de alias](./alias-attribute-declaration.md) descreve como definir aliases para um nome de parâmetro de cmdlet.

[Declaração de atributo do cmdlet](./cmdlet-attribute-declaration.md) descreve como definir uma classe do .NET Framework como um cmdlet.

[Declaração de atributo de credenciais](./credential-attribute-declaration.md) descreve como adicionar suporte para a conversão de entrada de cadeia de caracteres num [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.

[Atributo OutputType declaração](./outputtype-attribute-declaration.md) descreve como especificar os tipos do .NET Framework devolvidos pelo cmdlet.

[Declaração de atributo de parâmetro](./parameter-attribute-declaration.md) descreve como definir os parâmetros de um cmdlet.

[Declaração de atributo ValidateCount](./validatecount-attribute-declaration.md) descreve como definir o número de argumentos são permitidos para um parâmetro.

[Declaração de atributo ValidateLength](./validatelength-attribute-declaration.md) descreve como definir o comprimento (em carateres) de um argumento do parâmetro.

[Declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md) descreve como definir os padrões válidos para um argumento do parâmetro.

[Declaração de atributo ValidateRange](./validaterange-attribute-declaration.md) descreve como definir o intervalo válido de um argumento do parâmetro.

[Declaração de atributo ValidateSet](./validateset-attribute-declaration.md) descreve como definir os valores possíveis para um argumento do parâmetro.

## <a name="reference"></a>Referência

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
