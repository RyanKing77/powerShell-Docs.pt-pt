---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5280ef5ff95679dc8721be8f5f81031a4ffe796f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085253"
---
# <a name="updates-to-fileinfo-object"></a>Atualizações do objeto FileInfo
Informações de versão do ficheiro podem ser equivocado, particularmente em casos em que o ficheiro foi corrigido. Esta versão do WMF 5.0 adiciona novos **FileVersionRaw** e **ProductVersionRaw** propriedades para objetos FileInfo do script. Aqui estão as propriedades, tal como apresentado para powershell.exe (partindo do princípio de $pid é o ID do processo do PowerShell):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
