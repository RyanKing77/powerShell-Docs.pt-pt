---
title: Validação de entrada do parâmetro | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848805"
---
# <a name="validating-parameter-input"></a>Validating Parameter Input (Validar a Entrada de Parâmetros)

Windows PowerShell pode validar os argumentos passados para os parâmetros de cmdlet de várias formas. Windows PowerShell pode validar o comprimento, o intervalo e o padrão de caracteres do argumento. Pode validar o número de argumentos disponíveis (a contagem). Estas regras de validação são definidas por atributos de validação que são declarados com o atributo de parâmetro em propriedades públicas da classe cmdlet.

Para validar um argumento do parâmetro, o tempo de execução do Windows PowerShell usa as informações fornecidas pelos atributos de validação para confirmar o valor do parâmetro antes do cmdlet é executado. Se a entrada de parâmetro não for válida, o utilizador recebe uma mensagem de erro. Cada parâmetro de validação define uma regra de validação que é imposta pelo Windows PowerShell.

Windows PowerShell impõe as regras de validação com base nos seguintes atributos.

ValidateCount Especifica o número mínimo e máximo de argumentos que pode aceitar um parâmetro. Para obter mais informações sobre a sintaxe usada para declarar este atributo, consulte [declaração de atributo ValidateCount](./validatecount-attribute-declaration.md).

ValidateLength Especifica o número mínimo e máximo de carateres no argumento do parâmetro. Para obter mais informações sobre a sintaxe usada para declarar este atributo, consulte [declaração de atributo ValidateLength](./validatelength-attribute-declaration.md).

ValidatePattern Especifica uma expressão regular que valida o argumento do parâmetro. Para obter mais informações sobre a sintaxe usada para declarar este atributo, consulte [declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md).

ValidateRange Especifica os valores mínimos e máximo do argumento do parâmetro. Para obter mais informações sobre a sintaxe usada para declarar este atributo, consulte [declaração de atributo ValidateRange](./validaterange-attribute-declaration.md).

ValidateSet Especifica os valores válidos para o argumento do parâmetro. Para obter mais informações sobre a sintaxe usada para declarar este atributo, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Veja Também

[Como validar a entrada de parâmetro](./how-to-validate-parameter-input.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
