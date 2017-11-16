---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Obter informações sobre os comandos"
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="getting-information-about-commands"></a>Obter informações sobre os comandos
O Windows PowerShell **Get-Command** cmdlet obtém todos os comandos que estão disponíveis na sua sessão atual. Quando escrever **Get-Command** na linha de comandos do Windows PowerShell, aparece um resultado semelhante ao seguinte:

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

Isto de saída procura muito semelhante a saída de ajuda do Cmd.exe: um resumo dos comandos internos tabular. No excerpt do **Get-Command** comando saída mostrada acima, cada comando mostrado tem um CommandType de Cmdlet. Um cmdlet é o tipo de comando intrínseco do Windows PowerShell - um tipo que corresponde aproximadamente ao **dir** e **cd** comandos da Cmd.exe e built-ins no shells de UNIX como BASH.

Na saída do **Get-Command** comando, todas as definições de terminar com nas reticências (…) para indicar que o PowerShell não é possível apresentar todo o conteúdo no espaço disponível. Quando o Windows PowerShell apresenta uma saída, formata o resultado como texto e, em seguida, dispõe para verificar os dados ajustar corretamente a janela. Serão abordadas isto mais tarde na secção ao mesmo tempo.

O **Get-Command** cmdlet tem um **sintaxe** parâmetro que obtém a sintaxe de cada cmdlet. Para obter a sintaxe do cmdlet Get-Help, utilize o seguinte comando:

**Get-Help Get-Command-sintaxe**

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a>Apresentar os tipos de comando disponíveis
O **Get-Command** comando não listar todos os comandos que está disponível no Windows PowerShell. Em vez disso, o **Get-Command** comando lista apenas os cmdlets na sessão atual. O Windows PowerShell, na verdade, suporta vários outros tipos de comandos. Aliases, funções e scripts são também comandos do Windows PowerShell, embora estes não são abordados em detalhe no Guia do utilizador do Windows PowerShell. Ficheiros externos que são executável ou que têm um processador de tipo de ficheiros registada, também estão classificados como comandos.

Para obter todos os comandos na sessão, escreva:

```
Get-Command *
```

Porque esta lista inclui ficheiros externos no seu caminho de pesquisa, pode conter a milhares de itens. É mais útil ver um conjunto de comandos reduzido.

Para obter comandos nativos de outros tipos, utilize o **CommandType** parâmetro o **Get-Command** cmdlet.

> [!NOTE]
> O asterisco (\*) é utilizado para correspondência nos argumentos de comando do Windows PowerShell de caracteres universais. O \* significa "corresponde uma ou mais caracteres". Pode escrever **Get-Command um\&#42;** para localizar todos os comandos que começam com a letra "a". Ao contrário do caráter universal correspondente no Cmd.exe, universal do Windows PowerShell irá também de coincidir com um período.

Para obter os aliases de comando, que são os nicknames atribuídos de comandos, escreva:

```
Get-Command -CommandType Alias
```

Para obter as funções na sessão atual, escreva:

```
Get-Command -CommandType Function
```

Para apresentar scripts no caminho de pesquisa do Windows PowerShell, escreva:

```
Get-Command -CommandType Script
```
