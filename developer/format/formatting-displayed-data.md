---
title: Formatação apresentados dados | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065670"
---
# <a name="formatting-displayed-data"></a>Formatting Displayed Data (Formatar a Apresentação de Dados)

Pode especificar a forma como são apresentados os pontos de dados na sua lista, tabela ou vista alargada. Pode utilizar o `FormatString` elemento ao definir os itens de sua exibição, ou pode utilizar o `ScriptBlock` elemento para chamar o `FormatString` método nos dados.

## <a name="using-the-formatstring-element"></a>Usando o elemento de FormatString

No exemplo a seguir, o valor do `TotalProcessorTime` propriedade o [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto está formatado com o elemento de FormatString. o `TotalProcessorTime` propriedade

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



