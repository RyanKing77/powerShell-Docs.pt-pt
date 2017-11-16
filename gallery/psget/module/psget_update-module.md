---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: "Módulo de atualização"
ms.openlocfilehash: 343c296dad2a3df35f13393b3796a1d484f5f535
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="update-module"></a>Módulo de atualização

Transfere e instala a versão mais recente dos módulos especificados a partir de uma galeria online no computador local.

## <a name="description"></a>Descrição

O cmdlet do módulo de atualização instala uma versão mais recente de um módulo do Windows PowerShell que foi instalado na galeria do online ao executar o módulo de instalação no computador local.

Por predefinição, a versão mais recente do módulo especificado disponível na Galeria online está instalada, a menos que especifique uma versão necessária. Pode atualizar um módulo existente, instalado, especificando o nome do módulo; Módulo de atualização procura $env: PSModulePath para o módulo que pretende atualizar.

Executar o módulo de atualização sem o parâmetro de nome de atualizações de todos os módulos que podem ser atualizados no computador local.

### <a name="notes"></a>Notas

- Este cmdlet é executado no Windows PowerShell 3.0 ou versões posteriores do Windows PowerShell, no Windows 7 ou Windows 2008 R2 e versões posteriores do Windows.
- O módulo que especificou com o parâmetro de nome não tenha sido instalado utilizando o módulo de instalação, ocorre um erro. Módulo de atualização só pode ser executada em módulos que instalou a Galeria online executando o módulo de instalação.
- Se tentar módulo de atualização ao atualizar binários que estão em utilização, o módulo de atualização devolve um erro que identifica os processos de problema e informa o utilizador para repetir o módulo de atualização depois de parar os processos.
- No PowerShell 5.0 ou versões mais recentes, quando o módulo de atualização atualiza um módulo, adiciona a versão mais recente (ou especificada) do módulo, pelo que as versões mais antigas e mais recentes são agora lado lado a lado no mesmo diretório. Seria útil para indicar, pelo que e para mostrar um exemplo de saída destes comandos.


## <a name="cmdlet-syntax"></a>Sintaxe de cmdlet
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Referência de ajuda online do cmdlet

[Módulo de atualização](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a>Comandos de exemplo

```powershell
PS C:\\windows\\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\\windows\\system32> Update-Module -Name ContosoServer
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```


###  <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>Atualize o módulo de TestDepWithNestedRequiredModules1 com dependências.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

