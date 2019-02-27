---
title: O elemento de DefaultSettings (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: 59cc0514087cc52438e0d1271b8b77a7799eb32c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846579"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings Element (Format) (Elemento DefaultSettings [Formatação])

Define configurações comuns que se aplicam a todas as vistas do ficheiro de formatação. Definições comuns incluem a exibição de erros, quebra de texto em tabelas, definir a forma como as coleções são expandidas e muito mais.

Elemento de DefaultSettings de elemento (formato) de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `DefaultSettings` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de DisplayError (Frmat)](./displayerror-element-format.md)|Elemento opcional.<br /><br /> Especifica que a cadeia de caracteres #ERR é apresentada quando ocorre um erro ao apresentar um conjunto de dados.|
|[Elemento de EnumerableExpansions (formato)](./enumerableexpansions-element-format.md)|Elemento opcional.<br /><br /> Define as diferentes formas em que os objetos do .NET são expandidos quando são apresentados numa vista.|
|[PropertyCountForTable (formato)](./propertycountfortable-element-format.md)|Elemento opcional.<br /><br /> Especifica o número mínimo de propriedades que têm de ter um objeto para exibir o objeto numa exibição de tabela.|
|[Elemento de ShowError (formato)](./showerror-element-format.md)|Elemento opcional.<br /><br /> Especifica que o registo de erro completa é apresentado quando ocorre um erro ao apresentar um conjunto de dados.|
|[Elemento de WrapTables (formato)](./wraptables-element-format.md)|Elemento opcional.<br /><br /> Especifica que os dados numa tabela são movidos para a próxima linha se ele não se adequarão a largura da coluna.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de configuração](./configuration-element-format.md)|Representa o elemento de nível superior de um ficheiro de formatação.|

## <a name="remarks"></a>Observações

## <a name="see-also"></a>Veja Também

[Elemento de configuração](./configuration-element-format.md)

[Elemento de DisplayError (Frmat)](./displayerror-element-format.md)

[Elemento de EnumerableExpansions (formato)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (formato)](./propertycountfortable-element-format.md)

[Elemento de ShowError (formato)](./showerror-element-format.md)

[Elemento de WrapTables (formato)](./wraptables-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
