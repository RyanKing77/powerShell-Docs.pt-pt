---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e6b54519d878ab572662075709beb4cf4454b0c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="clipboard-cmdlets"></a>Cmdlets de área de transferência
**Get-área de transferência** e **Set-área de transferência** tornar mais fácil para si transferir conteúdo de e para uma sessão do Windows PowerShell. Por exemplo, se utilizar o Explorador do Windows para copiar três ficheiros para a área de transferência (selecionando-los e premir `ctrl-c`, por exemplo), pode, em seguida, facilmente aceder ao conteúdo da área de transferência como uma lista de ficheiros:

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


Os cmdlets de área de transferência suporta imagens, ficheiros de áudio, listas de ficheiro e texto.
