---
title: Declaração de atributo de parâmetro | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "56852144"
---
# <a name="parameter-attribute-declaration"></a>Parameter Attribute Declaration (Declaração do Atributo Parameter)

O atributo de parâmetro identifica uma propriedade pública da classe cmdlet como um parâmetro de cmdlet.

## <a name="syntax"></a>Sintaxe

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parâmetros

`Mandatory` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter. `True` indica que o parâmetro de cmdlet é obrigatório. Se não for fornecido um parâmetro necessário quando o cmdlet é invocado, o Windows PowerShell pede ao utilizador para um valor de parâmetro. A predefinição é `false`.

`ParameterSetName` ([System. String](/dotnet/api/System.String)) opcional chamado de parameter. Especifica que o parâmetro definido que pertence este parâmetro de cmdlet. Se não for especificado nenhum conjunto de parâmetros, o parâmetro pertence a todos os conjuntos de parâmetros.

`Position` ([System.Integer](/dotnet/api/System.Integer)) opcional chamado de parameter. Especifica a posição do parâmetro dentro de um comando do Windows PowerShell.

`ValueFromPipeline` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter. `True` indica que o parâmetro de cmdlet assume o valor de um objeto de pipeline. Especifique essa palavra-chave, se o cmdlet acessa o completa de objeto, não apenas uma propriedade do objeto. A predefinição é `false`.

`ValueFromPipelineByPropertyName` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter. `True` indica que o parâmetro de cmdlet assume o valor de uma propriedade de um objeto de pipeline que tenha o mesmo nome ou o alias do mesmo como este parâmetro. Por exemplo, se o cmdlet tem um `Name` parâmetro e o objeto de pipeline também tem uma `Name` propriedade, o valor da `Name` propriedade é atribuída ao `Name` parâmetro do cmdlet. A predefinição é `false`.

`ValueFromRemainingArguments` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter. `True` indica que o parâmetro de cmdlet aceita todos os argumentos restantes que são transmitidos ao cmdlet. A predefinição é `false`.

`HelpMessage` Opcional chamado de parameter. Especifica uma breve descrição do parâmetro. Windows PowerShell apresenta esta mensagem quando um cmdlet é executado e não for especificado um parâmetro obrigatório.

`HelpMessageBaseName` Opcional chamado de parameter. Especifica a localização onde residem os identificadores de recurso. Por exemplo, este parâmetro pode especificar um assembly de recurso que contém mensagens de ajuda que pretende localizar.

`HelpMessageResourceId` Opcional chamado de parameter. Especifica o identificador de recurso para uma mensagem de ajuda.

## <a name="remarks"></a>Observações

- Para obter mais informações sobre como declarar este atributo, consulte [como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).

- Um cmdlet pode ter qualquer número de parâmetros. No entanto, para uma melhor experiência de utilizador, limite o número de parâmetros.

- Parâmetros devem ser declarados em campos de nestatické públicos ou propriedades. Os parâmetros devem ser declarados em propriedades. A propriedade tem de ter um acessador do conjunto público e se o `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` palavra-chave for especificada, a propriedade tem de ter um acessador get público.

- Quando especificar parâmetros posicionais, limite o número de parâmetros posicionais, num parâmetro definido para menos de cinco. E, parâmetros posicionais não tem de ser contíguo. Posições 5, 100 e 250 funcionam da mesma como posições 0, 1 e 2.

- Quando o `Position` palavra-chave não for especificado, o parâmetro de cmdlet deve ser referenciado pelo respetivo nome.

- Quando utiliza conjuntos de parâmetros, tenha em atenção o seguinte:

    - Cada conjunto de parâmetros tem de ter, pelo menos, um parâmetro exclusivo. Cmdlet bom design indica que este parâmetro exclusivo também deve ser obrigatório se for possível. Se seu cmdlet foi concebido para ser executado sem parâmetros, o único parâmetro não pode ser obrigatório.

    - Nenhum conjunto de parâmetros deve conter mais de um parâmetro posicional com a mesma posição.

    - Apenas um parâmetro num conjunto de parâmetros deve declarar `ValueFromPipeline = true`. Podem definir vários parâmetros `ValueFromPipelineByPropertyName = true`.

    - Podem definir vários parâmetros `ValueFromPipelineByPropertyName = true`.

- Para obter mais informações sobre as diretrizes para os nomes de parâmetros, consulte [nomes de parâmetros de Cmdlet](standard-cmdlet-parameter-names-and-types.md).

- O atributo de parâmetro é definido pela [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) classe.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Nomes dos parâmetros do cmdlet](standard-cmdlet-parameter-names-and-types.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
