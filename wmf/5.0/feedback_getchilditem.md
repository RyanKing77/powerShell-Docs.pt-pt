---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221906"
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
