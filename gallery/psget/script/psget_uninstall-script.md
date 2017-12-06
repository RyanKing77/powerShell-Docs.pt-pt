---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: "Script de desinstalação"
ms.openlocfilehash: 41f2b88ee81cf9f8c1a8c415ed658f29f4f08c3b
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2017
---
# <a name="uninstall-script"></a><span data-ttu-id="76eb4-103">Script de desinstalação</span><span class="sxs-lookup"><span data-stu-id="76eb4-103">Uninstall-Script</span></span>

<span data-ttu-id="76eb4-104">Desinstala um ficheiro de script que foi instalado através de PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="76eb4-104">Uninstalls a script file which was installed using PowerShellGet.</span></span>

## <a name="description"></a><span data-ttu-id="76eb4-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="76eb4-105">Description</span></span>

<span data-ttu-id="76eb4-106">O cmdlet de Script de desinstalação desinstala os ficheiros de script especificado instalado do repositório online.</span><span class="sxs-lookup"><span data-stu-id="76eb4-106">The Uninstall-Script cmdlet uninstalls the specified script files which were installed from the online repository.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="76eb4-107">Sintaxe de cmdlet</span><span class="sxs-lookup"><span data-stu-id="76eb4-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Uninstall-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="76eb4-108">Referência de ajuda online do cmdlet</span><span class="sxs-lookup"><span data-stu-id="76eb4-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="76eb4-109">Script de desinstalação</span><span class="sxs-lookup"><span data-stu-id="76eb4-109">Uninstall-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619789)

## <a name="example-commands"></a><span data-ttu-id="76eb4-110">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="76eb4-110">Example commands</span></span>

```powershell
Get-InstalledScript | Uninstall-Script -WhatIf
What if: Performing the operation "Uninstall-Script" on target "Version '2.5' of script 'Required-Script3'".
What if: Performing the operation "Uninstall-Script" on target "Version '1.0' of script 'Demo-Script'".
What if: Performing the operation "Uninstall-Script" on target "Version '2.5' of script 'Fabrikam-Script'".
What if: Performing the operation "Uninstall-Script" on target "Version '2.5' of script 'Fabrikam-ServerScript'".
What if: Performing the operation "Uninstall-Script" on target "Version '2.5' of script 'Required-Script1'".
What if: Performing the operation "Uninstall-Script" on target "Version '2.5' of script 'Required-Script2'".
What if: Performing the operation "Uninstall-Script" on target "Version '2.0' of script 'Script-WithDependencies2'".

Uninstall-Script Required-Script1 -WhatIf -RequiredVersion 2.5
What if: Performing the operation "Uninstall-Script" on target "Version '2.5' of script 'Required-Script1'".

Uninstall-Script Required-Script1 -WhatIf -MinimumVersion 2.0 -MaximumVersion 3.0
What if: Performing the operation "Uninstall-Script" on target "Version '2.5' of script 'Required-Script1'".

Get-InstalledScript -Name Script-WithDependencies2 | Uninstall-Script -WhatIf
What if: Performing the operation "Uninstall-Script" on target "Version '2.0' of script 'Script-WithDependencies2'".

Get-InstalledScript -Name Script-WithDependencies2 | Uninstall-Script -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Uninstall-Script" on target "Version '2.0' of script 'Script-WithDependencies2'".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "Y"): N

Uninstall-Script Required-Script1 -RequiredVersion 2.5 -Verbose
VERBOSE: Performing the operation "Uninstall-Script" on target "Version '2.5' of script 'Required-Script1'".
VERBOSE: Successfully uninstalled the script 'Required-Script1' from script base 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts'.

# Get-InstalledScript should not return the Required-Script1
Get-InstalledScript Required-Script1
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'Required-Script1'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:3142 char:9
+ PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
+ FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage

# Uninstall a specified prerelease version of a script
Uninstall-Script Required-Script1 -RequiredVersion 2.5.0-alpha -AllowPrerelease -Verbose
VERBOSE: Performing the operation "Uninstall-Script" on target "Version '2.5.0-alpha' of script 'Required-Script1'".
VERBOSE: Successfully uninstalled the script 'Required-Script1' from script base 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts'.

```

