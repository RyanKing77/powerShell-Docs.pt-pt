---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Manipular Itens Diretamente
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 4caa7d2e0eecff9783556062d8503fe10e616fe5
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293270"
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="b8a0d-103">Manipular Itens Diretamente</span><span class="sxs-lookup"><span data-stu-id="b8a0d-103">Manipulating Items Directly</span></span>

<span data-ttu-id="b8a0d-104">Os elementos que vê em unidades do Windows PowerShell, por exemplo, os ficheiros e pastas em unidades de sistema de ficheiros e as chaves de registo em unidades de registo do Windows PowerShell, são chamados *itens* no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="b8a0d-105">Os cmdlets para trabalhar com eles item têm o substantivo **Item** nos respetivos nomes.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="b8a0d-106">A saída do **Get-Command - Item substantivo** comando mostra que há nove cmdlets de item do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

## <a name="creating-new-items-new-item"></a><span data-ttu-id="b8a0d-107">Criação de novos itens (Novo Item)</span><span class="sxs-lookup"><span data-stu-id="b8a0d-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="b8a0d-108">Para criar um novo item no sistema de ficheiros, utilize o **New Item** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="b8a0d-109">Incluir o **caminho** parâmetro com o caminho para o item e o **ItemType** parâmetro com um valor de "arquivo" ou "diretório".</span><span class="sxs-lookup"><span data-stu-id="b8a0d-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="b8a0d-110">Por exemplo, para criar um novo diretório com o nome "New.Directory"in a unidade c:\\diretório Temp, escreva:</span><span class="sxs-lookup"><span data-stu-id="b8a0d-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="b8a0d-111">Para criar um ficheiro, altere o valor do **ItemType** parâmetro para "arquivo".</span><span class="sxs-lookup"><span data-stu-id="b8a0d-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="b8a0d-112">Por exemplo, para criar um arquivo chamado "file1.txt" no diretório New.Directory, escreva:</span><span class="sxs-lookup"><span data-stu-id="b8a0d-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="b8a0d-113">Pode utilizar a mesma técnica para criar uma nova chave de registo.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="b8a0d-114">Na verdade, uma chave de registo é mais fácil criar porque o único tipo de item no registo do Windows é uma chave.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="b8a0d-115">(As entradas do Registro são item *propriedades*.) Por exemplo, para criar uma chave denominada Testar"na subchave CurrentVersion, escreva:</span><span class="sxs-lookup"><span data-stu-id="b8a0d-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="b8a0d-116">Ao digitar um caminho de registo, certifique-se de que inclui os dois pontos (**:**) no Windows PowerShell unidade nomes, HKLM: e HKCU:.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="b8a0d-117">Sem os dois pontos, o Windows PowerShell não reconhece o nome da unidade no caminho.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

## <a name="why-registry-values-are-not-items"></a><span data-ttu-id="b8a0d-118">Por que os valores de registo não são itens</span><span class="sxs-lookup"><span data-stu-id="b8a0d-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="b8a0d-119">Quando utiliza a **Get-ChildItem** cmdlet para localizar os itens numa chave de registo nunca verá as entradas do Registro atual ou os respetivos valores.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="b8a0d-120">Por exemplo, a chave de registo **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\executar** geralmente contém várias entradas de registo que representam aplicações que são executadas quando o sistema é iniciado.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="b8a0d-121">No entanto, quando utiliza **Get-ChildItem** para procurar itens subordinados na chave, tudo o que verá é o **OptionalComponents** subchave da chave:</span><span class="sxs-lookup"><span data-stu-id="b8a0d-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="b8a0d-122">Embora seria conveniente tratar as entradas do Registro como itens, não é possível especificar um caminho para uma entrada de registo de uma forma que garante que é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="b8a0d-123">A notação de caminho não faz distinção entre a subchave de registo com o nome **execute** e o **(predefinida)** entrada de registo no **executar** subchave.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="b8a0d-124">Além disso, uma vez que os nomes de entrada de registo podem conter o caráter de barra invertida (**\\**), se as entradas do Registro foram itens, em seguida, não podia usar a notação de caminho para uma entrada de registo com o nome de distinguir  **Windows\\CurrentVersion\\executar** da subchave que está localizada em que o caminho.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if registry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

