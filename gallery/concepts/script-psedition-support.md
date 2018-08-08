---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Scripts com edições do PowerShell compatíveis
ms.openlocfilehash: 2313131fe17dcd9508db514883ae3dcb837fb07e
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587215"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="7e354-103">Scripts com edições do PowerShell compatíveis</span><span class="sxs-lookup"><span data-stu-id="7e354-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="7e354-104">Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.</span><span class="sxs-lookup"><span data-stu-id="7e354-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="7e354-105">**Edição Desktop:** incorporada no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows, tais como Server Core e o Ambiente de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="7e354-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="7e354-106">**Edição Core:** incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, tais como Servidor Nano e o IoT do Windows.</span><span class="sxs-lookup"><span data-stu-id="7e354-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="7e354-107">A edição em execução do PowerShell é apresentada na propriedade PSEdition da $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="7e354-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="7e354-108">Os autores de script podem impedir que um script em execução, a menos que ele é executado numa edição compatível do PowerShell com o parâmetro PSEdition num `#requires` instrução.</span><span class="sxs-lookup"><span data-stu-id="7e354-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="7e354-109">Os utilizadores da galeria do PowerShell podem encontrar a lista de scripts suportado numa edição específica do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e354-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="7e354-110">Scripts sem etiquetas PSEdition_Desktop e PSEdition_Core são considerados para funcionar bem, na edição de ambiente de trabalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e354-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="7e354-111">Obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="7e354-111">More details</span></span>

- [<span data-ttu-id="7e354-112">Módulos com Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7e354-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="7e354-113">Suporte de edições do PowerShell no PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="7e354-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)
