---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Trabalhar com Ficheiros e Pastas
ms.openlocfilehash: 743e261d2f5e8bfa39f2731fca7fea6e5678c711
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215529"
---
# <a name="working-with-files-and-folders"></a>Trabalhar com Ficheiros e Pastas

Navegar pelas unidades do Windows PowerShell e manipular os itens nelas é semelhante à manipulação de arquivos e pastas em unidades de disco físico do Windows. Esta seção discute como lidar com tarefas específicas de manipulação de arquivos e pastas usando o PowerShell.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>Listando todos os arquivos e pastas dentro de uma pasta

Você pode obter todos os itens diretamente em uma pasta usando **Get-ChildItem**. Adicione o parâmetro **Force** opcional para exibir itens ocultos ou do sistema. Por exemplo, esse comando exibe o conteúdo direto da unidade C do Windows PowerShell (que é o mesmo que a unidade física do Windows C):

```powershell
Get-ChildItem -Path C:\ -Force
```

O comando lista apenas os itens contidos diretamente, de forma semelhante ao uso do comando **dir** do cmd. exe ou **ls** em um shell do UNIX. Para mostrar os itens contidos, você precisa especificar o parâmetro **-recurse** também. (Isso pode levar muito tempo para ser concluído.) Para listar tudo na unidade C:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Get-ChildItem** pode filtrar itens com seu **caminho**, **Filtrar**, **incluir**e **excluir** parâmetros, mas eles geralmente são baseados apenas no nome. Você pode executar uma filtragem complexa com base em outras propriedades de itens usando **Where-Object**.

O comando a seguir localiza todos os executáveis na pasta arquivos de programas que foram modificados pela última vez após 1º de outubro de 2005 e que não são menores que 1 megabyte nem maiores que 10 megabytes:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Copiando arquivos e pastas

A cópia é feita com **Copy-Item**. O comando a seguir faz backup de\\c: boot. ini em\\c: boot. bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Se o arquivo de destino já existir, a tentativa de cópia falhará. Para substituir um destino pré-existente, use o parâmetro **Force** :

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Esse comando funciona mesmo quando o destino é somente leitura.

A cópia de pastas funciona da mesma maneira. Este comando copia a pasta c:\\temp\\Test1 para a nova pasta c:\\temp\\DeleteMe recursivamente:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

Você também pode copiar uma seleção de itens. O comando a seguir copia todos os arquivos. txt contidos em qualquer\\lugar em c:\\data\\para c: Temp Text:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Você ainda pode usar outras ferramentas para executar cópias do sistema de arquivos. Os objetos XCOPY, ROBOCOPY e COM, como o **script. FileSystemObject,** funcionam no Windows PowerShell. Por exemplo, você pode usar a classe com script do Windows Script Host **. FileSystem** para fazer backup de c\\: boot. ini em c\\: boot. bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Criando arquivos e pastas

A criação de novos itens funciona da mesma em todos os provedores do Windows PowerShell. Se um provedor do Windows PowerShell tiver mais de um tipo de item — por exemplo, o provedor do sistema de arquivos do Windows PowerShell se distingue entre diretórios e arquivos — você precisa especificar o tipo de item.

Este comando cria uma nova pasta C:\\temp\\nova pasta:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Este comando cria um novo arquivo vazio C:\\temp\\nova pasta\\File. txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>Removendo todos os arquivos e pastas dentro de uma pasta

Você pode remover os itens contidos usando **Remove-Item**, mas será solicitado que você confirme a remoção se o item contiver qualquer outra coisa. Por exemplo, se você tentar excluir a pasta C:\\temp\\DeleteMe que contém outros itens, o Windows PowerShell solicitará sua confirmação antes de excluir a pasta:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Se você não quiser ser solicitado para cada item contido, especifique o parâmetro Recurse :

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a>Mapeando uma pasta local como uma unidade

Você também pode mapear uma pasta local usando o comando **New-PSDrive** . O comando a seguir cria uma unidade local P: com raiz no diretório arquivos de programas locais, visível somente na sessão do PowerShell:

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

Assim como ocorre com unidades de rede, as unidades mapeadas no Windows PowerShell são imediatamente visíveis para o Shell do Windows PowerShell.
Para criar uma unidade mapeada visível no explorador de arquivos, o parâmetro **-Persist** é necessário. No entanto, somente caminhos remotos podem ser usados com Persist.


## <a name="reading-a-text-file-into-an-array"></a>Lendo um arquivo de texto em uma matriz

Um dos formatos de armazenamento mais comuns para dados de texto está em um arquivo com linhas separadas tratadas como elementos de dados distintos. O cmdlet **Get-Content** pode ser usado para ler um arquivo inteiro em uma única etapa, como mostrado aqui:

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

**Get-Content** já trata os dados lidos do arquivo como uma matriz, com um elemento por linha de conteúdo do arquivo. Você pode confirmar isso verificando o **comprimento** do conteúdo retornado:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Esse comando é mais útil para obter listas de informações diretamente no Windows PowerShell. Por exemplo, você pode armazenar uma lista de nomes de computador ou endereços IP em um arquivo C\\:\\Temp domainMembers. txt, com um nome em cada linha do arquivo. Você pode usar o **Get-Content** para recuperar o conteúdo do arquivo e colocá-lo na variável **$Computers**:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** agora é uma matriz que contém um nome de computador em cada elemento.
