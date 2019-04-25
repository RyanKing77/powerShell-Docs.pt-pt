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
# <a name="clipboard-cmdlets"></a>Cmdlets de área de transferência
**Get-Clipboard** e **área de transferência de conjunto** facilitar a transferência de conteúdo de e para uma sessão do Windows PowerShell. Por exemplo, se usar o Windows Explorer para copiar o três arquivos na área de transferência (selecionando-os e pressionando `ctrl-c`, por exemplo), pode, em seguida, a acessar facilmente o conteúdo da área de transferência como uma lista de ficheiros:

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


Os cmdlets de área de transferência suporta imagens, arquivos de áudio, listas de ficheiro e texto.
