---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
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