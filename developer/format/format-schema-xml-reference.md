---
title: Formatar a referência do esquema XML | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065789"
---
# <a name="format-schema-xml-reference"></a>Format Schema XML Reference (Referência XML do Esquema de Formatação)

Os tópicos nesta secção descrevem os elementos XML utilizados pela formatação de arquivos (Format.ps1xml arquivos). Arquivos de formatação definem como é apresentado o objeto .NET; Não altere o objeto em si.

## <a name="in-this-section"></a>Nesta Secção

[Elemento de alinhamento para TableColumnHeader para TableControl (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) define a forma como os dados num cabeçalho de coluna são apresentados.

[Elemento de alinhamento para TableColumnItem para TableControl (formato)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) define a forma como os dados na linha são apresentados.

[Elemento de dimensionamento automático para TableControl (formato)](./autosize-element-for-tablecontrol-format.md) Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.

[Elemento de dimensionamento automático para WideControl (formato)](./autosize-element-for-widecontrol-format.md) Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.

[Elemento de ColumnNumber para WideControl (formato)](./columnnumber-element-for-widecontrol-format.md) Especifica o número de colunas apresentadas na vista alargada.

[O elemento de configuração (formato)](./configuration-element-format.md) representa o elemento de nível superior do ficheiro formatação.

[Controlar o elemento para controles de configuração (formato)](./control-element-for-controls-for-configuration-format.md) define um controle comum que pode ser utilizado por todas as vistas do ficheiro formatação e o nome que é utilizado para referenciar o controle.

[Controlar o elemento para controles para exibição (formato)](./control-element-for-controls-for-view-format.md) define um controle que pode ser utilizado pela exibição e o nome que é utilizado para referenciar o controle.

[Controla o elemento de configuração (formato)](./controls-element-for-configuration-format.md) define os controles comuns que podem ser utilizados por todas as vistas do ficheiro de formatação.

[Controla o elemento para a exibição (formato)](./controls-element-for-view-format.md) define os controles de exibição que podem ser utilizados por uma vista específica.

[Elemento de CustomControl para controlo de configuração (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) define um controle. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de CustomControl para o controle para controles para exibição (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md) define um controle que é utilizado pela vista.

[Elemento de CustomControl para GroupBy (formato)](./customcontrol-element-for-groupby-format.md) define o controle personalizado que exibe o novo grupo.

[O elemento de CustomControl (formato)](./customcontrol-element-for-groupby-format.md) define um formato de controle personalizado para a vista.

[Elemento de CustomControlName para ExpressionBinding para controles de configuração (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) Especifica o nome de um controle comum. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de CustomControlName para ExpressionBindine para controles para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) Especifica o nome de um controle comum ou um controle de exibição. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de CustomControlName de GroupBy (formato)](./customcontrolname-element-for-groupby-format.md) Especifica o nome de um controle personalizado que é utilizado para apresentar o novo grupo. Este elemento é utilizado ao definir uma tabela, a lista, o modo de exibição control ampla ou personalizado.

[Elemento de CustomEntry para CustomControl para controles de configuração (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) fornece uma definição do controle comum. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de CustomEntry para CustomEntries para controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md) fornece uma definição do controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de CustomEntry para CustomEntries para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) fornece uma definição de vista do controle personalizado.

[Elemento de CustomEntry para CustomControl para GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md) fornece uma definição do controle. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de CustomEntries para CustomControl para a configuração (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) apresenta as definições de um controle comum. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de CustomEntries para CustomControl para controles para exibição (formato)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) fornece as definições para o controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de CustomEntries para CustomControl para GroupBy (formato)](./customentries-element-for-customcontrol-for-groupby-format.md) fornece as definições para o controle. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de CustomEntries para CustomControl para exibição (formato)](./customentries-element-for-customcontrol-for-view-format.md) fornece as definições de vista do controle personalizado. O modo de exibição do controle personalizado tem de especificar uma ou mais definições.

