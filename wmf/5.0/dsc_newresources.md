---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 64a00e041bbeeea117db43116b486e83dfe923b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688260"
---
# <a name="new-built-in-dsc-resources"></a><span data-ttu-id="669d9-102">Novos recursos de DSC incorporados</span><span class="sxs-lookup"><span data-stu-id="669d9-102">New built-in DSC resources</span></span>

<span data-ttu-id="669d9-103">WMF 5.0 RTM tem 4 novos recursos de DSC:</span><span class="sxs-lookup"><span data-stu-id="669d9-103">WMF 5.0 RTM has 4 new DSC resources:</span></span>
* <span data-ttu-id="669d9-104">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="669d9-104">WindowsFeatureSet</span></span>
* <span data-ttu-id="669d9-105">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="669d9-105">WindowsOptionalFeatureSet</span></span>
* <span data-ttu-id="669d9-106">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="669d9-106">ServiceSet</span></span>
* <span data-ttu-id="669d9-107">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="669d9-107">ProcessSet</span></span>

<span data-ttu-id="669d9-108">Estes recursos fornecem uma forma fácil de configurar várias instâncias usando uma chamada de recurso único.</span><span class="sxs-lookup"><span data-stu-id="669d9-108">These resources provide an easy way to configure multiple instances using a single resource call.</span></span>

## <a name="windowsfeatureset"></a><span data-ttu-id="669d9-109">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="669d9-109">WindowsFeatureSet</span></span>

```powershell
# Get the syntax of WindowsFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsFeatureSet -Syntax

WindowsFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [Ensure = [String]]
    [Source = [String]]
    [IncludeAllSubFeature = [Boolean]]
    [Credential = [PSCredential]]
    [LogPath = [String]]
}
```

## <a name="windowsoptionalfeatureset"></a><span data-ttu-id="669d9-110">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="669d9-110">WindowsOptionalFeatureSet</span></span>

```powershell
# Get the syntax of WindowsOptionalFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsOptionalFeatureSet -Syntax

WindowsOptionalFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    Ensure = [String]
    [Source = [String[]]]
    [RemoveFilesOnDisable = [Boolean]]
    [LogPath = [String]]
    [NoWindowsUpdateCheck = [Boolean]]
    [LogLevel = [String]]
}
```

## <a name="serviceset"></a><span data-ttu-id="669d9-111">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="669d9-111">ServiceSet</span></span>

```powershell
# Get the syntax of ServiceSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ServiceSet -Syntax

ServiceSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [StartupType = [String]]
    [BuiltInAccount = [String]]
    [State = [String]]
    [Ensure = [String]]
    [Credential = [PSCredential]]
}
```

## <a name="processset"></a><span data-ttu-id="669d9-112">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="669d9-112">ProcessSet</span></span>

```powershell
# Get the syntax of ProcessSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ProcessSet -Syntax

ProcessSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Path = [String[]]
    [Credential = [PSCredential]]
    [Ensure = [String]]
    [StandardOutputPath = [String]]
    [StandardErrorPath = [String]]
    [StandardInputPath = [String]]
    [WorkingDirectory = [String]]
}
```
