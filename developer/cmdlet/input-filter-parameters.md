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
# <a name="input-filter-parameters"></a>Input Filter Parameters (Parâmetros de Filtro de Entrada)

Pode definir um cmdlet `Filter`, `Include`, e `Exclude` parâmetros filtrar o conjunto de objetos de entrada que afeta o cmdlet.

Normalmente, o conjunto de objetos de entrada é especificado por uma `InputObject`, `Path`, ou `Name` parâmetro. Por exemplo, um cmdlet pode ter um `Path` parâmetro que aceita vários caminhos com carateres universais e cada pontos do caminho para um objeto de entrada. Utilizados em conjunto, o `Filter`, `Include`, e `Exclude` ainda mais parâmetros qualificam os caminhos do cmdlet funciona em cada vez que for solicitada.

## <a name="include-and-exclude-parameters"></a>Incluir e excluir parâmetros

O `Include` e `Exclude` parâmetros identificam os objetos que estão incluídos ou excluídos do conjunto de objetos de entrada transmitido para o cmdlet. Utilize estes parâmetros quando o filtro pode ser expresso no idioma padrão universal. (Para obter mais informações sobre os carateres universais, consulte [dar suporte a curingas nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).) O `Include` parâmetro inclui todos os objetos cujos nomes correspondam ao filtro inclusão. O `Exclude` parâmetro exclui todos os objetos cujos nomes correspondam ao filtro.

## <a name="filter-parameter"></a>Parâmetro de filtro

O `Filter` parâmetro especifica o filtro que não é expressa no idioma padrão universal. Por exemplo, Active Directory Service Interfaces (ADSI) ou SQL filtros podem ser transferidos para o cmdlet por meio de seu `Filter` parâmetro. Nos cmdlets fornecidos pelo Windows PowerShell, estes filtros são especificados pelos fornecedores de Windows PowerShell que utilizam o cmdlet para aceder a um arquivo de dados. Cada fornecedor normalmente define seu próprio filtro.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Se não for especificado nenhum conjunto de objetos de entrada de filtragem

Se não for especificado nenhum conjunto de objetos de entrada, isso normalmente significa filtrar em relação a todos os objetos. Para obter mais informações, consulte[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)