## <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="b8a0d-125">Mudar o nome de itens existentes (Rename-Item)</span><span class="sxs-lookup"><span data-stu-id="b8a0d-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="b8a0d-126">Para alterar o nome de um ficheiro ou pasta, utilize o **Rename-Item** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="b8a0d-127">O comando seguinte altera o nome da **file1.txt** do ficheiro para **fileOne.txt**.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="b8a0d-128">O **Rename-Item** cmdlet pode alterar o nome de um arquivo ou uma pasta, mas ele não é possível mover um item.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="b8a0d-129">O seguinte comando falha porque ele tenta mover o ficheiro a partir do diretório New.Directory para o diretório Temp.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a><span data-ttu-id="b8a0d-130">Mover itens (Move-Item)</span><span class="sxs-lookup"><span data-stu-id="b8a0d-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="b8a0d-131">Para mover um ficheiro ou pasta, utilize o **Move-Item** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="b8a0d-132">Por exemplo, o seguinte comando move o diretório de New.Directory da unidade c:\\diretório temporário para a raiz da unidade c:.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="b8a0d-133">Para verificar que o item foi movido, inclua o **PassThru** parâmetro do **Move-Item** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="b8a0d-134">Sem **Passthru**, o **Move-Item** cmdlet não apresenta quaisquer resultados.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a><span data-ttu-id="b8a0d-135">Copiar itens (Copy-Item)</span><span class="sxs-lookup"><span data-stu-id="b8a0d-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="b8a0d-136">Se estiver familiarizado com as operações de cópia de outros shells, talvez o comportamento do **Copy-Item** cmdlet no Windows PowerShell para ser invulgar.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="b8a0d-137">Quando copiar um item de uma localização para outra, Copy-Item não copia o conteúdo por predefinição.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="b8a0d-138">Por exemplo, se copiar os **New.Directory** diretório da unidade c: à unidade c:\\diretório temporário, o comando for concluída com êxito, mas os ficheiros no diretório New.Directory não são copiados.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="b8a0d-139">Se exibir o conteúdo do **c:\\temp\\New.Directory**, descobrirá que não contém ficheiros:</span><span class="sxs-lookup"><span data-stu-id="b8a0d-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="b8a0d-140">Por que não a **Copy-Item** cmdlet copie o conteúdo para a nova localização?</span><span class="sxs-lookup"><span data-stu-id="b8a0d-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="b8a0d-141">O **Copy-Item** cmdlet foi projetado para ser genérico; não é apenas para copiar ficheiros e pastas.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="b8a0d-142">Além disso, mesmo quando a copiar ficheiros e pastas, talvez queira copiar apenas o contentor e não os itens dentro do mesmo.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="b8a0d-143">Para copiar o conteúdo inteiro de uma pasta, inclua o **Recurse** parâmetro do **Copy-Item** cmdlet no comando.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="b8a0d-144">Se já tiver copiado o diretório sem o seu conteúdo, adicione a **força** parâmetro, que permite-lhe substituir a pasta vazia.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

## <a name="deleting-items-remove-item"></a><span data-ttu-id="b8a0d-145">A eliminar itens (Remove-Item)</span><span class="sxs-lookup"><span data-stu-id="b8a0d-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="b8a0d-146">Para eliminar ficheiros e pastas, utilize o **Remove-Item** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="b8a0d-147">Cmdlets do Windows PowerShell, tal como **Remove-Item**, que pode tornar significativo, muitas vezes, irão pedir alterações irreversível confirmação quando inserir seus comandos.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="b8a0d-148">Por exemplo, se tentar remover a **New.Directory** pasta, será solicitado a confirmar o comando, porque a pasta contém arquivos:</span><span class="sxs-lookup"><span data-stu-id="b8a0d-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="b8a0d-149">Uma vez **Sim** é a resposta padrão, para eliminar a pasta e os respetivos ficheiros, prima a **Enter** chave.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="b8a0d-150">Para remover a pasta sem confirmar, utilize o **-Recurse** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a><span data-ttu-id="b8a0d-151">Itens em execução (Invoke-Item)</span><span class="sxs-lookup"><span data-stu-id="b8a0d-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="b8a0d-152">Windows PowerShell utiliza a **Invoke-Item** cmdlet para efetuar uma ação padrão para um ficheiro ou pasta.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="b8a0d-153">Esta ação de predefinição é determinada pelo manipulador de aplicativo padrão no Registro; o efeito é o mesmo como se clicar duas vezes o item no Explorador de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="b8a0d-154">Por exemplo, suponha que execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b8a0d-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="b8a0d-155">Uma janela do Explorer que está localizada na unidade c:\\Windows é apresentada, tal como se tivesse clicar duas vezes a unidade c:\\pasta Windows.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="b8a0d-156">Se invoca o **Boot. ini** arquivo num sistema antes do Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="b8a0d-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="b8a0d-157">Se o tipo de ficheiro. ini está associado com o bloco de notas, abre o ficheiro Boot. ini no bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="b8a0d-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>
