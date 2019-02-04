---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685110"
---
# <a name="new-guid"></a>New-Guid
Muitas vezes, o script (ou talvez escrever um recurso de DSC), tem a necessidade de um identificador exclusivo. GUIDs funcionam bem e é fácil chamar a classe Guid do .NET Framework para geração de um, mas ter um cmdlet torna isso mais detectáveis para os utilizadores finais que já não estiver familiarizados com a classe do .NET Framework:

PS C:\\&gt; New-Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