[Elemento de CustomItem para CustomEntry para controles para configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md) define os dados que são apresentados pelo controle e como ele é exibido. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de CustomItem para CustomEntry para controles para exibição (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md) define os dados que são apresentados pelo controle e como ele é exibido. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de CustomItem para CustomEntry para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) define os dados que são apresentados pela vista do controle personalizado e como ele é exibido. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md) define os dados que são apresentados pela vista do controle personalizado e como ele é exibido. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[O elemento de DefaultSettings (formato)](./defaultsettings-element-format.md) define configurações comuns que se aplicam a todas as vistas do ficheiro de formatação. Definições comuns incluem a exibição de erros, quebra de texto em tabelas, definir a forma como as coleções são expandidas e muito mais.

[O elemento de DisplayError (formato)](./displayerror-element-format.md) Especifica que a cadeia de caracteres #ERR é apresentada quando ocorre um erro de apresentar um conjunto de dados.

[Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) define os tipos do .NET que utilizam a definição de controle comum ou a condição que tem de existir para este controlo a ser utilizado. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de EntrySelectedBy para CustomEntry para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) define os tipos do .NET que utilizam esta entrada personalizada ou a condição que tem de existir para esta entrada a ser utilizado.

[Elemento de EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md) define os tipos do .NET que utilizam esta definição ou a condição que tem de existir para esta definição a utilizar.

[Elemento de EntrySelectedBy para CustomEntry para GroupBy (formato)](./entryselectedby-element-for-customentry-for-groupby-format.md) define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de EntrySelectedBy para ListEntry para ListControl (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) define os tipos do .NET que utilizam esta definição de vista de lista ou a condição que tem de existir para esta definição a utilizar. Na maioria dos casos, apenas uma definição é necessária para uma vista de lista. No entanto, pode fornecer várias definições para a vista de lista, se pretender utilizar a mesma vista de lista para apresentar dados diferentes para objetos diferentes.

[Elemento de EntrySelectedBy para TableRowEntry (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) define os tipos .NET cujos valores de propriedade são apresentados na linha.

[Elemento de EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md) define os tipos do .NET que utilizam esta definição da vista alargada ou a condição que tem de existir para esta definição a utilizar.

[O elemento de EnumerableExpansion (formato)](./enumerableexpansion-element-format.md) define a coleção de .NET como específica objetos são expandidos quando são apresentados numa vista.

[O elemento de EnumerableExpansions (formato)](./enumerableexpansions-element-format.md) define como os objetos da coleção de .NET são expandidos quando são apresentados numa vista.

[Elemento de EnumerateCollection para ExpressionBinding para controles de configuração (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) especificado que os elementos de coleções são apresentados pelo controle. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de EnumerateCollection para ExpressionBinding para controles para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) especificado que os elementos de coleções são apresentados. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de EnumerateCollection para a expressão de vinculação para CustomControl para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) Especifica que os elementos de coleções são apresentados. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de EnumerateCollection para ExpressionBinding para GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Especifica que os elementos de coleções são apresentados. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Expanda o elemento (formato)](./expand-element-format.md) Especifica como o objeto de coleção é expandido para esta definição.

[Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) define os dados que são apresentados pelo controle. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) define os dados que são apresentados pelo controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de ExpressionBinding para CustomItem para CustomControl para exibição (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) define os dados que são apresentados pelo controle. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de ExpressionBinding para CustomItem para GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md) define os dados que são apresentados pelo controle. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de FirstLineHanging para quadro para controles de configuração (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) Especifica o número de carateres a primeira linha dos dados é desviada à esquerda. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de FirstLineHanging do quadro de controles de exibição (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) Especifica o número de carateres a primeira linha dos dados é desviada à esquerda. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de FirstLineHanging para quadro para CustomControl para exibição (formato)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) Especifica o número de carateres a primeira linha dos dados é desviada à esquerda. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de FirstLineHanging para quadro para GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md) Especifica o número de carateres a primeira linha dos dados é desviada à esquerda. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de FirstLineIndent para quadro para controles de configuração (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) Especifica o número de carateres a primeira linha dos dados é desviada à direita. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de FirstLineIndent do quadro de controles de exibição (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) Especifica o número de carateres a primeira linha dos dados é desviada à direita. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) Especifica o número de carateres a primeira linha dos dados é desviada à direita. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de FirstLineIndent para quadro para GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md) Especifica o número de carateres a primeira linha dos dados é desviada à direita. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de FormatString para ListItem (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md) Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado.

