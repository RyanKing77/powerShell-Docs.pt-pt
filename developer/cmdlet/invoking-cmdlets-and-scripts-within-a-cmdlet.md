---
title: Invocar Cmdlets e Scripts dentro de um Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846243"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="cd946-102">Invoking Cmdlets and Scripts Within a Cmdlet (Invocar Cmdlets e Scripts Através de um Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="cd946-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="cd946-103">Um cmdlet pode invocar outros cmdlets e scripts a partir de entrada a processar o método do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cd946-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="cd946-104">Isto permite-lhe adicionar a funcionalidade de scripts e cmdlets existentes ao seu cmdlet sem ter de reescrever o código.</span><span class="sxs-lookup"><span data-stu-id="cd946-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="cd946-105">A invocar método</span><span class="sxs-lookup"><span data-stu-id="cd946-105">The Invoke Method</span></span>

<span data-ttu-id="cd946-106">Todos os cmdlets pode invocar um cmdlet existente ao chamar o [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método a partir de uma entrada a processar o método, tais como [ System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), que é substituído pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cd946-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="cd946-107">No entanto, pode invocar apenas esses cmdlets que derivam diretamente a partir da [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="cd946-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="cd946-108">Não é possível invocar um cmdlet que deriva de [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="cd946-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="cd946-109">O [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método tem as seguintes variantes.</span><span class="sxs-lookup"><span data-stu-id="cd946-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="cd946-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) essa variante invoca o objeto de cmdlet e retorna uma coleção de objetos do tipo de "T".</span><span class="sxs-lookup"><span data-stu-id="cd946-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="cd946-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) essa variante invoca o objeto de cmdlet e retorna um emumerator com rigidez de tipos.</span><span class="sxs-lookup"><span data-stu-id="cd946-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="cd946-112">Essa variante permite ao utilizador a utilizar os objetos da coleção para efetuar operações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="cd946-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="cd946-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cd946-113">Examples</span></span>

|<span data-ttu-id="cd946-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cd946-114">Example</span></span>|<span data-ttu-id="cd946-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd946-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd946-116">Invocar Cmdlets num Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cd946-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="cd946-117">Este exemplo mostra como invocar um cmdlet a partir de outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cd946-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="cd946-118">Invocar Scripts dentro de um Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cd946-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="cd946-119">Este exemplo mostra como invocar um script que é fornecido para o cmdlet a partir de outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cd946-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="cd946-120">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="cd946-120">See Also</span></span>

[<span data-ttu-id="cd946-121">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd946-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
