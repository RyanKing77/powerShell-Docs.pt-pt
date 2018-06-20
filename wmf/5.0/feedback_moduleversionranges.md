---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225696"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="5cdcd-102">Suporte de módulos para declarar intervalos de versão (1.\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="5cdcd-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="5cdcd-103">Combinado com **- MinimumVersion**, **- MaximumVersion** agora permite ao utilizador para o módulo get/importação dentro do intervalo específico.</span><span class="sxs-lookup"><span data-stu-id="5cdcd-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="5cdcd-104">O parâmetro também suporta **.** \*.</span><span class="sxs-lookup"><span data-stu-id="5cdcd-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="5cdcd-105">O exemplo seguinte mostra como funciona:</span><span class="sxs-lookup"><span data-stu-id="5cdcd-105">The following example shows how it works:</span></span>

<span data-ttu-id="5cdcd-106">Agora, pode combinar **- MinimumVersion** e **- MaximumVersion** para importar o módulo dentro do intervalo específico:</span><span class="sxs-lookup"><span data-stu-id="5cdcd-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