[Elemento de FormatString para TableColumnItem (formato)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) Especifica um padrão de formato que define como o valor de propriedade ou do script da tabela é exibido.

[Elemento de FormatString para WideItem para WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md) Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado na vista.

[Estruturar o elemento para CustomItem para controles de configuração (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md) define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Estruturar o elemento para CustomItem para controles para exibição (formato)](./frame-element-for-customitem-for-controls-for-view-format.md) define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Estruturar o elemento para CustomItem para CustomControl para exibição (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Estruturar o elemento para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md) define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md) define como o Windows PowerShell apresenta um novo grupo de objetos.

[O elemento de HideTableHeaders (formato)](./hidetableheaders-element-format.md) Especifica que os cabeçalhos da tabela não são apresentados.

[Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) define a condição de que tem de existir para este controlo a ser utilizado. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) define a condição de que tem de existir para este controlo a ser utilizado. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de ItemSelectionCondition para a expressão de vinculação para CustomControl para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) define a condição de que tem de existir para este controlo a ser utilizado. Não existe nenhum limite para o número de condições de seleção que pode ser especificado para um item de controlo. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) define a condição de que tem de existir para este controlo a ser utilizado. Não existe nenhum limite para o número de condições de seleção que pode ser especificado para um item de controlo. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de ItemSelectionCondition para ListItem (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) define a condição de que tem de existir para este item de lista a ser utilizado.

[Elemento da etiqueta para ListItem para ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md) Especifica a etiqueta para o valor de propriedade ou um script na linha.

[Elemento da etiqueta para GroupBy (formato)](./label-element-for-groupby-format.md) Especifica uma etiqueta que é apresentada quando for detetado um novo grupo.

[Elemento da etiqueta para TableColumnHeader (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) define a etiqueta que é apresentada na parte superior de uma coluna.

[Elemento de LeftIndent para quadro para controles de configuração (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) Especifica o número de carateres de dados são desviados da margem esquerda. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de LeftIndent do quadro de controles de exibição (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md) Especifica o número de carateres de dados são desviados da margem esquerda. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de LeftIndent para quadro para CustomControl para exibição (formato)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) Especifica o número de carateres de dados são desviados da margem esquerda. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de LeftIndent para quadro para GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md) Especifica o número de carateres de dados são desviados da margem esquerda. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[ListControl elemento (formato)](./listcontrol-element-format.md) define um formato de lista para a vista.

[O elemento de ListEntry (formato)](./listentry-element-for-listcontrol-format.md) fornece uma definição de vista de lista.

[O elemento de ListEntries (formato)](./listentries-element-for-listcontrol-format.md) define a forma como são apresentadas as linhas da vista de lista.

[O elemento de ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md) define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.

[O elemento de ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md) define as propriedades e os scripts que são apresentados na vista de lista.

[Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md) Especifica o nome do controle. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de nome para SelectionSet (formato)](./name-element-for-selectionset-format.md) Especifica o nome utilizado para referenciar o conjunto de seleção.

[Elemento de nome para exibição (formato)](./name-element-for-view-format.md) Especifica o nome que é utilizado para identificar o modo de exibição.

