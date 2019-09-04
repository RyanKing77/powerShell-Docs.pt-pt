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
# <a name="working-with-files-and-folders"></a><span data-ttu-id="161ea-103">Trabalhar com Ficheiros e Pastas</span><span class="sxs-lookup"><span data-stu-id="161ea-103">Working with Files and Folders</span></span>

<span data-ttu-id="161ea-104">Navegar pelas unidades do Windows PowerShell e manipular os itens nelas é semelhante à manipulação de arquivos e pastas em unidades de disco físico do Windows.</span><span class="sxs-lookup"><span data-stu-id="161ea-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="161ea-105">Esta seção discute como lidar com tarefas específicas de manipulação de arquivos e pastas usando o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="161ea-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="161ea-106">Listando todos os arquivos e pastas dentro de uma pasta</span><span class="sxs-lookup"><span data-stu-id="161ea-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="161ea-107">Você pode obter todos os itens diretamente em uma pasta usando **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="161ea-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="161ea-108">Adicione o parâmetro **Force** opcional para exibir itens ocultos ou do sistema.</span><span class="sxs-lookup"><span data-stu-id="161ea-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="161ea-109">Por exemplo, esse comando exibe o conteúdo direto da unidade C do Windows PowerShell (que é o mesmo que a unidade física do Windows C):</span><span class="sxs-lookup"><span data-stu-id="161ea-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="161ea-110">O comando lista apenas os itens contidos diretamente, de forma semelhante ao uso do comando **dir** do cmd. exe ou **ls** em um shell do UNIX.</span><span class="sxs-lookup"><span data-stu-id="161ea-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="161ea-111">Para mostrar os itens contidos, você precisa especificar o parâmetro **-recurse** também.</span><span class="sxs-lookup"><span data-stu-id="161ea-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="161ea-112">(Isso pode levar muito tempo para ser concluído.) Para listar tudo na unidade C:</span><span class="sxs-lookup"><span data-stu-id="161ea-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="161ea-113">**Get-ChildItem** pode filtrar itens com seu **caminho**, **Filtrar**, **incluir**e **excluir** parâmetros, mas eles geralmente são baseados apenas no nome.</span><span class="sxs-lookup"><span data-stu-id="161ea-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="161ea-114">Você pode executar uma filtragem complexa com base em outras propriedades de itens usando **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="161ea-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="161ea-115">O comando a seguir localiza todos os executáveis na pasta arquivos de programas que foram modificados pela última vez após 1º de outubro de 2005 e que não são menores que 1 megabyte nem maiores que 10 megabytes:</span><span class="sxs-lookup"><span data-stu-id="161ea-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="161ea-116">Copiando arquivos e pastas</span><span class="sxs-lookup"><span data-stu-id="161ea-116">Copying Files and Folders</span></span>

<span data-ttu-id="161ea-117">A cópia é feita com **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="161ea-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="161ea-118">O comando a seguir faz backup de\\c: boot. ini em\\c: boot. bak:</span><span class="sxs-lookup"><span data-stu-id="161ea-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="161ea-119">Se o arquivo de destino já existir, a tentativa de cópia falhará.</span><span class="sxs-lookup"><span data-stu-id="161ea-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="161ea-120">Para substituir um destino pré-existente, use o parâmetro **Force** :</span><span class="sxs-lookup"><span data-stu-id="161ea-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="161ea-121">Esse comando funciona mesmo quando o destino é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="161ea-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="161ea-122">A cópia de pastas funciona da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="161ea-122">Folder copying works the same way.</span></span> <span data-ttu-id="161ea-123">Este comando copia a pasta c:\\temp\\Test1 para a nova pasta c:\\temp\\DeleteMe recursivamente:</span><span class="sxs-lookup"><span data-stu-id="161ea-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="161ea-124">Você também pode copiar uma seleção de itens.</span><span class="sxs-lookup"><span data-stu-id="161ea-124">You can also copy a selection of items.</span></span> <span data-ttu-id="161ea-125">O comando a seguir copia todos os arquivos. txt contidos em qualquer\\lugar em c:\\data\\para c: Temp Text:</span><span class="sxs-lookup"><span data-stu-id="161ea-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="161ea-126">Você ainda pode usar outras ferramentas para executar cópias do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="161ea-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="161ea-127">Os objetos XCOPY, ROBOCOPY e COM, como o **script. FileSystemObject,** funcionam no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="161ea-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="161ea-128">Por exemplo, você pode usar a classe com script do Windows Script Host **. FileSystem** para fazer backup de c\\: boot. ini em c\\: boot. bak:</span><span class="sxs-lookup"><span data-stu-id="161ea-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="161ea-129">Criando arquivos e pastas</span><span class="sxs-lookup"><span data-stu-id="161ea-129">Creating Files and Folders</span></span>

