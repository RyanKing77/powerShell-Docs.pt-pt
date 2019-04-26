---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Scripts com edições do PowerShell compatíveis
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084696"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="40d67-103">Scripts com edições do PowerShell compatíveis</span><span class="sxs-lookup"><span data-stu-id="40d67-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="40d67-104">Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.</span><span class="sxs-lookup"><span data-stu-id="40d67-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="40d67-105">**Edição Desktop:** Criado no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows como núcleo de servidor e Desktop do Windows.</span><span class="sxs-lookup"><span data-stu-id="40d67-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="40d67-106">**Edição Core:** Incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, como o servidor Nano e o Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="40d67-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="40d67-107">A edição em execução do PowerShell é apresentada na propriedade PSEdition da $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="40d67-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

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

<span data-ttu-id="40d67-108">Os autores de script podem impedir que um script em execução, a menos que ele é executado numa edição compatível do PowerShell com o parâmetro PSEdition num `#requires` instrução.</span><span class="sxs-lookup"><span data-stu-id="40d67-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

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

<span data-ttu-id="40d67-109">Os utilizadores da galeria do PowerShell podem encontrar a lista de scripts suportado numa edição específica do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40d67-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="40d67-110">Scripts sem etiquetas PSEdition_Desktop e PSEdition_Core são considerados para funcionar bem, na edição de ambiente de trabalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40d67-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="40d67-111">Obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="40d67-111">More details</span></span>

- [<span data-ttu-id="40d67-112">Módulos com Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="40d67-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="40d67-113">Suporte de edições do PowerShell no PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="40d67-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)
