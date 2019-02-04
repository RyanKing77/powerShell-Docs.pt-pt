---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5ac9566979e1b761249f5cc7c62ed44047a2b9f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685236"
---
# <a name="register-a-powershell-repository"></a>Registar um Repositório do PowerShell
Pode configurar o PowerShellGet para operar contra repositórios internos. Isso é feito ao utilizar as seguintes adições:
- Register-PSRepository: Registra um repositório para o utilizador atual.
- Unregister-PSRepository: Remove um repositório registado para o utilizador atual.
- Set-PSRepository: Definir valores para o repositório registado.
- Get-PSRepository: Obtenha repositórios tudo registados para o utilizador atual.

Depois de um repositório estiver registado, pode utilizar Find-Module e Install-Module para trabalhar com eles.

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
