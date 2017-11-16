---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 90e0ab3579e1840598cc3050c27db0b73ba6f69d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="new-temporaryfile"></a>Novo TemporaryFile
Por vezes nos scripts, terá de criar um ficheiro temporário. Pode facilmente fazê-com o **New-TemporaryFile** cmdlet:

PS c:\\ &gt; $tempFile = New-TemporaryFile

PS c:\\ &gt; $tempFile.FullName

C:\\utilizadores\\slee\\AppData\\Local\\Temp\\tmp375.tmp