[Elemento de nova linha para CustomItem para controles de configuração (formato)](./newline-element-for-customitem-for-controls-for-configuration-format.md) adiciona uma linha em branco para a exibição do controle. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de nova linha para CustomItem para controles para exibição (formato)](./newline-element-for-customitem-for-controls-for-view-format.md) adiciona uma linha em branco para a exibição do controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de nova linha para CustomItem para CustomControl para exibição (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) adiciona uma linha em branco para a exibição do controle. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de nova linha para CustomItem para GroupBy (formato)](./newline-element-for-customitem-for-groupby-format.md) adiciona uma linha em branco para a exibição do controle. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de PropertyName para ExpressionBinding para controles de configuração (formato)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) Especifica a propriedade de .NET cujo valor é apresentado pelo controle comum. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de PropertyName para ExpressionBinding para controles para exibição (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) Especifica a propriedade de .NET cujo valor é apresentado pelo controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de PropertyName para ExpressionBinding para CustomControl para exibição (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) Especifica a propriedade de .NET cujo valor é apresentado pelo controle. Este elemento é utilizado ao definir uma vista de controle personalizado

[Elemento de PropertyName para ExpressionBinding para GroupBy (formato)](./propertyname-element-for-expressionbinding-for-groupby-format.md) Especifica a propriedade de .NET cujo valor é apresentado pelo controle. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de PropertyName para GroupBy (formato)](./propertyname-element-for-groupby-format.md) Especifica a propriedade do .NET que inicia um novo grupo sempre que seu valor é alterado.

