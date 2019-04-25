---
title: Elemento de ScriptBlock para ItemSelectionCondition para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064718"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="ea097-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format) (Elemento ScriptBlock para ItemSelectionCondition para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="ea097-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="ea097-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="ea097-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ea097-104">Quando esse script é avaliado para `true`, a condição é cumprida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="ea097-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="ea097-105">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="ea097-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ea097-106">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para exibição (formato) ExpressionBinding elemento para CustomItem para controles para exibição (formato) Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato) ScriptBlock elemento para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="ea097-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ea097-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea097-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ea097-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ea097-108">Attributes and Elements</span></span>

<span data-ttu-id="ea097-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="ea097-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ea097-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ea097-110">Attributes</span></span>

<span data-ttu-id="ea097-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ea097-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ea097-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="ea097-112">Child Elements</span></span>

<span data-ttu-id="ea097-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ea097-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ea097-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="ea097-114">Parent Elements</span></span>

|<span data-ttu-id="ea097-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="ea097-115">Element</span></span>|<span data-ttu-id="ea097-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea097-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea097-117">Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="ea097-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="ea097-118">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="ea097-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ea097-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="ea097-119">Text Value</span></span>

<span data-ttu-id="ea097-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="ea097-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea097-121">Observações</span><span class="sxs-lookup"><span data-stu-id="ea097-121">Remarks</span></span>

<span data-ttu-id="ea097-122">Se este elemento é utilizado, não é possível especificar a [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="ea097-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea097-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ea097-123">See Also</span></span>

[<span data-ttu-id="ea097-124">Elemento de PropertyName para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="ea097-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="ea097-125">Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="ea097-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="ea097-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea097-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
