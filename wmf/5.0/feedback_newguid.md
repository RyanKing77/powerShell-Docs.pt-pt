---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a>New-Guid
Muitas vezes, o script (ou talvez ao escrever um recurso de DSC), tem a necessidade de um identificador exclusivo. GUIDs funcionam bem e é fácil chamar a classe de .NET Framework Guid para gerar um, mas com um cmdlet faz com que esta mais detetável para utilizadores finais que já não estiver familiarizados com a classe do .NET Framework:

PS c:\\ &gt; novo Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d