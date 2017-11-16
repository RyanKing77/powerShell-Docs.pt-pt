---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Gerir a localização atual"
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: cbdebb84b3191e3bd549a1cf344cbeefaa91a23c
ms.sourcegitcommit: c5251755c4442487f99ff74fadf7e37bbf039089
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/18/2017
---
# <a name="managing-current-location"></a><span data-ttu-id="a4a2a-103">Gerir a localização atual</span><span class="sxs-lookup"><span data-stu-id="a4a2a-103">Managing Current Location</span></span>
<span data-ttu-id="a4a2a-104">Quando navegar sistemas de pasta no Explorador de ficheiros, normalmente, têm de uma localização de trabalho específica - nomeadamente, abra pasta atual.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="a4a2a-105">Itens na pasta atual podem ser manipulados facilmente clicando-los.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="a4a2a-106">Para interfaces de linha de comandos como Cmd.exe, quando estão na mesma pasta que um ficheiro específico, pode acedê-lo ao especificar um nome de tempo relativamente curto, em vez de necessidade de especificar o caminho completo para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="a4a2a-107">O diretório atual é denominado o diretório de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="a4a2a-108">O Windows PowerShell utiliza o substantivo **localização** para fazer referência ao diretório de trabalho e implementa uma família de cmdlets para examinar e manipular a sua localização.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

### <a name="getting-your-current-location-get-location"></a><span data-ttu-id="a4a2a-109">Obter a localização atual (Get-Location)</span><span class="sxs-lookup"><span data-stu-id="a4a2a-109">Getting Your Current Location (Get-Location)</span></span>
<span data-ttu-id="a4a2a-110">Para determinar o caminho da sua localização do diretório atual, introduza o **Get-Location** comando:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="a4a2a-111">O cmdlet Get-Location é semelhante para o **pwd** comando na shell de DETEÇÃO.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="a4a2a-112">O cmdlet Set-Location é semelhante para o **cd** no Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

### <a name="setting-your-current-location-set-location"></a><span data-ttu-id="a4a2a-113">Definir a sua localização atual (localização do conjunto)</span><span class="sxs-lookup"><span data-stu-id="a4a2a-113">Setting Your Current Location (Set-Location)</span></span>
<span data-ttu-id="a4a2a-114">O **Get-Location** comando é utilizado com o **Set-Location** comando.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="a4a2a-115">O **Set-Location** comando permite-lhe especificar a localização do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```
PS> Set-Location -Path C:\Windows
```

<span data-ttu-id="a4a2a-116">Depois de introduzir o comando, irá reparar que não receber quaisquer comentários sobre o efeito do comando direto.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="a4a2a-117">A maioria dos comandos do Windows PowerShell que efetue uma ação produzem resultados de pouca ou nenhuma porque o resultado nem sempre é útil.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="a4a2a-118">Para verificar que uma alteração de directório de êxito ocorreu ao introduzir o **localização do conjunto** comando, que incluem o **- PassThru** parâmetro ao introduzir o **-localização do conjunto**comando:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru
Path
----
C:\WINDOWS
```

<span data-ttu-id="a4a2a-119">O **- PassThru** parâmetro pode ser utilizado com muitos de conjunto de comandos do Windows PowerShell para devolver informações sobre o resultado nos casos em que não há nenhuma saída predefinida.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="a4a2a-120">Pode especificar caminhos relativamente à sua localização atual da mesma forma como os seria na maioria dos UNIX e o Windows comando shells.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="a4a2a-121">Na notação padrão para caminhos relativos, durante um período (**.**) representa a pasta atual e um período doubled (**..** ) representa o diretório principal da sua localização atual.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="a4a2a-122">Por exemplo, se está a **c:\\Windows** pasta, um período (**.**) representa **c:\\Windows** e faça duplo períodos (**..** ) representam **c:**.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="a4a2a-123">Pode alterar da sua localização atual para a raiz da unidade c:, escrevendo:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```powershell
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="a4a2a-124">A mesma técnica funciona em unidades do Windows PowerShell que não estão unidades do sistema de ficheiros, tais como **HKLM:**.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="a4a2a-125">Pode definir a sua localização para o HKLM\\chave de Software no registo, escrevendo:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="a4a2a-126">Em seguida, pode alterar a localização do diretório para o diretório principal, qual é a raiz da HKLM de PowerShell Windows: unidade, utilizando um caminho relativo:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="a4a2a-127">Pode introduzir localização do conjunto ou utilizar qualquer um dos aliases incorporados do Windows PowerShell para Set-Location (cd, chdir, sl).</span><span class="sxs-lookup"><span data-stu-id="a4a2a-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="a4a2a-128">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-128">For example:</span></span>

