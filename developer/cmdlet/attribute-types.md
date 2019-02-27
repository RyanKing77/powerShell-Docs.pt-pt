---
title: Os tipos de atributo | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2019
ms.locfileid: "56852277"
---
# <a name="attribute-types"></a>Attribute Types (Tipos de Atributo)

Atributos de cmdlet podem ser agrupados por funcionalidade.
As secções seguintes descrevem os atributos disponíveis e descrevem o que faz o tempo de execução quando o atributo é invocado.

## <a name="cmdlet-attributes"></a>Cmdlet Attributes (Atributos de Cmdlet)

### <a name="cmdlet"></a>Cmdlet

Identifica uma classe do .NET Framework como um cmdlet.
Este é o atributo base necessário.
Para obter mais informações, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Atributos de parâmetro

### <a name="parameter"></a>Parâmetro

Identifica uma propriedade pública na classe cmdlet como um parâmetro de cmdlet.
Para obter mais informações, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Especifica um ou mais aliases para um parâmetro.
Para obter mais informações, consulte [declaração de atributo de Alias](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Atributos de validação de argumento

### <a name="validatecount"></a>ValidateCount

Especifica o número mínimo e máximo de argumentos que são permitidos para um parâmetro de cmdlet.
Para obter mais informações, consulte [declaração de atributo ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Especifica um número mínimo e máximo de carateres para um argumento do parâmetro de cmdlet.
Para obter mais informações, consulte [declaração de atributo ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Especifica um padrão de expressão regular que o argumento do parâmetro de cmdlet tem de corresponder.
Para obter mais informações, consulte [declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Especifica os valores mínimos e máximo para um argumento do parâmetro de cmdlet.
Para obter mais informações, consulte [declaração de atributo ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Especifica um conjunto de valores válidos para o argumento do parâmetro de cmdlet.
Para obter mais informações, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Consulte Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)
