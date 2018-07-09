---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Installing PowerShellGet (Instalar o PowerShellGet)
ms.openlocfilehash: c385f7fbf6b688a11face9c3ebf4e6475a7b4c33
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893965"
---
# <a name="installing-powershellget"></a><span data-ttu-id="d83fc-103">Installing PowerShellGet (Instalar o PowerShellGet)</span><span class="sxs-lookup"><span data-stu-id="d83fc-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="d83fc-104">O PowerShellGet é um módulo de incluído nas seguintes versões</span><span class="sxs-lookup"><span data-stu-id="d83fc-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="d83fc-105">[Windows 10](https://www.microsoft.com/en-us/windows) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="d83fc-105">[Windows 10](https://www.microsoft.com/en-us/windows) or newer</span></span>
- <span data-ttu-id="d83fc-106">[Windows Server 2016](/windows-server/windows-server) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="d83fc-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="d83fc-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="d83fc-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="d83fc-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="d83fc-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="d83fc-109">Obter o módulo PowerShellGet para versões do PowerShell 3.0 e 4.0</span><span class="sxs-lookup"><span data-stu-id="d83fc-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="d83fc-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="d83fc-110">PackageManagement MSI</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="d83fc-111">Obter a versão mais recente da galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="d83fc-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="d83fc-112">Antes de atualizar o PowerShellGet, sempre deve instalar o fornecedor mais recente do Nuget.</span><span class="sxs-lookup"><span data-stu-id="d83fc-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="d83fc-113">Para tal, execute o seguinte numa sessão elevada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d83fc-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="d83fc-114">Para sistemas com o PowerShell 5.0 (ou mais recente) pode instalar o PowerShellGet mais recente</span><span class="sxs-lookup"><span data-stu-id="d83fc-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="d83fc-115">Para fazer isso no Windows 10, Windows Server 2016, qualquer sistema com o WMF 5.0 ou 5.1 instalado ou qualquer sistema com o PowerShell 6, execute os seguintes comandos a partir de uma sessão elevada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d83fc-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- <span data-ttu-id="d83fc-116">Utilize `Update-Module` para obter as versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="d83fc-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomen-usdownloaddetailsaspxid51451"></a><span data-ttu-id="d83fc-117">Para sistemas com o PowerShell 3 ou 4 do PowerShell, que tem instalado o [PackageManagement MSI](https://www.microsoft.com/en-us/download/details.aspx?id=51451)</span><span class="sxs-lookup"><span data-stu-id="d83fc-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/en-us/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="d83fc-118">Utilize o cmdlet do PowerShellGet partir de uma sessão elevada do PowerShell abaixo para poupar os módulos para um diretório local</span><span class="sxs-lookup"><span data-stu-id="d83fc-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="d83fc-119">Certifique-se de que os módulos do PowerShellGet e PackageManagment não são carregados em todos os outros processos.</span><span class="sxs-lookup"><span data-stu-id="d83fc-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="d83fc-120">Eliminar conteúdo da `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` pastas.</span><span class="sxs-lookup"><span data-stu-id="d83fc-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="d83fc-121">Volte a abrir a consola de PS com permissões elevadas, em seguida, execute os seguintes comandos.</span><span class="sxs-lookup"><span data-stu-id="d83fc-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```