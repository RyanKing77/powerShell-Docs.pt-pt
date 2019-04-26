---
title: Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066622"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="436c6-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format) (Elemento CustomControlName para ExpressionBinding para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="436c6-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="436c6-103">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="436c6-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="436c6-104">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="436c6-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="436c6-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração para o modo de exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para CustomItem de exibição (formato) Elemento para CustomEntry para o elemento de ExpressionBinding de exibição (formato) para o elemento de CustomControlName CustomItem (formato) para a ligação de expressão para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="436c6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="436c6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="436c6-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="436c6-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="436c6-107">Attributes and Elements</span></span>

<span data-ttu-id="436c6-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="436c6-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="436c6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="436c6-109">Attributes</span></span>

<span data-ttu-id="436c6-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="436c6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="436c6-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="436c6-111">Child Elements</span></span>

<span data-ttu-id="436c6-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="436c6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="436c6-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="436c6-113">Parent Elements</span></span>

|<span data-ttu-id="436c6-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="436c6-114">Element</span></span>|<span data-ttu-id="436c6-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="436c6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="436c6-116">Elemento de ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="436c6-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="436c6-117">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="436c6-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="436c6-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="436c6-118">Text Value</span></span>

<span data-ttu-id="436c6-119">Especifique o nome do controle.</span><span class="sxs-lookup"><span data-stu-id="436c6-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="436c6-120">Observações</span><span class="sxs-lookup"><span data-stu-id="436c6-120">Remarks</span></span>

<span data-ttu-id="436c6-121">Pode criar controles comuns que podem ser utilizados por todas as vistas de um ficheiro de formatação e pode criar controles de exibição que podem ser utilizados por uma vista específica.</span><span class="sxs-lookup"><span data-stu-id="436c6-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="436c6-122">Os nomes desses controles são especificados pelos seguintes elementos.</span><span class="sxs-lookup"><span data-stu-id="436c6-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="436c6-123">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="436c6-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="436c6-124">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="436c6-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="436c6-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="436c6-125">See Also</span></span>

[<span data-ttu-id="436c6-126">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="436c6-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="436c6-127">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="436c6-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="436c6-128">Elemento de ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="436c6-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="436c6-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="436c6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
