---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Por vezes nos scripts, terá de criar um ficheiro temporário. Pode facilmente fazê-com o **New-TemporaryFile** cmdlet:

PS c:\\ &gt; $tempFile = New-TemporaryFile

PS c:\\ &gt; $tempFile.FullName

C:\\utilizadores\\slee\\AppData\\Local\\Temp\\tmp375.tmp
