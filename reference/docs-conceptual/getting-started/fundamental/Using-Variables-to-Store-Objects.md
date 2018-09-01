---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Utilizar Variáveis para Armazenar Objetos
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: f4254199facb914c68a487b281b30070c35550a1
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353223"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="31cd1-103">Utilizar variáveis para armazenar objetos</span><span class="sxs-lookup"><span data-stu-id="31cd1-103">Using variables to store objects</span></span>

<span data-ttu-id="31cd1-104">PowerShell funciona com objetos.</span><span class="sxs-lookup"><span data-stu-id="31cd1-104">PowerShell works with objects.</span></span> <span data-ttu-id="31cd1-105">PowerShell permite-lhe criar objetos nomeados, conhecidos como variáveis.</span><span class="sxs-lookup"><span data-stu-id="31cd1-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="31cd1-106">Nomes de variáveis podem incluir a lata de caráter de sublinhado quaisquer carateres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="31cd1-106">Variables names can include the underscore character can any alphanumeric characters.</span></span> <span data-ttu-id="31cd1-107">Quando utilizado no PowerShell, uma variável é sempre especificada usando a \$ caracteres seguido pelo nome da variável.</span><span class="sxs-lookup"><span data-stu-id="31cd1-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="31cd1-108">Criar uma variável</span><span class="sxs-lookup"><span data-stu-id="31cd1-108">Creating a variable</span></span>

<span data-ttu-id="31cd1-109">Pode criar uma variável, escrevendo um nome de variável válido:</span><span class="sxs-lookup"><span data-stu-id="31cd1-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="31cd1-110">Neste exemplo não retornará nenhum resultado porque `$loc` não tem um valor.</span><span class="sxs-lookup"><span data-stu-id="31cd1-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="31cd1-111">Pode criar uma variável e atribua-lhe um valor na mesma etapa.</span><span class="sxs-lookup"><span data-stu-id="31cd1-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="31cd1-112">PowerShell cria a variável apenas se não existir.</span><span class="sxs-lookup"><span data-stu-id="31cd1-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="31cd1-113">Caso contrário, atribui o valor especificado para a variável existente.</span><span class="sxs-lookup"><span data-stu-id="31cd1-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="31cd1-114">O exemplo seguinte armazena a localização atual na variável `$loc`:</span><span class="sxs-lookup"><span data-stu-id="31cd1-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="31cd1-115">PowerShell não apresenta nenhuma saída quando digitar este comando.</span><span class="sxs-lookup"><span data-stu-id="31cd1-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="31cd1-116">PowerShell envia a saída de Get-Location para `$loc`.</span><span class="sxs-lookup"><span data-stu-id="31cd1-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="31cd1-117">No PowerShell, os dados que não estão atribuídos ou redirecionados são enviados para o ecrã.</span><span class="sxs-lookup"><span data-stu-id="31cd1-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="31cd1-118">Escrever `$loc` mostra sua localização atual:</span><span class="sxs-lookup"><span data-stu-id="31cd1-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="31cd1-119">Pode usar `Get-Member` para apresentar informações sobre o conteúdo das variáveis.</span><span class="sxs-lookup"><span data-stu-id="31cd1-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="31cd1-120">`Get-Member` mostra-lhe que `$loc` é um **PathInfo** objeto, assim como a saída do `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="31cd1-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="31cd1-121">Manipulação de variáveis</span><span class="sxs-lookup"><span data-stu-id="31cd1-121">Manipulating variables</span></span>

<span data-ttu-id="31cd1-122">PowerShell fornece vários comandos para manipular as variáveis.</span><span class="sxs-lookup"><span data-stu-id="31cd1-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="31cd1-123">Pode ver uma lista completa num formato legível digitando:</span><span class="sxs-lookup"><span data-stu-id="31cd1-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="31cd1-124">PowerShell também cria várias variáveis definidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="31cd1-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="31cd1-125">Pode utilizar o `Remove-Variable` cmdlet para remover as variáveis, que não são controladas pelo PowerShell, da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="31cd1-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="31cd1-126">Escreva o seguinte comando para limpar todas as variáveis:</span><span class="sxs-lookup"><span data-stu-id="31cd1-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="31cd1-127">Depois de executar o comando anterior, o `Get-Variable` cmdlet mostra as variáveis de sistema do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31cd1-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="31cd1-128">PowerShell também cria uma unidade de variável.</span><span class="sxs-lookup"><span data-stu-id="31cd1-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="31cd1-129">Utilize o exemplo a seguir para exibir todas as variáveis do PowerShell usando a unidade de variável:</span><span class="sxs-lookup"><span data-stu-id="31cd1-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="31cd1-130">Usando variáveis cmd.exe</span><span class="sxs-lookup"><span data-stu-id="31cd1-130">Using cmd.exe variables</span></span>

<span data-ttu-id="31cd1-131">PowerShell, pode utilizar as variáveis de ambiente mesmo disponíveis a qualquer processo do Windows, incluindo **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="31cd1-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="31cd1-132">Estas variáveis são expostas por meio de uma unidade chamada `env:`.</span><span class="sxs-lookup"><span data-stu-id="31cd1-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="31cd1-133">Pode ver estas variáveis, escrevendo o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="31cd1-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="31cd1-134">O padrão `*-Variable` cmdlets não são concebidos para trabalhar com variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="31cd1-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="31cd1-135">Variáveis de ambiente são acessadas usando o `env:` prefixo de unidade.</span><span class="sxs-lookup"><span data-stu-id="31cd1-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="31cd1-136">Por exemplo, o **% SystemRoot %** variável **cmd.exe** contém o nome de diretório de raiz do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="31cd1-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="31cd1-137">No PowerShell, utilize `$env:SystemRoot` para acessar o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="31cd1-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="31cd1-138">Também pode criar e modificar variáveis de ambiente a partir do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31cd1-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="31cd1-139">Variáveis de ambiente no PowerShell, siga as mesmas regras para variáveis de ambiente utilizadas em outro lugar no sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="31cd1-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="31cd1-140">O exemplo seguinte cria uma nova variável de ambiente:</span><span class="sxs-lookup"><span data-stu-id="31cd1-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="31cd1-141">Embora não obrigatório, é comum para nomes de variáveis de ambiente utilizar todas as letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="31cd1-141">Though not required, is it common for environment variable names to use all uppercase letters.</span></span>