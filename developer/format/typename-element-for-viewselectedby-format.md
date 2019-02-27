---
title: Elemento de TypeName para ViewSelectedBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848140"
---
# <a name="typename-element-for-viewselectedby-format"></a>TypeName Element for ViewSelectedBy (Format) (Elemento TypeName para ViewSelectedBy [Formatação])

Especifica um objeto .NET que é apresentado pela vista.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ViewSelectedBy elemento (formato) TypeName elemento de configuração para ViewSelectedBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e os elementos pai do `TypeName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ViewSelectedBy (formato)](./viewselectedby-element-format.md)|Define os objetos do .NET que são apresentados pela exibição.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observações

Para obter mais informações sobre como este elemento é usado em exibições diferentes, consulte [criar uma vista de tabela](./creating-a-table-view.md), [criar uma vista de lista](./creating-a-list-view.md), [criação de uma vista alargada](./creating-a-wide-view.md), e [ Componentes de exibição personalizada](./creating-custom-controls.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como especificar a [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto para uma vista de lista. O mesmo esquema é usado para exibições de tabela, ampla e personalizadas.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Consulte Também

[Criar uma vista de lista](./creating-a-list-view.md)

[Criar uma vista de tabela](./creating-a-table-view.md)

[Criar uma vista alargada](./creating-a-wide-view.md)

[Criação de controles personalizados](./creating-custom-controls.md)

[Elemento de ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
