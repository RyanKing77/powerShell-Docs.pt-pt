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
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Invoking Cmdlets and Scripts Within a Cmdlet (Invocar Cmdlets e Scripts Através de um Cmdlet)

Um cmdlet pode invocar outros cmdlets e scripts a partir de entrada a processar o método do cmdlet. Isto permite-lhe adicionar a funcionalidade de scripts e cmdlets existentes ao seu cmdlet sem ter de reescrever o código.

## <a name="the-invoke-method"></a>A invocar método

Todos os cmdlets pode invocar um cmdlet existente ao chamar o [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método a partir de uma entrada a processar o método, tais como [ System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), que é substituído pelo cmdlet. No entanto, pode invocar apenas esses cmdlets que derivam diretamente a partir da [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Não é possível invocar um cmdlet que deriva de [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.

O [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método tem as seguintes variantes.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) essa variante invoca o objeto de cmdlet e retorna uma coleção de objetos do tipo de "T".

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) essa variante invoca o objeto de cmdlet e retorna um emumerator com rigidez de tipos. Essa variante permite ao utilizador a utilizar os objetos da coleção para efetuar operações personalizadas.

## <a name="examples"></a>Exemplos

|Exemplo|Descrição|
|-------------|-----------------|
|[Invocar Cmdlets num Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|Este exemplo mostra como invocar um cmdlet a partir de outro cmdlet.|
|[Invocar Scripts dentro de um Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|Este exemplo mostra como invocar um script que é fornecido para o cmdlet a partir de outro cmdlet.|

## <a name="see-also"></a>Consulte Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
