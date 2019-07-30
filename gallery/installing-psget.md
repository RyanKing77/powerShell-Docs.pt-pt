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
# <a name="installing-powershellget"></a>Installing PowerShellGet (Instalar o PowerShellGet)

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet é um módulo in-box nas seguintes versões

- [Windows 10](https://www.microsoft.com/windows) ou mais recente
- [Windows Server 2016](/windows-server/windows-server) ou mais recente
- [Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) ou mais recente
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Obter o módulo PowerShellGet para as versões 3,0 e 4,0 do PowerShell

- [MSI de PackageManagement](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Obter a versão mais recente do Galeria do PowerShell

- Antes de atualizar o PowerShellGet, você deve sempre instalar o provedor de NuGet mais recente. Para fazer isso, execute o seguinte em uma sessão do PowerShell com privilégios elevados.

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Para sistemas com o PowerShell 5,0 (ou mais recente), você pode instalar o PowerShellGet mais recente

- Para fazer isso no Windows 10, no Windows Server 2016, em qualquer sistema com o WMF 5,0 ou 5,1 instalado ou em qualquer sistema com o PowerShell 6, execute os seguintes comandos em uma sessão do PowerShell com privilégios elevados.

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- Use `Update-Module` para obter versões mais recentes.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>Para sistemas que executam o PowerShell 3 ou o PowerShell 4, que instalaram o [MSI de PackageManagement](https://www.microsoft.com/download/details.aspx?id=51451)

- Use o cmdlet do PowerShellGet abaixo de uma sessão do PowerShell com privilégios elevados para salvar os módulos em um diretório local

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Verifique se os módulos PowerShellGet e PackageManagement não estão carregados em nenhum outro processo.
- Exclua o `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` conteúdo `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` das pastas e.
- Abra novamente o console do PS com permissões elevadas e, em seguida, execute os comandos a seguir.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