[Elemento de PropertyName para ItemSeclectionCondition para controles de configuração (formato)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de PropertyName para ItemSelectionCondition para controles para exibição (formato)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de PropertyName para ItemSelectionCondition para CustomControl para exibição (formato](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de PropertyName para ItemSelectionCondition para GroupBy (formato)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de PropertyName para ItemSelectionCondition para ListItem (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o modo de exibição é utilizado. Este elemento é utilizado ao definir uma vista de lista.

[Elemento de PropertyName para ListItem para ListControl (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md) Especifica a propriedade de .NET cujo valor é apresentado na lista.

[Elemento de PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a entrada é utilizada. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de PropertyName para SelectionCondition para controles para exibição (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a entrada é utilizada. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de PropertyName para SelectionCondition para CustomControl para exibição (formato)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a definição é utilizada. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a definição é utilizada.

[Elemento de PropertyName para SelectionCondition para GroupBy (formato)](./propertyname-element-for-selectioncondition-for-groupby-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a definição é utilizada. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e é utilizada a entrada da lista.

[Elemento de PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e é utilizada a entrada da tabela.

[Elemento de PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a definição é utilizada.

[Elemento de PropertyName para TableColumnItem (formato)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Especifica a propriedade cujo valor é apresentado na coluna da linha.

[Elemento de PropertyName para WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md) Especifica a propriedade do objeto cujo valor é apresentado na vista alargada.

[Elemento de RightIndent para quadro para controles de configuração (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) Especifica o número de carateres de dados são desviados da margem direita. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de RightIndent do quadro de controles de exibição (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md) Especifica o número de carateres de dados são desviados da margem direita. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de RightIndent](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) Especifica o número de carateres de dados são desviados da margem direita. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de RightIndent para quadro para GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md) Especifica o número de carateres de dados são desviados da margem direita. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de ScriptBlock para ExpressionBinding para controles de configuração (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) Especifica o script cujo valor é apresentado pelo controle comum. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de ScriptBlock para ExpressionBinding para controles para exibição (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) Especifica o script cujo valor é apresentado pelo controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de ScriptBlock para ExpressionBinding para CustomCustomControl para exibição (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) Especifica o script cujo valor é apresentado pelo controle. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de ScriptBlock para ExpressionBinding para GroupBy (formato)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) Especifica o script cujo valor é apresentado pelo controle. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de ScriptBlock para GroupBy (formato)](./scriptblock-element-for-groupby-format.md) Especifica o script que inicia um novo grupo sempre que seu valor é alterado.

[Elemento de ScriptBlock para ItemSelectionCondition para controles de configuração (formato)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de ScriptBlock para ItemSelectionCondition para controles para exibição (formato)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de ScriptBlock para ItemSelectionCondition para CustomControl para exibição (formato)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de ScriptBlock para ItemSelectionCondition para GroupBy (formato)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de ScriptBlock para ItemSelectionCondition para ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e é utilizado o item da lista. Este elemento é utilizado ao definir uma vista de lista.

[Elemento de ScriptBlock para ListItem (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md) Especifica o script cujo valor é apresentado na linha da lista.

[Elemento de ScriptBlock para SelectionCondition para controles de configuração (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e a definição é utilizada. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de ScriptBlock para SelectionCondition para controles para exibição (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e a definição é utilizada. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de ScriptBlock para SelectionCondition para CustomControl para exibição (formato)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e a definição é utilizada. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica o script que aciona a condição.

[Elemento de ScriptBlock para SelectionCondition para GroupBy (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e a definição é utilizada. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e é utilizada a entrada da lista.

[Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Especifica o bloco de script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e é utilizada a entrada da tabela.

[Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e é utilizada a definição de entrada ampla.

[Elemento de ScriptBlock para TableColumnItem (formato)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Especifica o script cujo valor é apresentado na coluna da linha.

[Elemento de ScriptBlock para WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Especifica o script cujo valor é apresentado na vista alargada.

[Elemento de SelectionCondition para EntrySelectedBy para CustomEntry para a configuração (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) define uma condição que tem de existir uma definição de controle comum a ser utilizado. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) define uma condição que tem de existir durante a definição de controlo a ser utilizado. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) define uma condição que tem de existir para obter uma definição de controlo a ser utilizado. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) define a condição de que tem de existir para expandir os objetos da coleção desta definição.

[Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) define uma condição que tem de existir para obter uma definição de controlo a ser utilizado. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) define a condição de que tem de existir para utilizar esta definição de vista de lista. Não existe nenhum limite para o número de condições de seleção que podem ser especificados para uma definição de lista.

[Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) define a condição de que tem de existir para utilizar para esta definição de vista de tabela. Não existe nenhum limite para o número de condições de seleção que podem ser especificados para uma definição de tabela.

[Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) define a condição de que tem de existir para esta definição a utilizar. Não existe nenhum limite para o número de condições de seleção que podem ser especificados para uma definição de entrada ampla.

[O elemento de SelectionSet (formato)](./selectionset-element-format.md) define um conjunto de objetos do .NET que pode ser referenciado pelo nome do conjunto.

[Elemento de SelectionSetName para EntrySelectedBy para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica um conjunto de tipos do .NET que utilizam esta definição do controle. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de SelectionSetName para EntrySelectedBy para controles para exibição (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) Especifica um conjunto de tipos do .NET que utilizam esta definição do controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de SelectionSetName para EntrySelectedBy para CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) Especifica um conjunto de objetos do .NET para a entrada da lista. Não existe nenhum limite para o número de conjuntos de seleção que podem ser especificados para uma entrada.

[Elemento de SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) Especifica o conjunto de tipos do .NET que são expandidas por esta definição.

[Elemento de SelectionSetName para EntrySelectedBy para GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) Especifica um conjunto de objetos do .NET para a entrada da lista. Não existe nenhum limite para o número de conjuntos de seleção que podem ser especificados para uma entrada. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de SelectionSetName para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) Especifica um conjunto de objetos do .NET para a entrada da lista. Não existe nenhum limite para o número de conjuntos de seleção que podem ser especificados para uma entrada.

[Elemento de SelectionSetName para EntrySelectedBy para TableRowEntry (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) Especifica a utilização de tipos de um conjunto de .NET, esta entrada da vista de tabela. Não existe nenhum limite para o número de conjuntos de seleção que podem ser especificados para uma entrada.

[Elemento de SelectionSetName para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) Especifica um conjunto de objetos do .NET para a definição. A definição é utilizada sempre que um desses objetos é apresentado.

[Elemento de SelectionSetName para SelectionCondition para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica o conjunto de tipos do .NET que acionam a condição. Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar este controlo. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de SelectionSetName para SelectionCondition para controles para exibição (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) Especifica o conjunto de tipos do .NET que acionam a condição. Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado com esse controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de EntrySelectedBy para CustomEntry para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Especifica o conjunto de tipos do .NET que acionam a condição. Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado com esse controle. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica o conjunto de tipos do .NET que acionam a condição. Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida.

[Elemento de SelectionSetName para SelectionCondition para GroupBy (formato)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) Especifica o conjunto de tipos do .NET que acionam a condição. Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar este controlo. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) Especifica o conjunto de tipos do .NET que acionam a condição. Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar esta definição de vista de lista.

[Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Especifica o conjunto de tipos do .NET que acionam a condição. Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar esta definição de vista de tabela.

[Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Especifica o conjunto de tipos do .NET que acionam a condição. Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar esta definição da vista ampla.

[Elemento de SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md) Especifica um conjunto de objetos do .NET que são apresentados pela exibição.

[O elemento de SelectionSets (formato)](./selectionsets-element-format.md) define os conjuntos de objetos do .NET que podem ser utilizados pelas vistas de formato individuais.

[O elemento de ShowError (formato)](./showerror-element-format.md) Especifica que o registo de erro completa é apresentado quando ocorre um erro ao apresentar um conjunto de dados.

[Elemento de TableColumnHeader para TableHeaders para TableControl (formato)](./tablecolumnheader-element-format.md) define a etiqueta, a largura da coluna e o alinhamento da etiqueta para uma coluna da tabela.

[O elemento de TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) define a propriedade ou um script cujo valor é apresentado na coluna da linha.

[O elemento de TableColumnItems (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) define as propriedades ou scripts cujos valores são apresentados na linha.

[O elemento de TableControl (formato)](./tablecontrol-element-format.md) define um formato de tabela para obter uma exibição.

[O elemento de TableHeaders (formato)](./tableheaders-element-format.md) define os cabeçalhos das colunas de uma tabela.

[O elemento de TableRowEntries (formato)](./tablerowentries-element-for-tablecontrol-format.md) define as linhas da tabela.

[O elemento de TableRowEntry (formato)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) define os dados que são apresentados numa linha da tabela.

[Elemento de texto para CustomItem para controles de configuração (formato)](./text-element-for-customitem-for-controls-for-configuration-format.md) Especifica texto adicionado aos dados que são apresentados por controle, como uma etiqueta, parêntesis Retos delimitar os dados e os espaços para recuar os dados. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de texto para CustomItem para controles para exibição (formato)](./text-element-for-customitem-for-controls-for-view-format.md) Especifica texto adicionado aos dados que são apresentados por controle, como uma etiqueta, parêntesis Retos delimitar os dados e os espaços para recuar os dados. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de texto para CustomItem (formato)](./text-element-for-customitem-for-customview-for-view-format.md) Especifica texto adicionado aos dados que são apresentados por controle, como uma etiqueta, parêntesis Retos delimitar os dados e os espaços para recuar os dados. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de texto para CustomItem para GroupBy (formato)](./text-element-for-customitem-for-groupby-format.md) Especifica texto adicionado aos dados que são apresentados por controle, como uma etiqueta, parêntesis Retos delimitar os dados e os espaços para recuar os dados. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de TypeName para EntrySelectedBy para controles de configuração (formato)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) Especifica um tipo .NET que utiliza esta definição do controle. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de TypeName para EntrySelectedBy para controles para exibição (formato)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) Especifica um tipo .NET que utiliza esta definição do controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de TypeName para EntrySelectedBy para CustomEntry para exibição (formato)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) Especifica um tipo .NET que utiliza esta definição de vista do controle personalizado. Não existe nenhum limite para o número de tipos que podem ser especificados para uma definição.

[Elemento de TypeName para EntrySelectedBy para EnumerableExpansion (formato)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) Especifica um tipo .NET que é expandido por esta definição. Este elemento é utilizado ao definir um predefinições.

[Elemento de TypeName para EntrySelectedBy para GroupBy (formato)](./typename-element-for-entryselectedby-for-groupby-format.md) Especifica um tipo .NET que utiliza esta definição do controle personalizado. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de TypeName para EntrySelectedBy para ListControl (formato)](./typename-element-for-entryselectedby-for-listcontrol-format.md) Especifica um tipo .NET que utiliza esta entrada da exibição de lista. Não existe nenhum limite para o número de tipos que podem ser especificados para uma entrada na lista.

[Elemento de TypeName para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) Especifica um tipo .NET que utiliza esta entrada da vista de tabela. Não existe nenhum limite para o número de tipos que podem ser especificados para uma entrada de tabela.

[Elemento de TypeName para EntrySelectedBy para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md) Especifica um tipo de .NET para a definição. A definição é utilizada sempre que este objeto é apresentado.

[Elemento de TypeName para SelectionCondition para controles de configuração (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) Especifica um tipo .NET que aciona a condição. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

[Elemento de TypeName para SelectionCondition para controles para exibição (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) Especifica um tipo .NET que aciona a condição. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

[Elemento de TypeName para SelectionCondition para CustomControl para exibição (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) Especifica um tipo .NET que aciona a condição. Este elemento é utilizado ao definir uma vista de controle personalizado.

[Elemento de TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Especifica um tipo .NET que aciona a condição.

[Elemento de TypeName para SelectionCondition para GroupBy (formato)](./typename-element-for-selectioncondition-for-groupby-format.md) Especifica um tipo .NET que aciona a condição. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

[Elemento de TypeName para SelectionCondition para EntrySelectedBy para ListControl (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Especifica um tipo .NET que aciona a condição. Quando este tipo está presente, é utilizada a entrada da lista.

[Elemento de TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Especifica um tipo .NET que aciona a condição. Quando este tipo está presente, a condição é cumprida e a linha da tabela é utilizada.

[Elemento de TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Especifica um tipo .NET que aciona a condição. Quando este tipo está presente, a definição é utilizada.

[Elemento de TypeName para tipos (formato)](./typename-element-for-types-format.md) Especifica o tipo de .NET de um objeto que pertence ao conjunto de seleção.

[Elemento de TypeName para ViewSelectedBy (formato)](./typename-element-for-viewselectedby-format.md) Especifica um objeto .NET que é apresentado pela vista.

[Tipos de elemento (formato)](./types-element-for-selectionset-format.md) define os objetos .NET na seleção definidas.

[Ver o elemento (formato)](./view-element-format.md) define uma vista que é utilizada para apresentar um ou mais objetos do .NET.

[O elemento de ViewDefinitions (formato)](./viewdefinitions-element-format.md) define os modos de exibição utilizados para apresentar os objetos.

[O elemento de ViewSelectedBy (formato)](./viewselectedby-element-format.md) define os objetos do .NET que são apresentados pela exibição.

[O elemento de WideControl (formato)](./widecontrol-element-format.md) define o formato de uma lista de toda a (o único valor) para a vista. Esta vista apresenta um valor de propriedade de único ou um valor de script para cada objeto.

[O elemento de WideEntries (formato)](./wideentries-element-for-widecontrol-format.md) fornece as definições da vista ampla. A vista alargada tem de especificar uma ou mais definições.

[O elemento de WideEntry (formato)](./wideentry-element-for-widecontrol-format.md) fornece uma definição da vista ampla.

[O elemento de WideItem (formato)](./wideitem-element-for-widecontrol-format.md) define a propriedade ou um script cujo valor é apresentado.

[O elemento de largura (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) define a largura (em carateres) de uma coluna.

[Encapsular o elemento (formato)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) Especifica que o texto que excede a largura da coluna é apresentado na próxima linha.

[O elemento de WrapTables (formato)](./wraptables-element-format.md) Especifica que os dados numa célula de tabela são movidos para a próxima linha se os dados são maiores do que a largura da coluna.

## <a name="see-also"></a>Veja Também

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
