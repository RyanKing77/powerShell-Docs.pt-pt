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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849918"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="b14f7-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format) (Elemento CustomControlName para ExpressionBinding para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="b14f7-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="b14f7-103">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="b14f7-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="b14f7-104">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="b14f7-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b14f7-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração para o modo de exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para CustomItem de exibição (formato) Elemento para CustomEntry para o elemento de ExpressionBinding de exibição (formato) para o elemento de CustomControlName CustomItem (formato) para a ligação de expressão para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="b14f7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b14f7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b14f7-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b14f7-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="b14f7-107">Attributes and Elements</span></span>

<span data-ttu-id="b14f7-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="b14f7-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b14f7-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b14f7-109">Attributes</span></span>

<span data-ttu-id="b14f7-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b14f7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b14f7-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="b14f7-111">Child Elements</span></span>

<span data-ttu-id="b14f7-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b14f7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b14f7-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="b14f7-113">Parent Elements</span></span>

|<span data-ttu-id="b14f7-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b14f7-114">Element</span></span>|<span data-ttu-id="b14f7-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b14f7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b14f7-116">Elemento de ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="b14f7-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b14f7-117">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="b14f7-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b14f7-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="b14f7-118">Text Value</span></span>

<span data-ttu-id="b14f7-119">Especifique o nome do controle.</span><span class="sxs-lookup"><span data-stu-id="b14f7-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="b14f7-120">Observações</span><span class="sxs-lookup"><span data-stu-id="b14f7-120">Remarks</span></span>

<span data-ttu-id="b14f7-121">Pode criar controles comuns que podem ser utilizados por todas as vistas de um ficheiro de formatação e pode criar controles de exibição que podem ser utilizados por uma vista específica.</span><span class="sxs-lookup"><span data-stu-id="b14f7-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="b14f7-122">Os nomes desses controles são especificados pelos seguintes elementos.</span><span class="sxs-lookup"><span data-stu-id="b14f7-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="b14f7-123">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b14f7-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="b14f7-124">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b14f7-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="b14f7-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b14f7-125">See Also</span></span>

[<span data-ttu-id="b14f7-126">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b14f7-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="b14f7-127">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b14f7-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="b14f7-128">Elemento de ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="b14f7-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b14f7-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b14f7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
