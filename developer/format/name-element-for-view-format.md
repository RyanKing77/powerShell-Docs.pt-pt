---
title: Elemento de nome para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849267"
---
# <a name="name-element-for-view-format"></a>Name Element for View (Format) (Elemento Name para View [Formatação])

Especifica o nome que é utilizado para identificar o modo de exibição.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) nome elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Name` elemento. Apenas um `Name` elemento é permitido para cada exibição.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma vista que é utilizada para apresentar os membros de um ou mais objetos do .NET.|

## <a name="text-value"></a>Valor do Texto

Especifique um nome amigável exclusivo para a vista. Este nome pode incluir uma referência para o tipo da exibição (como uma vista de tabela ou vista de lista), qual objeto ou conjunto de objetos, utilize a vista, o comando devolve os objetos ou uma combinação das mesmas.

## <a name="remarks"></a>Observações

Para obter mais informações sobre os diferentes tipos de vistas, consulte os seguintes tópicos: [Exibição de tabela](./creating-a-table-view.md), [vista de lista](./creating-a-list-view.md), [vista alargada](./creating-a-wide-view.md), e [vista personalizada](./creating-custom-controls.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `View` elemento que define uma vista de tabela para o [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto. O nome da vista é o "serviço".

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>Veja Também

[Criar uma vista de lista](./creating-a-list-view.md)

[Criar uma vista de tabela](./creating-a-table-view.md)

[Criar uma vista alargada](./creating-a-wide-view.md)

[Criação de controles personalizados](./creating-custom-controls.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
