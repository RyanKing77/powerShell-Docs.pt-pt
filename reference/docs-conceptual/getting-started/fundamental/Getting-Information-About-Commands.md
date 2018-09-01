---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Obter informações sobre os comandos
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353175"
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

Esta saída se parece muito como a saída de ajuda de **cmd.exe**: um resumo em tabela de comandos internos. No trecho do `Get-Command` comando mostrada acima, cada comando mostrado de saída tem um CommandType de Cmdlet. Um cmdlet é o tipo de comando intrínsecos do PowerShell. Este tipo corresponde mais ou menos para comandos como `dir` e `cd` na **cmd.exe** ou os comandos internos de shells do Unix, como bash.

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
> O asterisco (\*) é utilizado para o caráter universal correspondente nos argumentos de comando do PowerShell. O \* significa "corresponde uma ou mais das quaisquer carateres". Pode digitar `Get-Command a*` para localizar todos os comandos que começam com a letra "a". Ao contrário de correspondência de carateres universais no **cmd.exe**, universais do PowerShell irão também de coincidir com um período.

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