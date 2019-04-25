---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057515"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Suporte de módulos para a declaração de intervalos de versão (1. *, etc.)
Combinado com **- MinimumVersion**, **- MaximumVersion** agora permite que o utilizador para o módulo de importação/get dentro do intervalo específico. O parâmetro também suporta **.** \*. O exemplo seguinte mostra como ele funciona:

Agora, pode combinar **- MinimumVersion** e **- MaximumVersion** para importar o módulo dentro do intervalo específico:

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
