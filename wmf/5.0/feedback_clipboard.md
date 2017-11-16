---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 8d5f8cc8c85d584b195483e464e878857629a78e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
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

