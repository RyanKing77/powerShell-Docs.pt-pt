---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Ficheiros e Pastas
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 393e886a4945222198d9b81019250c5d5b905ad3
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984396"
---
# <a name="working-with-files-and-folders"></a>Trabalhar com Ficheiros e Pastas

Navegar através de unidades do Windows PowerShell e manipular os itens nos mesmos são semelhante à manipulação de ficheiros e pastas em unidades de disco físicas do Windows. Esta secção descreve como lidar com determinadas tarefas de manipulação de ficheiros e pastas com o PowerShell.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>A listagem de todos os arquivos e pastas numa pasta

Pode obter todos os itens diretamente dentro de uma pasta usando **Get-ChildItem**. Adicionar o opcional **força** parâmetro para apresentar ocultada ou itens de sistema. Por exemplo, este comando apresenta o conteúdo direto do Windows PowerShell unidade C (que é o mesmo que a unidade física de Windows C):

```powershell
Get-ChildItem -Path C:\ -Force
```

O comando lista apenas os itens contidos diretamente, bem similar ao uso do Cmd.exe **DIR** comando ou **ls** numa shell de UNIX. Para mostrar os itens contidos, tem de especificar o **-Recurse** parâmetro também. (Pode demorar muito tempo a concluir.) Para listar tudo na unidade C:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Get-ChildItem** pode filtrar os itens com suas **caminho**, **filtro**, **Include**, e **excluir** são parâmetros, mas também as Normalmente, com base apenas no nome. Pode efetuar uma filtragem complexa com base nas outras propriedades de itens utilizando **Where-Object**.

O seguinte comando localiza todos os executáveis dentro da pasta de arquivos de programas que foram modificado pela última vez depois de 1 de Outubro de 2005 e que são nem menor que 1 megabyte nem superior a 10 megabytes:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Copiar ficheiros e pastas

A copiar é feita com **Copy-Item**. O seguinte comando faz o backup c:\\Boot. ini para c:\\boot.bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Se o ficheiro de destino já existir, a tentativa de cópia falhar. Para substituir um destino já existente, utilize o **força** parâmetro:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Este comando funciona, mesmo quando o destino é só de leitura.

Copiar a pasta funciona da mesma forma. Este comando copia a pasta c:\\temp\\test1 para a nova pasta c:\\temp\\DeleteMe recursivamente:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

Também pode copiar uma seleção de itens. O seguinte comando copia todos os arquivos. txt contidos em qualquer lugar em c:\\dados para c:\\temp\\texto:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Ainda pode usar outras ferramentas para efetuar cópias de sistema de ficheiros. XCOPY, ROBOCOPY e COM objetos, tais como o **FileSystemObject,** funcionam no Windows PowerShell. Por exemplo, pode utilizar o Windows Script Host **Scripting.FileSystem COM** classe para criar cópias de segurança c:\\Boot. ini para c:\\boot.bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Criar ficheiros e pastas

Criação de novos itens funciona da mesma em todos os fornecedores de Windows PowerShell. Se um fornecedor de Windows PowerShell tem mais de um tipo de item — por exemplo, o fornecedor do sistema de ficheiros Windows PowerShell distingue entre diretórios e arquivos — tem de especificar o tipo de item.

Este comando cria uma nova pasta c:\\temp\\nova pasta:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Este comando cria um novo ficheiro vazio c:\\temp\\nova pasta\\file.txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>Remover todos os ficheiros e pastas numa pasta

Pode remover itens contidos usando **Remove-Item**, mas será solicitado a confirmar a remoção, se o item contiver qualquer outra coisa. Por exemplo, se tentar eliminar a pasta c:\\temp\\DeleteMe que contém outros itens, Windows PowerShell pede-lhe confirmação antes de eliminar a pasta:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Se não pretender que seja pedido para cada item contido, especifique a **Recurse** parâmetro:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Mapeamento de uma pasta Local como uma unidade de acessíveis do Windows

Também pode mapear uma pasta local, utilizando o **subst** comando. O comando seguinte cria uma unidade local que p: enraizada no diretório arquivos de programas local:

```powershell
subst p: $env:programfiles
```

Assim como com unidades de rede, as unidades mapeadas dentro do Windows PowerShell usando **subst** são imediatamente visíveis ao shell do Windows PowerShell.

## <a name="reading-a-text-file-into-an-array"></a>Leitura de um arquivo de texto numa matriz

Um dos formatos de armazenamento mais comuns para dados de texto é num arquivo com linhas separadas, tratadas como elementos de dados distintos. O **Get-Content** cmdlet pode ser utilizado para ler um ficheiro completo num único passo, conforme mostrado aqui:

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

**Get-Content** já trata os dados lidos do arquivo como uma matriz, com um elemento por linha de conteúdo do ficheiro. Pode confirmar isto, verificando a **comprimento** do conteúdo devolvido:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Este comando é mais útil para obter as listas de informações no Windows PowerShell diretamente. Por exemplo, pode armazenar uma lista de nomes de computadores ou endereços IP num arquivo c:\\temp\\domainMembers.txt, com um nome em cada linha do ficheiro. Pode usar **Get-Content** para obter o conteúdo do ficheiro e coloque-os na variável **$Computers**:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** agora é uma matriz contendo um nome de computador em cada elemento.
