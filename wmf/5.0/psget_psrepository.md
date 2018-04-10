---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 269f4112704067f291728e4c1d745d68ec6ccd6f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="f74e5-102">Registar um Repositório do PowerShell</span><span class="sxs-lookup"><span data-stu-id="f74e5-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="f74e5-103">Pode configurar PowerShellGet operar contra repositórios internos.</span><span class="sxs-lookup"><span data-stu-id="f74e5-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="f74e5-104">Isto é feito utilizando as seguintes adições:</span><span class="sxs-lookup"><span data-stu-id="f74e5-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="f74e5-105">Registar-PSRepository: Regista um repositório para o utilizador atual.</span><span class="sxs-lookup"><span data-stu-id="f74e5-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="f74e5-106">Anular o registo PSRepository: Remove um repositório registado para o utilizador atual.</span><span class="sxs-lookup"><span data-stu-id="f74e5-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="f74e5-107">Set-PSRepository: Definir os valores para um repositório registado.</span><span class="sxs-lookup"><span data-stu-id="f74e5-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="f74e5-108">Get-PSRepository: Obter repositórios de todos os registado para o utilizador atual.</span><span class="sxs-lookup"><span data-stu-id="f74e5-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="f74e5-109">Depois de um repositório estiver registado, pode utilizar o módulo de localizar e instalar módulo para trabalhar com a mesma.</span><span class="sxs-lookup"><span data-stu-id="f74e5-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```