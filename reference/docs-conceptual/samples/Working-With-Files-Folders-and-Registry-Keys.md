---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Pastas de Ficheiros e Chaves do Registo
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405496"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Trabalhar com arquivos, pastas e chaves de registo

Windows PowerShell utiliza o substantivo **Item** para fazer referência a itens encontrados numa unidade do Windows PowerShell. Ao lidar com o fornecedor do sistema de ficheiros do Windows PowerShell, uma **Item** pode ser um arquivo, uma pasta ou unidade do Windows PowerShell. Listagem e trabalhar com estes itens são uma tarefa de básica crítica na maioria das definições administrativas, para que o que queremos abordar essas tarefas em detalhes.

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>A enumerar os arquivos, pastas e chaves do Registro (Get-ChildItem)

Como obter uma coleção de itens a partir de uma localização específica é uma tarefa comum, o **Get-ChildItem** cmdlet foi desenvolvido especificamente para retornar todos os itens encontrados dentro de um contêiner como uma pasta.

Se quiser retornar todos os ficheiros e pastas que estão contidas diretamente dentro da pasta c:\\Windows, tipo:

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

A listagem assemelha-se de que o que veria ao introduzir o **dir** comando **Cmd.exe**, ou o **ls** comando numa shell de comando de UNIX.

Pode efetuar as listagens muito complexas, utilizando parâmetros do **Get-ChildItem** cmdlet. Vamos ver alguns cenários a seguir. Pode ver a sintaxe da **Get-ChildItem** cmdlet digitando:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Esses parâmetros podem ser misturados e correspondentes para obter uma saída altamente personalizável.

#### <a name="listing-all-contained-items--recurse"></a>Listar todos os itens contidos (-Recurse)

Para ver os itens dentro de uma pasta do Windows e todos os itens que estão contidos dentro as subpastas, utilize o **Recurse** parâmetro do **Get-ChildItem**. A listagem apresenta tudo dentro da pasta do Windows e os itens em suas subpastas. Por exemplo:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a>Filtrar itens por nome (-nome)

Para apresentar apenas os nomes de itens, utilize o **Name** parâmetro do **Get-Childitem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a>A forçar a listagem itens ocultos (-Force)

Itens que são normalmente invisíveis no Explorador de ficheiros ou Cmd.exe não são apresentados no resultado de uma **Get-ChildItem** comando. Para exibir itens ocultos, use o **força** parâmetro do **Get-ChildItem**. Por exemplo:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Este parâmetro com o nome força porque a forçar pode substituir o comportamento normal da **Get-ChildItem** comando. Force é um parâmetro amplamente usado que força uma ação que um cmdlet não seria normalmente executam, apesar de não executará nenhuma ação que compromete a segurança do sistema.

#### <a name="matching-item-names-with-wildcards"></a>Correspondência de nomes de Item com carateres universais

**O Get-ChildItem** comando aceita carateres universais no caminho dos itens de lista.

Porque a correspondência de carateres universais é processada pelo mecanismo do Windows PowerShell, todos os cmdlets que aceita carateres universais utilizar a mesma notação e têm o mesmo comportamento correspondente. A notação de caráter universal do Windows PowerShell inclui:

- Asterisco (\*) corresponde a zero ou mais ocorrências de qualquer caractere.

- Ponto de interrogação (?) corresponde a exatamente um caractere.

- Parênteses Reto de abertura (\[) caráter e o caráter de Reto (]) envolvem um conjunto de caracteres para corresponder.

Aqui estão alguns exemplos de como funciona a especificação de caráter universal.

Para localizar todos os ficheiros no diretório do Windows com o sufixo **. log** e exatamente cinco caracteres no nome de base, introduza o seguinte comando:

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

Para localizar todos os ficheiros que começam com a letra **x** no diretório do Windows, escreva:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Para localizar todos os arquivos cujos nomes comecem com **x** ou **z**, tipo:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a>Excluir itens (-excluir)

Pode excluir itens específicos, utilizando o **excluir** parâmetro de Get-ChildItem. Isto permite-lhe efetuar complexos de filtragem numa única instrução.

Por exemplo, suponha que está tentando encontrar a DLL de serviço de hora do Windows na pasta System32, e tudo o que pode se lembrar sobre o nome da DLL é que começa com "W" e tem "32" nela.

Uma expressão, como **w\&#42; 32\&#42;. dll** irá encontrar todas as DLLs que cumprem as condições, mas ele pode retornar também o Windows 95 e compatibilidade do Windows de 16 bits DLLs que incluem "95" ou "16" nos respetivos nomes. Pode omitir ficheiros com qualquer um desses números nos respetivos nomes utilizando o **excluir** parâmetro com o padrão  **\&#42;\[ 9516]\&#42;**:

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

#### <a name="mixing-get-childitem-parameters"></a>Misturar os parâmetros de Get-ChildItem

Pode utilizar vários dos parâmetros do **Get-ChildItem** cmdlet no mesmo comando. Antes de misturar parâmetros, certifique-se de que compreende a correspondência de carateres universais. Por exemplo, o comando seguinte devolve não existem resultados:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Não há nenhum resultado, muito embora haja duas DLLs que começam com a letra "z", na pasta Windows.

Não foram devolvidos resultados porque foi especificado o caráter universal como parte do caminho. Embora o comando foi recursiva, o **Get-ChildItem** cmdlet restrito os itens para os que estão na pasta do Windows com nomes que termina com ". dll".

Para especificar uma pesquisa recursiva para arquivos cujos nomes correspondem a um padrão especial, utilize o **-incluem** parâmetro.

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