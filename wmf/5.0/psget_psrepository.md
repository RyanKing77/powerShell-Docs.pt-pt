---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9a9bdac652512640209c20e3deb20d7abc0142c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219536"
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="8d6ce-102">Registar um Repositório do PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d6ce-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="8d6ce-103">Pode configurar PowerShellGet operar contra repositórios internos.</span><span class="sxs-lookup"><span data-stu-id="8d6ce-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="8d6ce-104">Isto é feito utilizando as seguintes adições:</span><span class="sxs-lookup"><span data-stu-id="8d6ce-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="8d6ce-105">Registar-PSRepository: Regista um repositório para o utilizador atual.</span><span class="sxs-lookup"><span data-stu-id="8d6ce-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="8d6ce-106">Anular o registo PSRepository: Remove um repositório registado para o utilizador atual.</span><span class="sxs-lookup"><span data-stu-id="8d6ce-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="8d6ce-107">Set-PSRepository: Definir os valores para um repositório registado.</span><span class="sxs-lookup"><span data-stu-id="8d6ce-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="8d6ce-108">Get-PSRepository: Obter repositórios de todos os registado para o utilizador atual.</span><span class="sxs-lookup"><span data-stu-id="8d6ce-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="8d6ce-109">Depois de um repositório estiver registado, pode utilizar o módulo de localizar e instalar módulo para trabalhar com a mesma.</span><span class="sxs-lookup"><span data-stu-id="8d6ce-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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
