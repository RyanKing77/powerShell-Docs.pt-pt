---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9a9bdac652512640209c20e3deb20d7abc0142c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="register-a-powershell-repository"></a>Registar um Repositório do PowerShell
Pode configurar PowerShellGet operar contra repositórios internos. Isto é feito utilizando as seguintes adições:
- Registar-PSRepository: Regista um repositório para o utilizador atual.
- Anular o registo PSRepository: Remove um repositório registado para o utilizador atual.
- Set-PSRepository: Definir os valores para um repositório registado.
- Get-PSRepository: Obter repositórios de todos os registado para o utilizador atual.

Depois de um repositório estiver registado, pode utilizar o módulo de localizar e instalar módulo para trabalhar com a mesma.

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
