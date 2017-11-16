---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Trabalhar com ficheiros e pastas
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 73773df9f018c396c9c4237a40f2e9d2c841464e
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-files-and-folders"></a>Trabalhar com ficheiros e pastas
Navegar através de unidades do Windows PowerShell e manipular os itens nos mesmos são semelhante a manipulação de ficheiros e pastas em unidades de disco físicas do Windows. Como lidar com tarefas específicas de manipulação de ficheiros e pastas nesta secção, vamos abordar.

### <a name="listing-all-the-files-and-folders-within-a-folder"></a>Listar todos os ficheiros e pastas numa pasta
Pode obter todos os itens diretamente numa pasta utilizando **Get-ChildItem**. Adicionar o opcional **Force** parâmetro para apresentar ocultada ou itens de sistema. Por exemplo, este comando apresenta o conteúdo diretamente do Windows PowerShell unidade C (que é o mesmo que a unidade física de Windows C):

```
Get-ChildItem -Force C:\
```

O comando lista apenas os itens contidos diretamente, semelhante a utilização do Cmd.exe **DIR** comando ou **ls** na shell de UNIX. Para mostrar os itens que contêm, tem de especificar o **-Recurse** , bem como parâmetro. (Isto pode demorar um extremamente muito tempo a concluir.) Para listar tudo na unidade C:

```
Get-ChildItem -Force C:\ -Recurse
```

**Get-ChildItem** pode filtrar itens com o respetivo **caminho**, **filtro**, **incluir**, e **excluir** parâmetros, mas os Normalmente, baseiam-se apenas no nome. Pode efetuar a filtragem complexas com base nas outras propriedades de itens utilizando **Where-Object**.

O comando seguinte localiza todas as executáveis dentro da pasta de ficheiros de programa que foram modificado pela última vez depois de 1 de Outubro de 2005 e que são maiores do que 10 megabytes nem inferior a 1 megabyte:

```
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt "2005-10-01") -and ($_.Length -ge 1m) -and ($_.Length -le 10m)}
```

### <a name="copying-files-and-folders"></a>Copiar ficheiros e pastas
A copiar é feito com **Copy-Item**. O comando seguinte cria cópias de segurança c:\\boot.ini para c:\\boot.bak:

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak
```

Se o ficheiro de destino já existir, a tentativa de copiar falha. Para substituir um destino já existente, utilize o parâmetro Force:

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak -Force
```

Este comando funciona mesmo quando o destino é só de leitura.

Copiar a pasta funciona da mesma forma. Este comando copia a pasta c:\\temp\\test1 a unidade c para nova pasta:\\temp\\DeleteMe recursivamente:

```
Copy-Item C:\temp\test1 -Recurse c:\temp\DeleteMe
```

Também pode copiar uma seleção de itens. O comando seguinte copia todos os ficheiros. txt contidos em qualquer local c:\\dados para c:\\temp\\texto:

```
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination c:\temp\text
```

Pode continuar a utilizar outras ferramentas para efetuar cópias de sistema de ficheiros. XCOPY, ROBOCOPY e COM os objetos, tais como o **Scripting.FileSystemObject,** tudo funcionar no Windows PowerShell. Por exemplo, pode utilizar o Windows Script Host **Scripting.FileSystem COM** classe fazer cópias de segurança c:\\boot.ini para c:\\boot.bak:

```
(New-Object -ComObject Scripting.FileSystemObject).CopyFile("c:\boot.ini", "c:\boot.bak")
```

### <a name="creating-files-and-folders"></a>Criar ficheiros e pastas
Criar novos itens funciona da mesma em todos os fornecedores do Windows PowerShell. Se um fornecedor de Windows PowerShell tem mais do que um tipo de item de — por exemplo, o fornecedor do PowerShell do sistema de ficheiros Windows distingue entre diretórios e ficheiros — tem de especificar o tipo de item.

Este comando cria uma nova pasta c:\\temp\\nova pasta:

```
New-Item -Path 'C:\temp\New Folder' -ItemType "directory"
```

Este comando cria um novo ficheiro vazio c:\\temp\\nova pasta\\file.txt

```
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType "file"
```

### <a name="removing-all-files-and-folders-within-a-folder"></a>Remover todos os ficheiros e pastas numa pasta
Pode remover os itens que contêm utilizando **Remove-Item**, mas será solicitado para confirmar a remoção, se o item contém tudo o resto. Por exemplo, se tentar eliminar a pasta c:\\temp\\DeleteMe que contém outros itens, do Windows PowerShell pede-lhe confirmação antes de eliminar a pasta:

```
Remove-Item C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Se não pretender que lhe seja pedida a cada item contida, especifique o **Recurse** parâmetro:

```
Remove-Item C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Mapeamento de uma pasta Local como uma unidade de acessível do Windows
Também pode mapear uma pasta local, utilizando o **subst** comando. O comando seguinte cria uma unidade local que p: Root no diretório de ficheiros de programa local:

```
subst p: $env:programfiles
```

Tal como com unidades de rede, unidades mapeadas dentro do Windows PowerShell utilizando **subst** imediatamente visíveis para a shell do Windows PowerShell.

### <a name="reading-a-text-file-into-an-array"></a>Ler um ficheiro de texto para uma matriz
Um dos formatos de armazenamento mais comuns para dados de texto é num ficheiro com linhas separadas tratadas como elementos de dados distintos. O **Get-Content** cmdlet pode ser utilizado para ler de todo um ficheiro num único passo, conforme mostrado aqui:

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

**Get-Content** já trata os dados lidos a partir do ficheiro como uma matriz, com um elemento por linha conteúdo de um ficheiro. Pode confirmar isto, verificando o **comprimento** do conteúdo devolvido:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Este comando é mais útil para obter listas de informações com o Windows PowerShell diretamente. Por exemplo, pode armazenar uma lista de nomes de computador ou endereços IP num ficheiro c:\\temp\\domainMembers.txt, com um nome de cada linha do ficheiro. Pode utilizar **Get-Content** para obter os conteúdos do ficheiro e colocá-los na variável **$Computers**:

```
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** agora é uma matriz que contém um nome de computador em que cada elemento.
