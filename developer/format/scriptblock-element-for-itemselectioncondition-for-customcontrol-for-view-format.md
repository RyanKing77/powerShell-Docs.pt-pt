---
title: Elemento de ScriptBlock para ItemSelectionCondition para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851178"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="1065a-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format) (Elemento ScriptBlock para ItemSelectionCondition para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="1065a-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="1065a-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="1065a-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1065a-104">Quando esse script é avaliado para `true`, a condição é cumprida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="1065a-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="1065a-105">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="1065a-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="1065a-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato) CustomItem elemento para CustomEntry para exibição (formato) ExpressionBinding elemento para CustomItem para CustomControl para exibição (formato) ItemSelectionCondition elemento para a ligação de expressão para CustomControl para exibição (formato) ScriptBlock elemento para ItemSelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="1065a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1065a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1065a-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1065a-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="1065a-108">Attributes and Elements</span></span>

<span data-ttu-id="1065a-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="1065a-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1065a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1065a-110">Attributes</span></span>

<span data-ttu-id="1065a-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1065a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1065a-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="1065a-112">Child Elements</span></span>

<span data-ttu-id="1065a-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1065a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1065a-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="1065a-114">Parent Elements</span></span>

|<span data-ttu-id="1065a-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="1065a-115">Element</span></span>|<span data-ttu-id="1065a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="1065a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1065a-117">Elemento de ItemSelectionCondition para enlace de expressão para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="1065a-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="1065a-118">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="1065a-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1065a-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="1065a-119">Text Value</span></span>

<span data-ttu-id="1065a-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="1065a-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1065a-121">Observações</span><span class="sxs-lookup"><span data-stu-id="1065a-121">Remarks</span></span>

<span data-ttu-id="1065a-122">Se este elemento é utilizado, não é possível especificar a [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="1065a-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="1065a-123">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="1065a-123">See Also</span></span>

[<span data-ttu-id="1065a-124">Elemento de PropertyName para ItemSelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="1065a-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1065a-125">Elemento de ItemSelectionCondition para enlace de expressão para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="1065a-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="1065a-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1065a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
