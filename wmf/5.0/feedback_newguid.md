---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="new-guid"></a>New-Guid
Muitas vezes, o script (ou talvez ao escrever um recurso de DSC), tem a necessidade de um identificador exclusivo. GUIDs funcionam bem e é fácil chamar a classe de .NET Framework Guid para gerar um, mas com um cmdlet faz com que esta mais detetável para utilizadores finais que já não estiver familiarizados com a classe do .NET Framework:

PS c:\\ &gt; novo Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
