---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 89e908969641afd9ad9541dcfedcc8eb6315d07c
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="7d9b5-102">Suporte de módulos para declarar intervalos de versão (1.\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="7d9b5-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="7d9b5-103">Combinado com **- MinimumVersion**, **- MaximumVersion** agora permite ao utilizador para o módulo get/importação dentro do intervalo específico.</span><span class="sxs-lookup"><span data-stu-id="7d9b5-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="7d9b5-104">O parâmetro também suporta **.** \*.</span><span class="sxs-lookup"><span data-stu-id="7d9b5-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="7d9b5-105">O exemplo seguinte mostra como funciona:</span><span class="sxs-lookup"><span data-stu-id="7d9b5-105">The following example shows how it works:</span></span>

<span data-ttu-id="7d9b5-106">Agora, pode combinar **- MinimumVersion** e **- MaximumVersion** para importar o módulo dentro do intervalo específico:</span><span class="sxs-lookup"><span data-stu-id="7d9b5-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
