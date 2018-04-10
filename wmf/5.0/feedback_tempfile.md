---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: ada4fcc0beb3eb74b099f221762341abbf2c3b4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Por vezes nos scripts, terá de criar um ficheiro temporário. Pode facilmente fazê-com o **New-TemporaryFile** cmdlet:

PS c:\\ &gt; $tempFile = New-TemporaryFile

PS c:\\ &gt; $tempFile.FullName

C:\\utilizadores\\slee\\AppData\\Local\\Temp\\tmp375.tmp