---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Utilizar Variáveis para Armazenar Objetos
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030363"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="bd703-103">Utilizar variáveis para armazenar objetos</span><span class="sxs-lookup"><span data-stu-id="bd703-103">Using variables to store objects</span></span>

<span data-ttu-id="bd703-104">PowerShell funciona com objetos.</span><span class="sxs-lookup"><span data-stu-id="bd703-104">PowerShell works with objects.</span></span> <span data-ttu-id="bd703-105">PowerShell permite-lhe criar objetos nomeados, conhecidos como variáveis.</span><span class="sxs-lookup"><span data-stu-id="bd703-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="bd703-106">Os nomes das variáveis podem incluir o caráter de sublinhado e quaisquer carateres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="bd703-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="bd703-107">Quando utilizado no PowerShell, uma variável é sempre especificada usando a \$ caracteres seguido pelo nome da variável.</span><span class="sxs-lookup"><span data-stu-id="bd703-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="bd703-108">Criar uma variável</span><span class="sxs-lookup"><span data-stu-id="bd703-108">Creating a variable</span></span>

<span data-ttu-id="bd703-109">Pode criar uma variável, escrevendo um nome de variável válido:</span><span class="sxs-lookup"><span data-stu-id="bd703-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="bd703-110">Neste exemplo não retornará nenhum resultado porque `$loc` não tem um valor.</span><span class="sxs-lookup"><span data-stu-id="bd703-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="bd703-111">Pode criar uma variável e atribua-lhe um valor na mesma etapa.</span><span class="sxs-lookup"><span data-stu-id="bd703-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="bd703-112">PowerShell cria a variável apenas se não existir.</span><span class="sxs-lookup"><span data-stu-id="bd703-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="bd703-113">Caso contrário, atribui o valor especificado para a variável existente.</span><span class="sxs-lookup"><span data-stu-id="bd703-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="bd703-114">O exemplo seguinte armazena a localização atual na variável `$loc`:</span><span class="sxs-lookup"><span data-stu-id="bd703-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="bd703-115">PowerShell não apresenta nenhuma saída quando digitar este comando.</span><span class="sxs-lookup"><span data-stu-id="bd703-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="bd703-116">PowerShell envia a saída de Get-Location para `$loc`.</span><span class="sxs-lookup"><span data-stu-id="bd703-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="bd703-117">No PowerShell, os dados que não estão atribuídos ou redirecionados são enviados para o ecrã.</span><span class="sxs-lookup"><span data-stu-id="bd703-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="bd703-118">Escrever `$loc` mostra sua localização atual:</span><span class="sxs-lookup"><span data-stu-id="bd703-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="bd703-119">Pode usar `Get-Member` para apresentar informações sobre o conteúdo das variáveis.</span><span class="sxs-lookup"><span data-stu-id="bd703-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="bd703-120">`Get-Member` mostra-lhe que `$loc` é um **PathInfo** objeto, assim como a saída do `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="bd703-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

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

## <a name="manipulating-variables"></a><span data-ttu-id="bd703-121">Manipulação de variáveis</span><span class="sxs-lookup"><span data-stu-id="bd703-121">Manipulating variables</span></span>

<span data-ttu-id="bd703-122">PowerShell fornece vários comandos para manipular as variáveis.</span><span class="sxs-lookup"><span data-stu-id="bd703-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="bd703-123">Pode ver uma lista completa num formato legível digitando:</span><span class="sxs-lookup"><span data-stu-id="bd703-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="bd703-124">PowerShell também cria várias variáveis definidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="bd703-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="bd703-125">Pode utilizar o `Remove-Variable` cmdlet para remover as variáveis, que não são controladas pelo PowerShell, da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="bd703-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="bd703-126">Escreva o seguinte comando para limpar todas as variáveis:</span><span class="sxs-lookup"><span data-stu-id="bd703-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="bd703-127">Depois de executar o comando anterior, o `Get-Variable` cmdlet mostra as variáveis de sistema do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd703-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="bd703-128">PowerShell também cria uma unidade de variável.</span><span class="sxs-lookup"><span data-stu-id="bd703-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="bd703-129">Utilize o exemplo a seguir para exibir todas as variáveis do PowerShell usando a unidade de variável:</span><span class="sxs-lookup"><span data-stu-id="bd703-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="bd703-130">Usando variáveis cmd.exe</span><span class="sxs-lookup"><span data-stu-id="bd703-130">Using cmd.exe variables</span></span>

<span data-ttu-id="bd703-131">PowerShell, pode utilizar as variáveis de ambiente mesmo disponíveis a qualquer processo do Windows, incluindo **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="bd703-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="bd703-132">Estas variáveis são expostas por meio de uma unidade chamada `env:`.</span><span class="sxs-lookup"><span data-stu-id="bd703-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="bd703-133">Pode ver estas variáveis, escrevendo o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="bd703-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="bd703-134">O padrão `*-Variable` cmdlets não são concebidos para trabalhar com variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="bd703-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="bd703-135">Variáveis de ambiente são acessadas usando o `env:` prefixo de unidade.</span><span class="sxs-lookup"><span data-stu-id="bd703-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="bd703-136">Por exemplo, o **% SystemRoot %** variável **cmd.exe** contém o nome de diretório de raiz do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="bd703-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="bd703-137">No PowerShell, utilize `$env:SystemRoot` para acessar o mesmo valor.</span><span class="sxs-lookup"><span data-stu-id="bd703-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="bd703-138">Também pode criar e modificar variáveis de ambiente a partir do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd703-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="bd703-139">Variáveis de ambiente no PowerShell, siga as mesmas regras para variáveis de ambiente utilizadas em outro lugar no sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="bd703-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="bd703-140">O exemplo seguinte cria uma nova variável de ambiente:</span><span class="sxs-lookup"><span data-stu-id="bd703-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="bd703-141">Embora não obrigatório, é comum para nomes de variáveis de ambiente utilizar todas as letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="bd703-141">Though not required, it's common for environment variable names to use all uppercase letters.</span></span>
