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
# <a name="clipboard-cmdlets"></a><span data-ttu-id="35298-102">Cmdlets de área de transferência</span><span class="sxs-lookup"><span data-stu-id="35298-102">Clipboard cmdlets</span></span>
<span data-ttu-id="35298-103">**Get-área de transferência** e **Set-área de transferência** tornar mais fácil para si transferir conteúdo de e para uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35298-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="35298-104">Por exemplo, se utilizar o Explorador do Windows para copiar três ficheiros para a área de transferência (selecionando-los e premir `ctrl-c`, por exemplo), pode, em seguida, facilmente aceder ao conteúdo da área de transferência como uma lista de ficheiros:</span><span class="sxs-lookup"><span data-stu-id="35298-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell 
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="35298-105">Os cmdlets de área de transferência suporta imagens, ficheiros de áudio, listas de ficheiro e texto.</span><span class="sxs-lookup"><span data-stu-id="35298-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

