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
# <a name="working-with-files-and-folders"></a><span data-ttu-id="4a9ac-103">Trabalhar com Ficheiros e Pastas</span><span class="sxs-lookup"><span data-stu-id="4a9ac-103">Working with Files and Folders</span></span>

<span data-ttu-id="4a9ac-104">Navegar através de unidades do Windows PowerShell e manipular os itens nos mesmos são semelhante à manipulação de ficheiros e pastas em unidades de disco físicas do Windows.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="4a9ac-105">Esta secção descreve como lidar com determinadas tarefas de manipulação de ficheiros e pastas com o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="4a9ac-106">A listagem de todos os arquivos e pastas numa pasta</span><span class="sxs-lookup"><span data-stu-id="4a9ac-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="4a9ac-107">Pode obter todos os itens diretamente dentro de uma pasta usando **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="4a9ac-108">Adicionar o opcional **força** parâmetro para apresentar ocultada ou itens de sistema.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="4a9ac-109">Por exemplo, este comando apresenta o conteúdo direto do Windows PowerShell unidade C (que é o mesmo que a unidade física de Windows C):</span><span class="sxs-lookup"><span data-stu-id="4a9ac-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="4a9ac-110">O comando lista apenas os itens contidos diretamente, bem similar ao uso do Cmd.exe **DIR** comando ou **ls** numa shell de UNIX.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="4a9ac-111">Para mostrar os itens contidos, tem de especificar o **-Recurse** parâmetro também.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="4a9ac-112">(Pode demorar muito tempo a concluir.) Para listar tudo na unidade C:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="4a9ac-113">**Get-ChildItem** pode filtrar os itens com suas **caminho**, **filtro**, **Include**, e **excluir** são parâmetros, mas também as Normalmente, com base apenas no nome.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="4a9ac-114">Pode efetuar uma filtragem complexa com base nas outras propriedades de itens utilizando **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="4a9ac-115">O seguinte comando localiza todos os executáveis dentro da pasta de arquivos de programas que foram modificado pela última vez depois de 1 de Outubro de 2005 e que são nem menor que 1 megabyte nem superior a 10 megabytes:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="4a9ac-116">Copiar ficheiros e pastas</span><span class="sxs-lookup"><span data-stu-id="4a9ac-116">Copying Files and Folders</span></span>

<span data-ttu-id="4a9ac-117">A copiar é feita com **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="4a9ac-118">O seguinte comando faz o backup c:\\Boot. ini para c:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="4a9ac-119">Se o ficheiro de destino já existir, a tentativa de cópia falhar.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="4a9ac-120">Para substituir um destino já existente, utilize o **força** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="4a9ac-121">Este comando funciona, mesmo quando o destino é só de leitura.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="4a9ac-122">Copiar a pasta funciona da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-122">Folder copying works the same way.</span></span> <span data-ttu-id="4a9ac-123">Este comando copia a pasta c:\\temp\\test1 para a nova pasta c:\\temp\\DeleteMe recursivamente:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="4a9ac-124">Também pode copiar uma seleção de itens.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-124">You can also copy a selection of items.</span></span> <span data-ttu-id="4a9ac-125">O seguinte comando copia todos os arquivos. txt contidos em qualquer lugar em c:\\dados para c:\\temp\\texto:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="4a9ac-126">Ainda pode usar outras ferramentas para efetuar cópias de sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="4a9ac-127">XCOPY, ROBOCOPY e COM objetos, tais como o **FileSystemObject,** funcionam no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="4a9ac-128">Por exemplo, pode utilizar o Windows Script Host **Scripting.FileSystem COM** classe para criar cópias de segurança c:\\Boot. ini para c:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="4a9ac-129">Criar ficheiros e pastas</span><span class="sxs-lookup"><span data-stu-id="4a9ac-129">Creating Files and Folders</span></span>

<span data-ttu-id="4a9ac-130">Criação de novos itens funciona da mesma em todos os fornecedores de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="4a9ac-131">Se um fornecedor de Windows PowerShell tem mais de um tipo de item — por exemplo, o fornecedor do sistema de ficheiros Windows PowerShell distingue entre diretórios e arquivos — tem de especificar o tipo de item.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="4a9ac-132">Este comando cria uma nova pasta c:\\temp\\nova pasta:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="4a9ac-133">Este comando cria um novo ficheiro vazio c:\\temp\\nova pasta\\file.txt</span><span class="sxs-lookup"><span data-stu-id="4a9ac-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="4a9ac-134">Remover todos os ficheiros e pastas numa pasta</span><span class="sxs-lookup"><span data-stu-id="4a9ac-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="4a9ac-135">Pode remover itens contidos usando **Remove-Item**, mas será solicitado a confirmar a remoção, se o item contiver qualquer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="4a9ac-136">Por exemplo, se tentar eliminar a pasta c:\\temp\\DeleteMe que contém outros itens, Windows PowerShell pede-lhe confirmação antes de eliminar a pasta:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="4a9ac-137">Se não pretender que seja pedido para cada item contido, especifique a **Recurse** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="4a9ac-138">Mapeamento de uma pasta Local como uma unidade de acessíveis do Windows</span><span class="sxs-lookup"><span data-stu-id="4a9ac-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>

<span data-ttu-id="4a9ac-139">Também pode mapear uma pasta local, utilizando o **subst** comando.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="4a9ac-140">O comando seguinte cria uma unidade local que p: enraizada no diretório arquivos de programas local:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```powershell
subst p: $env:programfiles
```

<span data-ttu-id="4a9ac-141">Assim como com unidades de rede, as unidades mapeadas dentro do Windows PowerShell usando **subst** são imediatamente visíveis ao shell do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="4a9ac-142">Leitura de um arquivo de texto numa matriz</span><span class="sxs-lookup"><span data-stu-id="4a9ac-142">Reading a Text File into an Array</span></span>

<span data-ttu-id="4a9ac-143">Um dos formatos de armazenamento mais comuns para dados de texto é num arquivo com linhas separadas, tratadas como elementos de dados distintos.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="4a9ac-144">O **Get-Content** cmdlet pode ser utilizado para ler um ficheiro completo num único passo, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

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

<span data-ttu-id="4a9ac-145">**Get-Content** já trata os dados lidos do arquivo como uma matriz, com um elemento por linha de conteúdo do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="4a9ac-146">Pode confirmar isto, verificando a **comprimento** do conteúdo devolvido:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="4a9ac-147">Este comando é mais útil para obter as listas de informações no Windows PowerShell diretamente.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="4a9ac-148">Por exemplo, pode armazenar uma lista de nomes de computadores ou endereços IP num arquivo c:\\temp\\domainMembers.txt, com um nome em cada linha do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="4a9ac-149">Pode usar **Get-Content** para obter o conteúdo do ficheiro e coloque-os na variável **$Computers**:</span><span class="sxs-lookup"><span data-stu-id="4a9ac-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="4a9ac-150">**$Computers** agora é uma matriz contendo um nome de computador em cada elemento.</span><span class="sxs-lookup"><span data-stu-id="4a9ac-150">**$Computers** is now an array containing a computer name in each element.</span></span>
