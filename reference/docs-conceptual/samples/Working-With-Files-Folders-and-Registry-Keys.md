---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Pastas de Ficheiros e Chaves do Registo
ms.openlocfilehash: 0c8716c384827d0816e2847ff81232c14638681b
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030757"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="56ae2-103">Trabalhar com arquivos, pastas e chaves de registo</span><span class="sxs-lookup"><span data-stu-id="56ae2-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="56ae2-104">Windows PowerShell utiliza o substantivo **Item** para fazer referência a itens encontrados numa unidade do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56ae2-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="56ae2-105">Ao lidar com o fornecedor do sistema de ficheiros do Windows PowerShell, uma **Item** pode ser um arquivo, uma pasta ou unidade do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56ae2-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="56ae2-106">Listagem e trabalhar com estes itens são uma tarefa de básica crítica na maioria das definições administrativas, para que o que queremos abordar essas tarefas em detalhes.</span><span class="sxs-lookup"><span data-stu-id="56ae2-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="56ae2-107">A enumerar os arquivos, pastas e chaves do Registro (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="56ae2-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="56ae2-108">Como obter uma coleção de itens a partir de uma localização específica é uma tarefa comum, o **Get-ChildItem** cmdlet foi desenvolvido especificamente para retornar todos os itens encontrados dentro de um contêiner como uma pasta.</span><span class="sxs-lookup"><span data-stu-id="56ae2-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="56ae2-109">Se quiser retornar todos os ficheiros e pastas que estão contidas diretamente dentro da pasta c:\\Windows, tipo:</span><span class="sxs-lookup"><span data-stu-id="56ae2-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

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

<span data-ttu-id="56ae2-110">A listagem assemelha-se de que o que veria ao introduzir o **dir** comando **Cmd.exe**, ou o **ls** comando numa shell de comando de UNIX.</span><span class="sxs-lookup"><span data-stu-id="56ae2-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="56ae2-111">Pode efetuar as listagens muito complexas, utilizando parâmetros do **Get-ChildItem** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56ae2-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="56ae2-112">Vamos ver alguns cenários a seguir.</span><span class="sxs-lookup"><span data-stu-id="56ae2-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="56ae2-113">Pode ver a sintaxe da **Get-ChildItem** cmdlet digitando:</span><span class="sxs-lookup"><span data-stu-id="56ae2-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="56ae2-114">Esses parâmetros podem ser misturados e correspondentes para obter uma saída altamente personalizável.</span><span class="sxs-lookup"><span data-stu-id="56ae2-114">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="56ae2-115">Listar todos os itens contidos (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="56ae2-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="56ae2-116">Para ver os itens dentro de uma pasta do Windows e todos os itens que estão contidos dentro as subpastas, utilize o **Recurse** parâmetro do **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="56ae2-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="56ae2-117">A listagem apresenta tudo dentro da pasta do Windows e os itens em suas subpastas.</span><span class="sxs-lookup"><span data-stu-id="56ae2-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="56ae2-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="56ae2-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="56ae2-119">Filtrar itens por nome (-nome)</span><span class="sxs-lookup"><span data-stu-id="56ae2-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="56ae2-120">Para apresentar apenas os nomes de itens, utilize o **Name** parâmetro do **Get-Childitem**:</span><span class="sxs-lookup"><span data-stu-id="56ae2-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="56ae2-121">A forçar a listagem itens ocultos (-Force)</span><span class="sxs-lookup"><span data-stu-id="56ae2-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="56ae2-122">Itens que são normalmente invisíveis no Explorador de ficheiros ou Cmd.exe não são apresentados no resultado de uma **Get-ChildItem** comando.</span><span class="sxs-lookup"><span data-stu-id="56ae2-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="56ae2-123">Para exibir itens ocultos, use o **força** parâmetro do **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="56ae2-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="56ae2-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="56ae2-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="56ae2-125">Este parâmetro com o nome força porque a forçar pode substituir o comportamento normal da **Get-ChildItem** comando.</span><span class="sxs-lookup"><span data-stu-id="56ae2-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="56ae2-126">Force é um parâmetro amplamente usado que força uma ação que um cmdlet não seria normalmente executam, apesar de não executará nenhuma ação que compromete a segurança do sistema.</span><span class="sxs-lookup"><span data-stu-id="56ae2-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="56ae2-127">Correspondência de nomes de Item com carateres universais</span><span class="sxs-lookup"><span data-stu-id="56ae2-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="56ae2-128">**O Get-ChildItem** comando aceita carateres universais no caminho dos itens de lista.</span><span class="sxs-lookup"><span data-stu-id="56ae2-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="56ae2-129">Porque a correspondência de carateres universais é processada pelo mecanismo do Windows PowerShell, todos os cmdlets que aceita carateres universais utilizar a mesma notação e têm o mesmo comportamento correspondente.</span><span class="sxs-lookup"><span data-stu-id="56ae2-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="56ae2-130">A notação de caráter universal do Windows PowerShell inclui:</span><span class="sxs-lookup"><span data-stu-id="56ae2-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="56ae2-131">Asterisco (\*) corresponde a zero ou mais ocorrências de qualquer caractere.</span><span class="sxs-lookup"><span data-stu-id="56ae2-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="56ae2-132">Ponto de interrogação (?) corresponde a exatamente um caractere.</span><span class="sxs-lookup"><span data-stu-id="56ae2-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="56ae2-133">Parênteses Reto de abertura (\[) caráter e o caráter de Reto (]) envolvem um conjunto de caracteres para corresponder.</span><span class="sxs-lookup"><span data-stu-id="56ae2-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="56ae2-134">Aqui estão alguns exemplos de como funciona a especificação de caráter universal.</span><span class="sxs-lookup"><span data-stu-id="56ae2-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="56ae2-135">Para localizar todos os ficheiros no diretório do Windows com o sufixo **. log** e exatamente cinco caracteres no nome de base, introduza o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="56ae2-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

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

