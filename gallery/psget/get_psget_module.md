---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: "Obter módulo PowerShellGet"
ms.openlocfilehash: 7224cf5d71b98d51ca22c47a00ca382d34864bfb
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
<a name="get-powershellget-module"></a><span data-ttu-id="6dbe1-103">Obter módulo PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="6dbe1-103">Get PowerShellGet Module</span></span>
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="6dbe1-104">PowerShellGet é um módulo de na caixa as seguintes versões</span><span class="sxs-lookup"><span data-stu-id="6dbe1-104">PowerShellGet is an in-box module in the following releases</span></span>
- <span data-ttu-id="6dbe1-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="6dbe1-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) or newer</span></span>
- <span data-ttu-id="6dbe1-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="6dbe1-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) or newer</span></span>
- <span data-ttu-id="6dbe1-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="6dbe1-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="6dbe1-108">6 de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6dbe1-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="6dbe1-109">Obter módulo PowerShellGet para versões de PowerShell 3.0 e 4.0</span><span class="sxs-lookup"><span data-stu-id="6dbe1-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>
- [<span data-ttu-id="6dbe1-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="6dbe1-110">PackageManagement MSI</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

### <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="6dbe1-111">Obter a versão mais recente a partir da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="6dbe1-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="6dbe1-112">Antes de atualizar PowerShellGet, deve instalar sempre o fornecedor mais recente do Nuget.</span><span class="sxs-lookup"><span data-stu-id="6dbe1-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="6dbe1-113">Para tal, execute o seguinte numa sessão do PowerShell elevada.</span><span class="sxs-lookup"><span data-stu-id="6dbe1-113">To do that, run the following in an elevated PowerShell session.</span></span>
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="6dbe1-114">Para sistemas com o PowerShell 5.0 (ou mais recente) pode instalar o PowerShellGet mais recente</span><span class="sxs-lookup"><span data-stu-id="6dbe1-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span> 
- <span data-ttu-id="6dbe1-115">Para fazê-lo no Windows 10, Windows Server 2016, qualquer sistema com WMF 5.0 ou 5.1 instalado ou qualquer sistema com 6 do PowerShell, execute os seguintes comandos a partir de uma sessão elevada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6dbe1-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- <span data-ttu-id="6dbe1-116">Utilize o módulo de atualização para obter as versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="6dbe1-116">Use Update-Module to get newer versions.</span></span>
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a><span data-ttu-id="6dbe1-117">Para sistemas com o PowerShell 3 ou 4 do PowerShell, que tem instalado o [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="6dbe1-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span></span>

- <span data-ttu-id="6dbe1-118">Utilize PowerShellGet cmdlet a partir de uma sessão elevada do PowerShell abaixo para guardar os módulos para um diretório local</span><span class="sxs-lookup"><span data-stu-id="6dbe1-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- <span data-ttu-id="6dbe1-119">Certifique-se de que os módulos PowerShellGet e PackageManagment não estão carregados em quaisquer outros processos.</span><span class="sxs-lookup"><span data-stu-id="6dbe1-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="6dbe1-120">Eliminar conteúdos da `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` pastas.</span><span class="sxs-lookup"><span data-stu-id="6dbe1-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="6dbe1-121">Volte a abrir a consola de PS com permissões elevadas, em seguida, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="6dbe1-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force