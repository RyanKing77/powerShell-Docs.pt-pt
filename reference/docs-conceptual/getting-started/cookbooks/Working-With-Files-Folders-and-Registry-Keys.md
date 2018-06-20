---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Pastas de Ficheiros e Chaves do Registo
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952312"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Trabalhar com ficheiros, pastas e chaves de registo

O Windows PowerShell utiliza o substantivo **Item** para fazer referência aos itens encontrados numa unidade do Windows PowerShell. Ao lidar com o fornecedor de sistema de ficheiros do Windows PowerShell, uma **Item** poderá ser uma pasta, um ficheiro ou a unidade do Windows PowerShell. Listar e trabalhar com estes itens são uma tarefa de básica crítico na maioria das definições administrativas, pelo que queremos abordam estas tarefas em detalhe.

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>A enumerar os ficheiros, pastas e chaves de registo (Get-ChildItem)

Uma vez que obter uma colecção de itens a partir de uma localização específica essas tarefas comuns, a **Get-ChildItem** cmdlet foi concebido especificamente para devolver todos os itens localizados num contentor, tais como uma pasta.

Se pretender devolver todos os ficheiros e pastas que estão incluídas diretamente na pasta c:\\Windows, tipo:

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

A listagem semelhante que verá ao introduzir o **dir** no **Cmd.exe**, ou o **ls** comando numa shell de comandos UNIX.

Pode efetuar listagens muito complexas utilizando os parâmetros do **Get-ChildItem** cmdlet. Iremos abordar o alguns cenários seguinte. Pode ver a sintaxe de **Get-ChildItem** cmdlet escrevendo:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Estes parâmetros podem ser misto e correspondência para obter Resultado altamente personalizado.

#### <a name="listing-all-contained-items--recurse"></a>Listar todos os itens contidos (-Recurse)

Para ver os itens dentro de uma pasta do Windows e quaisquer itens que estão incluídos as subpastas, utilize o **Recurse** parâmetro **Get-ChildItem**. A lista apresenta tudo dentro da pasta do Windows e os itens nas respetivas subpastas. Por exemplo:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a>Filtrar itens por nome (-Name)

Para apresentar apenas os nomes de itens, utilize o **nome** parâmetro **Get-Childitem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a>A forçar a listar itens ocultos (-forçar)

Os itens que são normalmente invisíveis no Explorador de ficheiros ou Cmd.exe não são apresentados no resultado de uma **Get-ChildItem** comando. Para apresentar os itens ocultos, utilize o **Force** parâmetro **Get-ChildItem**. Por exemplo:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Este parâmetro é denominado Force porque pode forçar a substituir o comportamento normal a **Get-ChildItem** comando. Force é um parâmetro amplamente utilizado que força uma ação que um cmdlet não seria normalmente efetuar, apesar de não efetuará nenhuma ação que compromises a segurança do sistema.

#### <a name="matching-item-names-with-wildcards"></a>Nomes de itens correspondentes com carateres universais

**Get-ChildItem** comando aceita carateres universais no caminho dos itens de lista.

Porque a correspondência de carateres universais é processado pelo motor do Windows PowerShell, todos os cmdlets que aceita carateres universais utilizam a notação mesma e ter o mesmo comportamento correspondente. A notação de caráter universal do Windows PowerShell inclui:

- Asterisco (\*) corresponde a zero ou mais ocorrências de qualquer caráter.

- Ponto de interrogação (?) corresponde exatamente um caráter.

- Reto esquerdo (\[) carateres e o caráter de parêntesis Reto direito (]) coloque um conjunto de carateres a ser correspondido.

Seguem-se alguns exemplos de como funciona a especificação de caráter universal.

Localizar todos os ficheiros no diretório do Windows com o sufixo **. log** e exatamente cinco carateres no nome de base, introduza o seguinte comando:

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

Localizar todos os ficheiros que começam com a letra **x** no diretório do Windows, escreva:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Localizar todos os ficheiros cujos nomes começam por **x** ou **z**, tipo:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a>Excluir itens (-excluir)

Pode excluir itens específicos utilizando o **excluir** parâmetro de Get-ChildItem. Isto permite-lhe efetuar complexas filtragem numa instrução única.

Por exemplo, suponha está a tentar localizar a DLL de serviço de hora do Windows na pasta System32, não sendo todas pode Lembre-se sobre o nome DLL que comece com "M" e tem "32" no mesmo.

Como uma expressão **w\&#42; 32\&#42;. dll** irá encontrar todas as DLLs que cumprem as condições, mas pode devolver também o Windows 95 e compatibilidade de Windows de 16 bits DLLs que incluem "95" ou "16" nos respetivos nomes. Pode omitir ficheiros com qualquer um destes números nos respetivos nomes utilizando o **excluir** parâmetro com o padrão  **\&#42;\[ 9516]\&#42;**:

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

#### <a name="mixing-get-childitem-parameters"></a>A combinação de parâmetros de Get-ChildItem

Pode utilizar vários dos parâmetros do **Get-ChildItem** cmdlet no mesmo comando. Antes de combinar parâmetros, lembre-se de que compreende a correspondência de carateres universais. Por exemplo, o comando seguinte devolve não existem resultados:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Não existirem resultados, apesar de existirem duas DLLs que começam com a letra "z" na pasta do Windows.

Não foram devolver resultados porque foi especificado o caráter universal como parte do caminho. Apesar do comando foi recursiva, o **Get-ChildItem** cmdlet restrito os itens que estão na pasta do Windows com nomes que termina com ". dll".

Para especificar uma pesquisa recursiva para ficheiros cujos nomes correspondem um padrão especial, utilize o **-incluem** parâmetro.

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```