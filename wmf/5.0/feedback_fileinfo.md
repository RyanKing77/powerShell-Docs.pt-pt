---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 587f3f592f4aab53c95bbc6d37ea37d7f2364aec
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="updates-to-fileinfo-object"></a>Atualizações ao objeto FileInfo
Informação de versão pode enganadoras, especialmente nos casos em que o ficheiro foi corrigido. Esta versão do WMF 5.0 adiciona novos **FileVersionRaw** e **ProductVersionRaw** propriedades FileInfo objetos de script. Seguem-se as propriedades, tal como apresentado para o powershell.exe (partindo do princípio de $pid é o ID do processo do PowerShell):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117