<span data-ttu-id="161ea-130">A criação de novos itens funciona da mesma em todos os provedores do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="161ea-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="161ea-131">Se um provedor do Windows PowerShell tiver mais de um tipo de item — por exemplo, o provedor do sistema de arquivos do Windows PowerShell se distingue entre diretórios e arquivos — você precisa especificar o tipo de item.</span><span class="sxs-lookup"><span data-stu-id="161ea-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="161ea-132">Este comando cria uma nova pasta C:\\temp\\nova pasta:</span><span class="sxs-lookup"><span data-stu-id="161ea-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="161ea-133">Este comando cria um novo arquivo vazio C:\\temp\\nova pasta\\File. txt</span><span class="sxs-lookup"><span data-stu-id="161ea-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="161ea-134">Removendo todos os arquivos e pastas dentro de uma pasta</span><span class="sxs-lookup"><span data-stu-id="161ea-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="161ea-135">Você pode remover os itens contidos usando **Remove-Item**, mas será solicitado que você confirme a remoção se o item contiver qualquer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="161ea-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="161ea-136">Por exemplo, se você tentar excluir a pasta C:\\temp\\DeleteMe que contém outros itens, o Windows PowerShell solicitará sua confirmação antes de excluir a pasta:</span><span class="sxs-lookup"><span data-stu-id="161ea-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="161ea-137">Se você não quiser ser solicitado para cada item contido, especifique o parâmetro Recurse :</span><span class="sxs-lookup"><span data-stu-id="161ea-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a><span data-ttu-id="161ea-138">Mapeando uma pasta local como uma unidade</span><span class="sxs-lookup"><span data-stu-id="161ea-138">Mapping a Local Folder as a drive</span></span>

<span data-ttu-id="161ea-139">Você também pode mapear uma pasta local usando o comando **New-PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="161ea-139">You can also map a local folder, using the **New-PSDrive** command.</span></span> <span data-ttu-id="161ea-140">O comando a seguir cria uma unidade local P: com raiz no diretório arquivos de programas locais, visível somente na sessão do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="161ea-140">The following command creates a local drive P: rooted in the local Program Files directory, visible only from the PowerShell session:</span></span>

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

<span data-ttu-id="161ea-141">Assim como ocorre com unidades de rede, as unidades mapeadas no Windows PowerShell são imediatamente visíveis para o Shell do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="161ea-141">Just as with network drives, drives mapped within Windows PowerShell are immediately visible to the Windows PowerShell shell.</span></span>
<span data-ttu-id="161ea-142">Para criar uma unidade mapeada visível no explorador de arquivos, o parâmetro **-Persist** é necessário.</span><span class="sxs-lookup"><span data-stu-id="161ea-142">In order to create a mapped drive visible from File Explorer, the parameter **-Persist** is needed.</span></span> <span data-ttu-id="161ea-143">No entanto, somente caminhos remotos podem ser usados com Persist.</span><span class="sxs-lookup"><span data-stu-id="161ea-143">However, only remote paths can be used with Persist.</span></span>


## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="161ea-144">Lendo um arquivo de texto em uma matriz</span><span class="sxs-lookup"><span data-stu-id="161ea-144">Reading a Text File into an Array</span></span>

<span data-ttu-id="161ea-145">Um dos formatos de armazenamento mais comuns para dados de texto está em um arquivo com linhas separadas tratadas como elementos de dados distintos.</span><span class="sxs-lookup"><span data-stu-id="161ea-145">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="161ea-146">O cmdlet **Get-Content** pode ser usado para ler um arquivo inteiro em uma única etapa, como mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="161ea-146">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

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

<span data-ttu-id="161ea-147">**Get-Content** já trata os dados lidos do arquivo como uma matriz, com um elemento por linha de conteúdo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="161ea-147">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="161ea-148">Você pode confirmar isso verificando o **comprimento** do conteúdo retornado:</span><span class="sxs-lookup"><span data-stu-id="161ea-148">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="161ea-149">Esse comando é mais útil para obter listas de informações diretamente no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="161ea-149">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="161ea-150">Por exemplo, você pode armazenar uma lista de nomes de computador ou endereços IP em um arquivo C\\:\\Temp domainMembers. txt, com um nome em cada linha do arquivo.</span><span class="sxs-lookup"><span data-stu-id="161ea-150">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="161ea-151">Você pode usar o **Get-Content** para recuperar o conteúdo do arquivo e colocá-lo na variável **$Computers**:</span><span class="sxs-lookup"><span data-stu-id="161ea-151">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="161ea-152">**$Computers** agora é uma matriz que contém um nome de computador em cada elemento.</span><span class="sxs-lookup"><span data-stu-id="161ea-152">**$Computers** is now an array containing a computer name in each element.</span></span>
