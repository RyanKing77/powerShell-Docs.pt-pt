---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057303"
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="7ed0c-102">Cmdlets de área de transferência</span><span class="sxs-lookup"><span data-stu-id="7ed0c-102">Clipboard cmdlets</span></span>
<span data-ttu-id="7ed0c-103">**Get-Clipboard** e **área de transferência de conjunto** facilitar a transferência de conteúdo de e para uma sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7ed0c-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="7ed0c-104">Por exemplo, se usar o Windows Explorer para copiar o três arquivos na área de transferência (selecionando-os e pressionando `ctrl-c`, por exemplo), pode, em seguida, a acessar facilmente o conteúdo da área de transferência como uma lista de ficheiros:</span><span class="sxs-lookup"><span data-stu-id="7ed0c-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="7ed0c-105">Os cmdlets de área de transferência suporta imagens, arquivos de áudio, listas de ficheiro e texto.</span><span class="sxs-lookup"><span data-stu-id="7ed0c-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>
