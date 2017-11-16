---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a>Novo Guid
Muitas vezes, o script (ou talvez ao escrever um recurso de DSC), tem a necessidade de um identificador exclusivo. GUIDs funcionam bem e é fácil chamar a classe de .NET Framework Guid para gerar um, mas com um cmdlet faz com que esta mais detetável para utilizadores finais que já não estiver familiarizados com a classe do .NET Framework:

PS c:\\ &gt; novo Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d

