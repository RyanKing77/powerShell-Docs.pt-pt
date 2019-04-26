---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Ordenar Objetos
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086056"
---
# <a name="sorting-objects"></a>Ordenar Objetos

Podemos pode organizar os dados exibidos para que seja mais fácil verificar utilizando o `Sort-Object` cmdlet. `Sort-Object` obtém o nome de uma ou mais propriedades a classificação e retorna dados ordenados por valores dessas propriedades.

## <a name="basic-sorting"></a>A classificação básica

Considere o problema de listagem subdiretórios e arquivos no diretório atual.
Se queremos ordenar por **LastWriteTime** e, em seguida, por **nome**, podemos fazer isso digitando:

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

Também pode ordenar os objetos na ordem inversa, especificando o **descendente** mudar o parâmetro.

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a>Utilizar tabelas de hash

Pode ordenar diferentes propriedades em ordens diferentes ao utilizar tabelas de hash numa matriz.
Cada tabela de hash utiliza um **expressão** chave para especificar o nome da propriedade como cadeia de caracteres e uma **Ascending** ou **descendente** chave para especificar a ordem de classificação por `$true` ou `$false`.
O **expressão** chave é obrigatória.
O **ascendente** ou **descendente** chave é opcional.

O exemplo seguinte classifica os objetos por descendente **LastWriteTime** ordem e ascendente **nome** ordem.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

Também pode definir um scriptblock o **expressão** chave.
Ao executar o `Sort-Object` cmdlet, que é executado o scriptblock e o resultado é utilizado para ordenação.

O exemplo seguinte classifica os objetos em ordem decrescente pelo período de tempo entre **CreationTime** e **LastWriteTime**.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a>Sugestões

Pode omitir os **propriedade** nome do parâmetro seguinte:

```powershell
Sort-Object LastWriteTime, Name
```

Além disso, pode consultar `Sort-Object` pelo seu alias incorporada, `sort`:

```powershell
sort LastWriteTime, Name
```

As chaves das tabelas de hash para ordenação podem ser abreviadas como o seguinte:

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

Neste exemplo, o **i** significa **expressão**, o **1!d** significa **descendente**e o **um** quer dizer **Ascending**.

Para melhorar a legibilidade, pode colocar as tabelas de hash numa variável separada:

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```