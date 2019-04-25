---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: aa2e9540af8b3d4c5de5e00377a84e0e5edd6e4a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057861"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
Por vezes, nos seus scripts, tem de criar um arquivo temporário. Pode fazê-lo com facilidade, o **New-TemporaryFile** cmdlet:

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\usuários\\slee\\AppData\\Local\\Temp\\tmp375.tmp
