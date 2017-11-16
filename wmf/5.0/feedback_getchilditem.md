---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="get-childitem-has--depth-parameter"></a>Tem de GET-ChildItem - parâmetro de profundidade
**Get-ChildItem** tem agora um **– profundidade** parâmetro a utilizar com **-Recurse** para limitar a recursão:

PS c:\\utilizadores\\slee\\transfere\\exemplo&gt; Get-ChildItem-Recurse - profundidade 0

Diretório: C\\utilizadores\\slee\\transfere\\exemplo

Nome de comprimento de LastWriteTime modo

---- ------------- ------ ----

---d 4/14/2015 as 17:36:00 Depth0

-a---4/14/2015 1:19 PM 0 File1.txt

-a---4/14/2015 1:19 PM 0 File2.txt

-a---4/14/2015 1:19 PM 0 File3.txt

PS c:\\utilizadores\\slee\\transfere\\exemplo&gt; Get-ChildItem-Recurse - profundidade 1

Diretório: C\\utilizadores\\slee\\transfere\\exemplo

Nome de comprimento de LastWriteTime modo

---- ------------- ------ ----

---d 4/14/2015 as 17:36:00 Depth0

-a---4/14/2015 1:19 PM 0 File1.txt

-a---4/14/2015 1:19 PM 0 File2.txt

-a---4/14/2015 1:19 PM 0 File3.txt

Diretório: C\\utilizadores\\slee\\transfere\\exemplo\\Depth0

Nome de comprimento de LastWriteTime modo

---- ------------- ------ ----

---d 4/14/2015 5:33 PM Depth1

