---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085300"
---
# <a name="get-childitem-has--depth-parameter"></a>Tem de GET-ChildItem - parâmetro de profundidade
**Get-ChildItem** tem agora um **– profundidade** parâmetro, que utiliza com o **– Recurse** para limitar a recursão:

PS c:\\usuários\\slee\\Downloads\\exemplo&gt; Get-ChildItem-Recurse - profundidade de 0

Diretório: C:\\usuários\\slee\\Downloads\\exemplo

Nome de comprimento de LastWriteTime de modo

---- ------------- ------ ----

---1!d 4/14/2015 5 36 PM Depth0

-a---4/14/2015 1:19 PM 0 File1.txt

-a---4/14/2015 1:19 PM 0 File2.txt

-a---4/14/2015 1:19 PM 0 File3.txt

PS c:\\usuários\\slee\\Downloads\\exemplo&gt; Get-ChildItem-Recurse - 1 de profundidade

Diretório: C:\\usuários\\slee\\Downloads\\exemplo

Nome de comprimento de LastWriteTime de modo

---- ------------- ------ ----

---1!d 4/14/2015 5 36 PM Depth0

-a---4/14/2015 1:19 PM 0 File1.txt

-a---4/14/2015 1:19 PM 0 File2.txt

-a---4/14/2015 1:19 PM 0 File3.txt

Diretório: C:\\usuários\\slee\\Downloads\\exemplo\\Depth0

Nome de comprimento de LastWriteTime de modo

---- ------------- ------ ----

---1!d 4/14/2015 5 33 PM Depth1
