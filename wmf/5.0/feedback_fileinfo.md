---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 63c3b8237a9883b147380dfe9cb173107cea9aa9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225645"
---
# <a name="updates-to-fileinfo-object"></a>Atualizações do objeto FileInfo
Informação de versão pode enganadoras, especialmente nos casos em que o ficheiro foi corrigido. Esta versão do WMF 5.0 adiciona novos **FileVersionRaw** e **ProductVersionRaw** propriedades FileInfo objetos de script. Seguem-se as propriedades, tal como apresentado para o powershell.exe (partindo do princípio de $pid é o ID do processo do PowerShell):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
