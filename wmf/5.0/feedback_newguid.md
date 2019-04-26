---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085331"
---
# <a name="new-guid"></a>New-Guid
Muitas vezes, o script (ou talvez escrever um recurso de DSC), tem a necessidade de um identificador exclusivo. GUIDs funcionam bem e é fácil chamar a classe Guid do .NET Framework para geração de um, mas ter um cmdlet torna isso mais detectáveis para os utilizadores finais que já não estiver familiarizados com a classe do .NET Framework:

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
