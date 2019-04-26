---
title: GroupBy elemento para a exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065548"
---
# <a name="groupby-element-for-view-format"></a>GroupBy Element for View (Format) (Elemento GroupBy para View [Formatação])

Define a forma como é apresentado um novo grupo de objetos. Este elemento é utilizado ao definir uma tabela, a lista, o modo de exibição control ampla ou personalizada.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para a exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos principais elementos filho.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomControl para GroupBy (formato)](./customcontrol-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Define o controlo personalizado que apresentar novos grupos.|
|[Elemento de CustomControlName para GroupBy (formato)](./customcontrolname-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica o nome de um controlo que é utilizado para apresentar o novo grupo.|
|[Elemento da etiqueta para GroupBy (formato)](./label-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica uma etiqueta que é apresentada quando for detetado um novo grupo.|
|[Elemento de PropertyName para GroupBy (formato)](./propertyname-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade .NET iniciada a um novo grupo sempre que seu valor é alterado.|
|[Elemento de ScriptBlock para GroupBy (formato)](./scriptblock-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica o script que inicia um novo grupo sempre que seu valor é alterado.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma vista que apresente um ou mais objetos do .NET.|

## <a name="remarks"></a>Observações

Ao definir como é apresentado um novo grupo de objetos, tem de especificar a propriedade ou um script que iniciará o novo grupo; No entanto, não é possível especificar ambos.

## <a name="see-also"></a>Veja Também

[Elemento de CustomControlName para GroupBy (formato)](./customcontrolname-element-for-groupby-format.md)

[Elemento da etiqueta para GroupBy (formato)](./label-element-for-groupby-format.md)

[Elemento de PropertyName para GroupBy (formato)](./propertyname-element-for-groupby-format.md)

[Elemento de ScriptBlock para GroupBy (formato)](./scriptblock-element-for-groupby-format.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
