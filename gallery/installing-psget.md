---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, PowerShell, cmdlet, psget
title: Installing PowerShellGet (Instalar o PowerShellGet)
ms.openlocfilehash: 2d3ba8c4d4d4c7ee023c7e6a948a29d8f47ea242
ms.sourcegitcommit: 8d47eb41445ffaf10fcd68874e397c9a1703d898
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/29/2019
ms.locfileid: "68601412"
---
# <a name="installing-powershellget"></a><span data-ttu-id="b961a-103">Installing PowerShellGet (Instalar o PowerShellGet)</span><span class="sxs-lookup"><span data-stu-id="b961a-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="b961a-104">PowerShellGet é um módulo in-box nas seguintes versões</span><span class="sxs-lookup"><span data-stu-id="b961a-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="b961a-105">[Windows 10](https://www.microsoft.com/windows) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="b961a-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="b961a-106">[Windows Server 2016](/windows-server/windows-server) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="b961a-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="b961a-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) ou mais recente</span><span class="sxs-lookup"><span data-stu-id="b961a-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="b961a-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="b961a-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="b961a-109">Obter o módulo PowerShellGet para as versões 3,0 e 4,0 do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b961a-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="b961a-110">MSI de PackageManagement</span><span class="sxs-lookup"><span data-stu-id="b961a-110">PackageManagement MSI</span></span>](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="b961a-111">Obter a versão mais recente do Galeria do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b961a-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="b961a-112">Antes de atualizar o PowerShellGet, você deve sempre instalar o provedor de NuGet mais recente.</span><span class="sxs-lookup"><span data-stu-id="b961a-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="b961a-113">Para fazer isso, execute o seguinte em uma sessão do PowerShell com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="b961a-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="b961a-114">Para sistemas com o PowerShell 5,0 (ou mais recente), você pode instalar o PowerShellGet mais recente</span><span class="sxs-lookup"><span data-stu-id="b961a-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="b961a-115">Para fazer isso no Windows 10, no Windows Server 2016, em qualquer sistema com o WMF 5,0 ou 5,1 instalado ou em qualquer sistema com o PowerShell 6, execute os seguintes comandos em uma sessão do PowerShell com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="b961a-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- <span data-ttu-id="b961a-116">Use `Update-Module` para obter versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="b961a-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a><span data-ttu-id="b961a-117">Para sistemas que executam o PowerShell 3 ou o PowerShell 4, que instalaram o [MSI de PackageManagement](https://www.microsoft.com/download/details.aspx?id=51451)</span><span class="sxs-lookup"><span data-stu-id="b961a-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="b961a-118">Use o cmdlet do PowerShellGet abaixo de uma sessão do PowerShell com privilégios elevados para salvar os módulos em um diretório local</span><span class="sxs-lookup"><span data-stu-id="b961a-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="b961a-119">Verifique se os módulos PowerShellGet e PackageManagement não estão carregados em nenhum outro processo.</span><span class="sxs-lookup"><span data-stu-id="b961a-119">Ensure that PowerShellGet and PackageManagement modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="b961a-120">Exclua o `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` conteúdo `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` das pastas e.</span><span class="sxs-lookup"><span data-stu-id="b961a-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="b961a-121">Abra novamente o console do PS com permissões elevadas e, em seguida, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="b961a-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