```
cd -Path C:\Windows
```

```
chdir -Path .. -PassThru
```

```
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="a4a2a-129">Guardar e recupera um recentes localizações (localização de Push e Pop-Location)</span><span class="sxs-lookup"><span data-stu-id="a4a2a-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>
<span data-ttu-id="a4a2a-130">Quando alterar as localizações, é útil para manter um registo de onde foram e conseguir regressar à sua localização anterior.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="a4a2a-131">O **Push-Location** cmdlet no Windows PowerShell cria um histórico ordenado (um "pilha") de caminhos de diretório em que foi e pode seguir novamente o histórico de caminhos de diretório, utilizando o complementares  **POP-Location** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="a4a2a-132">Por exemplo, do Windows PowerShell, normalmente, é iniciada no diretório raiz do utilizador.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="a4a2a-133">A palavra *pilha* tem um significado especial nos muitas definições de programação, incluindo o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="a4a2a-134">Como uma pilha física de itens, o último item que colocar na pilha é o primeiro item que pode solicitar a desativar a pilha.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="a4a2a-135">A adição de um item a uma pilha colloquially é conhecida como "emitir" item na pilha.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="a4a2a-136">Extrair um item desativado a pilha colloquially é conhecido como "popping" item fora da pilha.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="a4a2a-137">Push a localização atual na pilha e, em seguida, mova para a pasta de definições do Local, escreva:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```
PS> Push-Location -Path "Local Settings"
```

<span data-ttu-id="a4a2a-138">Em seguida, pode emitir a localização de definições locais na pilha e e mover para a pasta Temp escrevendo:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-138">You can then push the Local Settings location onto the stack and and move to the Temp folder by typing:</span></span>

```
PS> Push-Location -Path Temp
```

<span data-ttu-id="a4a2a-139">Pode verificar que alterou diretórios introduzindo o **Get-Location** comando:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="a4a2a-140">Pode extrair, em seguida, volta para o diretório mais recentemente visitado introduzindo o **Pop-Location** comando e certifique-se a alteração ao introduzir o **Get-Location** comando:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="a4a2a-141">Apenas como com a **Set-Location** cmdlet, pode incluir o **- PassThru** parâmetro ao introduzir o **Pop-Location** cmdlet para ver o diretório que introduziu:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="a4a2a-142">Também pode utilizar os cmdlets de localização com caminhos de rede.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="a4a2a-143">Se tiver um servidor com o nome FS01 com uma partilha com o nome público, pode alterar a localização, escrevendo</span><span class="sxs-lookup"><span data-stu-id="a4a2a-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```
Set-Location \\FS01\Public
```

<span data-ttu-id="a4a2a-144">ou</span><span class="sxs-lookup"><span data-stu-id="a4a2a-144">or</span></span>

```
Push-Location \\FS01\Public
```

<span data-ttu-id="a4a2a-145">Pode utilizar o **Push-Location** e **Set-Location** comandos para alterar a localização para qualquer unidade disponível.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="a4a2a-146">Por exemplo, se tiver uma unidade de CD-ROM local com letra de unidade D que contém um CD de dados, pode alterar a localização para a unidade de CD introduzindo o **D: de localização do conjunto** comando.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="a4a2a-147">Se a unidade está vazia, obterá a seguinte mensagem de erro:</span><span class="sxs-lookup"><span data-stu-id="a4a2a-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="a4a2a-148">Quando estiver a utilizar uma interface de linha de comandos, não é conveniente utilizar o Explorador de ficheiros para examinar as unidades físicas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="a4a2a-149">Além disso, Explorador de ficheiros iria não mostram-lhe a todas as unidades do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="a4a2a-150">O Windows PowerShell oferece um conjunto de comandos para manipular unidades do Windows PowerShell e serão abordadas estes seguinte.</span><span class="sxs-lookup"><span data-stu-id="a4a2a-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>

