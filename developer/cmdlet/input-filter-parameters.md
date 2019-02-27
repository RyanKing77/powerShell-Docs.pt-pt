---
title: Parâmetros de filtro de entradas | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845739"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="babac-102">Input Filter Parameters (Parâmetros de Filtro de Entrada)</span><span class="sxs-lookup"><span data-stu-id="babac-102">Input Filter Parameters</span></span>

<span data-ttu-id="babac-103">Pode definir um cmdlet `Filter`, `Include`, e `Exclude` parâmetros filtrar o conjunto de objetos de entrada que afeta o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="babac-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="babac-104">Normalmente, o conjunto de objetos de entrada é especificado por uma `InputObject`, `Path`, ou `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="babac-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="babac-105">Por exemplo, um cmdlet pode ter um `Path` parâmetro que aceita vários caminhos com carateres universais e cada pontos do caminho para um objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="babac-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="babac-106">Utilizados em conjunto, o `Filter`, `Include`, e `Exclude` ainda mais parâmetros qualificam os caminhos do cmdlet funciona em cada vez que for solicitada.</span><span class="sxs-lookup"><span data-stu-id="babac-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="babac-107">Incluir e excluir parâmetros</span><span class="sxs-lookup"><span data-stu-id="babac-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="babac-108">O `Include` e `Exclude` parâmetros identificam os objetos que estão incluídos ou excluídos do conjunto de objetos de entrada transmitido para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="babac-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="babac-109">Utilize estes parâmetros quando o filtro pode ser expresso no idioma padrão universal.</span><span class="sxs-lookup"><span data-stu-id="babac-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="babac-110">(Para obter mais informações sobre os carateres universais, consulte [dar suporte a curingas nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).) O `Include` parâmetro inclui todos os objetos cujos nomes correspondam ao filtro inclusão.</span><span class="sxs-lookup"><span data-stu-id="babac-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="babac-111">O `Exclude` parâmetro exclui todos os objetos cujos nomes correspondam ao filtro.</span><span class="sxs-lookup"><span data-stu-id="babac-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="babac-112">Parâmetro de filtro</span><span class="sxs-lookup"><span data-stu-id="babac-112">Filter Parameter</span></span>

<span data-ttu-id="babac-113">O `Filter` parâmetro especifica o filtro que não é expressa no idioma padrão universal.</span><span class="sxs-lookup"><span data-stu-id="babac-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="babac-114">Por exemplo, Active Directory Service Interfaces (ADSI) ou SQL filtros podem ser transferidos para o cmdlet por meio de seu `Filter` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="babac-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="babac-115">Nos cmdlets fornecidos pelo Windows PowerShell, estes filtros são especificados pelos fornecedores de Windows PowerShell que utilizam o cmdlet para aceder a um arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="babac-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="babac-116">Cada fornecedor normalmente define seu próprio filtro.</span><span class="sxs-lookup"><span data-stu-id="babac-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="babac-117">Se não for especificado nenhum conjunto de objetos de entrada de filtragem</span><span class="sxs-lookup"><span data-stu-id="babac-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="babac-118">Se não for especificado nenhum conjunto de objetos de entrada, isso normalmente significa filtrar em relação a todos os objetos.</span><span class="sxs-lookup"><span data-stu-id="babac-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="babac-119">Para obter mais informações, consulte[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="babac-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="babac-120">Veja Também</span><span class="sxs-lookup"><span data-stu-id="babac-120">See Also</span></span>

[<span data-ttu-id="babac-121">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="babac-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)