---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Obter informações sobre os comandos
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: f4238927f10b4204cd3e23f0b0453011f54cb04a
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134015"
---
# <a name="getting-information-about-commands"></a>Obter informações sobre os comandos

O PowerShell `Get-Command` apresenta os comandos que estão disponíveis na sua sessão atual.
Quando executa o `Get-Command` cmdlet, verá algo semelhante à seguinte saída:

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

Esta saída se parece muito como a saída de ajuda de Cmd.exe: um resumo em tabela de comandos internos. No trecho do `Get-Command` comando mostrada acima, cada comando mostrado de saída tem um CommandType de Cmdlet. Um cmdlet é o tipo de comando intrínsecos do PowerShell. Este tipo corresponde mais ou menos para comandos como `dir` e `cd` em Cmd.exe ou os comandos internos de Unix shells, como bash.

O `Get-Command` cmdlet tem um **sintaxe** parâmetro que retorna a sintaxe de cada cmdlet. O exemplo seguinte mostra como obter a sintaxe do `Get-Help` cmdlet:

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>Exibição de comando disponíveis por tipo

O `Get-Command` comando lista apenas os cmdlets na sessão atual. Na verdade, o PowerShell suporta vários outros tipos de comandos:

- Aliases
- Funções
- Scripts

Arquivos executáveis externos ou ficheiros que tenham um manipulador de tipo de ficheiros registada, também estão classificados como comandos.

Para obter todos os comandos na sessão, escreva:

```powershell
Get-Command *
```

Esta lista inclui os comandos externos no seu caminho de pesquisa para que ele pode conter milhares de itens.
É mais útil examinar um conjunto reduzido de comandos.

> [!NOTE]
> O asterisco (\*) é utilizado para o caráter universal correspondente nos argumentos de comando do PowerShell. O \* significa "corresponde uma ou mais das quaisquer carateres". Pode digitar `Get-Command a*` para localizar todos os comandos que começam com a letra "a". Ao contrário de caráter universal correspondente no Cmd.exe, universais do PowerShell também corresponderá um período.

Utilize o **CommandType** parâmetro do `Get-Command` para obter comandos nativos de outros tipos.
cmdlet.

Para obter os aliases de comandos, que são os nicknames atribuídos de comandos, escreva:

```powershell
Get-Command -CommandType Alias
```

Para obter as funções na sessão atual, escreva:

```powershell
Get-Command -CommandType Function
```

Para ver scripts no caminho de pesquisa do PowerShell, escreva:

```powershell
Get-Command -CommandType Script
```