<span data-ttu-id="56ae2-136">Para localizar todos os ficheiros que começam com a letra **x** no diretório do Windows, escreva:</span><span class="sxs-lookup"><span data-stu-id="56ae2-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="56ae2-137">Para localizar todos os arquivos cujos nomes comecem com **x** ou **z**, tipo:</span><span class="sxs-lookup"><span data-stu-id="56ae2-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a><span data-ttu-id="56ae2-138">Excluir itens (-excluir)</span><span class="sxs-lookup"><span data-stu-id="56ae2-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="56ae2-139">Pode excluir itens específicos, utilizando o **excluir** parâmetro de Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="56ae2-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="56ae2-140">Isto permite-lhe efetuar complexos de filtragem numa única instrução.</span><span class="sxs-lookup"><span data-stu-id="56ae2-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="56ae2-141">Por exemplo, suponha que está tentando encontrar a DLL de serviço de hora do Windows na pasta System32, e tudo o que pode se lembrar sobre o nome da DLL é que começa com "W" e tem "32" nela.</span><span class="sxs-lookup"><span data-stu-id="56ae2-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="56ae2-142">Uma expressão, como **w\&#42; 32\&#42;. dll** irá encontrar todas as DLLs que cumprem as condições, mas ele pode retornar também o Windows 95 e compatibilidade do Windows de 16 bits DLLs que incluem "95" ou "16" nos respetivos nomes.</span><span class="sxs-lookup"><span data-stu-id="56ae2-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="56ae2-143">Pode omitir ficheiros com qualquer um desses números nos respetivos nomes utilizando o **excluir** parâmetro com o padrão  **\&#42;\[ 9516]\&#42;** :</span><span class="sxs-lookup"><span data-stu-id="56ae2-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

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

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="56ae2-144">Misturar os parâmetros de Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="56ae2-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="56ae2-145">Pode utilizar vários dos parâmetros do **Get-ChildItem** cmdlet no mesmo comando.</span><span class="sxs-lookup"><span data-stu-id="56ae2-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="56ae2-146">Antes de misturar parâmetros, certifique-se de que compreende a correspondência de carateres universais.</span><span class="sxs-lookup"><span data-stu-id="56ae2-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="56ae2-147">Por exemplo, o comando seguinte devolve não existem resultados:</span><span class="sxs-lookup"><span data-stu-id="56ae2-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="56ae2-148">Não há nenhum resultado, muito embora haja duas DLLs que começam com a letra "z", na pasta Windows.</span><span class="sxs-lookup"><span data-stu-id="56ae2-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="56ae2-149">Não foram devolvidos resultados porque foi especificado o caráter universal como parte do caminho.</span><span class="sxs-lookup"><span data-stu-id="56ae2-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="56ae2-150">Embora o comando foi recursiva, o **Get-ChildItem** cmdlet restrito os itens para os que estão na pasta do Windows com nomes que termina com ". dll".</span><span class="sxs-lookup"><span data-stu-id="56ae2-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="56ae2-151">Para especificar uma pesquisa recursiva para arquivos cujos nomes correspondem a um padrão especial, utilize o **-incluem** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="56ae2-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

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
