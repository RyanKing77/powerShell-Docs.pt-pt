---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: "Obter módulo PowerShellGet"
ms.openlocfilehash: a5a323b17709e519ec57623a9dd7499e591bbed5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
<a name="get-powershellget-module"></a>Obter módulo PowerShellGet
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet é um módulo de na caixa as seguintes versões
- [Windows 10](https://www.microsoft.com/en-us/windows/get-windows-10) ou mais recente
- [Windows Server 2016](https://technet.microsoft.com/en-us/windows-server-docs/get-started/windows-server-2016) ou mais recente
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) ou mais recente
- [6 de PowerShell](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Obter módulo PowerShellGet para versões de PowerShell 3.0 e 4.0
- [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

### <a name="get-the-latest-version-from-powershell-gallery"></a>Obter a versão mais recente a partir da galeria do PowerShell

- Antes de atualizar PowerShellGet, deve instalar sempre o fornecedor mais recente do Nuget. Para tal, execute o seguinte numa sessão do PowerShell elevada.
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Para sistemas com o PowerShell 5.0 (ou mais recente) pode instalar o PowerShellGet mais recente 
- Para fazê-lo no Windows 10, Windows Server 2016, qualquer sistema com WMF 5.0 ou 5.1 instalado ou qualquer sistema com 6 do PowerShell, execute os seguintes comandos a partir de uma sessão elevada do PowerShell.
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- Utilize o módulo de atualização para obter as versões mais recentes.
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a>Para sistemas com o PowerShell 3 ou 4 do PowerShell, que tem instalado o [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

- Utilize PowerShellGet cmdlet a partir de uma sessão elevada do PowerShell abaixo para guardar os módulos para um diretório local

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- Certifique-se de que os módulos PowerShellGet e PackageManagment não estão carregados em quaisquer outros processos.
- Eliminar conteúdos da `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` e `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` pastas.
- Volte a abrir a consola de PS com permissões elevadas, em seguida, execute os seguintes comandos.

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force