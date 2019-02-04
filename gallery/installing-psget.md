---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Installing PowerShellGet (Instalar o PowerShellGet)
ms.openlocfilehash: 5c51cb1c7ea2538cc5f8503ce6c5d80edda70e15
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683878"
---
# <a name="installing-powershellget"></a>Installing PowerShellGet (Instalar o PowerShellGet)

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>O PowerShellGet é um módulo de incluído nas seguintes versões

- [Windows 10](https://www.microsoft.com/windows) ou mais recente
- [Windows Server 2016](/windows-server/windows-server) ou mais recente
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) ou mais recente
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Obter o módulo PowerShellGet para versões do PowerShell 3.0 e 4.0

- [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Obter a versão mais recente da galeria do PowerShell

- Antes de atualizar o PowerShellGet, sempre deve instalar o fornecedor mais recente do Nuget. Para tal, execute o seguinte numa sessão elevada do PowerShell.

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Para sistemas com o PowerShell 5.0 (ou mais recente) pode instalar o PowerShellGet mais recente

- Para fazer isso no Windows 10, Windows Server 2016, qualquer sistema com o WMF 5.0 ou 5.1 instalado ou qualquer sistema com o PowerShell 6, execute os seguintes comandos a partir de uma sessão elevada do PowerShell.

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- Utilize `Update-Module` para obter as versões mais recentes.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>Para sistemas com o PowerShell 3 ou 4 do PowerShell, que tem instalado o [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

- Utilize o cmdlet do PowerShellGet partir de uma sessão elevada do PowerShell abaixo para poupar os módulos para um diretório local

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Certifique-se de que os módulos do PowerShellGet e PackageManagment não são carregados em todos os outros processos.
- Eliminar conteúdo da `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` pastas.
- Volte a abrir a consola de PS com permissões elevadas, em seguida, execute os seguintes comandos.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
