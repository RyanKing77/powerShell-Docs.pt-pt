---
title: Estruturar o elemento para CustomItem para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: a7ee550527ec1cb00b4ed83478992c7ab54dbdb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850807"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Frame Element for CustomItem for CustomControl for View (Format) (Elemento Frame para CustomItem para CustomControl para View [Formatação])

Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita. Este elemento é utilizado ao definir uma vista de controle personalizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato) CustomItem elemento para CustomEntry para o elemento de quadro de CutomControlView (formato) para CustomItem para CustomControl para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Frame` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|`CustomItem Element`|Elemento necessário|
|[Elemento de FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres a primeira linha dos dados é desviada à esquerda.|
|[Elemento de FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres a primeira linha dos dados é desviada à direita.|
|[Elemento de LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres de dados são desviados da margem esquerda.|
|[Elemento de RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres de dados são desviados da margem direita.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomItem para CustomEntry para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Define os dados que são apresentados pelo controle e como ele é exibido.|

## <a name="remarks"></a>Observações

Não é possível especificar a [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementos na mesma `Frame` elemento.

## <a name="see-also"></a>Consulte Também

[Elemento de FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento de FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento de LeftIndent](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento de RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[Elemento de CustomItem para CustomEntry para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
