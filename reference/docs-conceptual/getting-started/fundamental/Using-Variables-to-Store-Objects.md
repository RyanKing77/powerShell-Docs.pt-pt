---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar Variáveis para Armazenar Objetos
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: e52f0a344d0ad13db42b34bed912d584c99b0e30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953332"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="e6051-103">Utilizar Variáveis para Armazenar Objetos</span><span class="sxs-lookup"><span data-stu-id="e6051-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="e6051-104">PowerShell funciona com objetos.</span><span class="sxs-lookup"><span data-stu-id="e6051-104">PowerShell works with objects.</span></span> <span data-ttu-id="e6051-105">PowerShell permite-lhe criar variáveis, essencialmente com o nome de objetos, para preservar a saída para utilização posterior.</span><span class="sxs-lookup"><span data-stu-id="e6051-105">PowerShell lets you create variables, essentially named objects, to preserve output for later use.</span></span> <span data-ttu-id="e6051-106">Se forem utilizados para trabalhar com variáveis noutras shells Lembre-se de que as variáveis de PowerShell são objetos, não texto.</span><span class="sxs-lookup"><span data-stu-id="e6051-106">If you are used to working with variables in other shells remember that PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="e6051-107">Variáveis são sempre especificadas com o caráter inicial $ e podem incluir quaisquer carateres alfanuméricos ou o caráter de sublinhado nos respetivos nomes.</span><span class="sxs-lookup"><span data-stu-id="e6051-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="e6051-108">Criar uma variável</span><span class="sxs-lookup"><span data-stu-id="e6051-108">Creating a Variable</span></span>
<span data-ttu-id="e6051-109">Pode criar uma variável, escrevendo um nome de variável válido:</span><span class="sxs-lookup"><span data-stu-id="e6051-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="e6051-110">Esta ação não devolve nenhum resultado porque **$loc** não tem um valor.</span><span class="sxs-lookup"><span data-stu-id="e6051-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="e6051-111">Pode criar uma variável e atribua-lhe um valor no mesmo passo.</span><span class="sxs-lookup"><span data-stu-id="e6051-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="e6051-112">PowerShell apenas cria a variável se não existir; caso contrário, atribui o valor especificado para a variável existente.</span><span class="sxs-lookup"><span data-stu-id="e6051-112">PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="e6051-113">Para armazenar a sua localização atual na variável **$loc**, tipo:</span><span class="sxs-lookup"><span data-stu-id="e6051-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="e6051-114">Não há nenhuma saída apresentada quando escreva este comando porque o resultado é enviado para $loc.</span><span class="sxs-lookup"><span data-stu-id="e6051-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="e6051-115">No PowerShell, o resultado apresentado é um efeito de facto de dados, que não é; caso contrário, direcionado, sempre são enviados para o ecrã.</span><span class="sxs-lookup"><span data-stu-id="e6051-115">In PowerShell, displayed output is a side effect of the fact that data, which is not otherwise directed, always gets sent to the screen.</span></span> <span data-ttu-id="e6051-116">Escrever $loc mostrará a sua localização atual:</span><span class="sxs-lookup"><span data-stu-id="e6051-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="e6051-117">Pode utilizar **Get-membro** para apresentar informações sobre o conteúdo das variáveis.</span><span class="sxs-lookup"><span data-stu-id="e6051-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="e6051-118">Encaminhando $loc Get-membro irá mostrar-lhe que é um **PathInfo** objeto, tal como o resultado de Get-localização:</span><span class="sxs-lookup"><span data-stu-id="e6051-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="e6051-119">Manipulação de variáveis</span><span class="sxs-lookup"><span data-stu-id="e6051-119">Manipulating Variables</span></span>
<span data-ttu-id="e6051-120">PowerShell fornece vários comandos para manipular variáveis.</span><span class="sxs-lookup"><span data-stu-id="e6051-120">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="e6051-121">Pode ver uma lista completa num formulário legível escrevendo:</span><span class="sxs-lookup"><span data-stu-id="e6051-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="e6051-122">Para além das variáveis de que criar na sua sessão atual do PowerShell, existem várias variáveis definidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="e6051-122">In addition to the variables you create in your current PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="e6051-123">Pode utilizar o **Remove-Variable** cmdlet para limpar terminar todas as variáveis que não são controladas através do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6051-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by PowerShell.</span></span> <span data-ttu-id="e6051-124">Escreva o seguinte comando para limpar todas as variáveis:</span><span class="sxs-lookup"><span data-stu-id="e6051-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="e6051-125">Isto produzirá o pedido de confirmação, que veja a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6051-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="e6051-126">Se, em seguida, executar o **Get-Variable** cmdlet, verá as variáveis de PowerShell restantes.</span><span class="sxs-lookup"><span data-stu-id="e6051-126">If you then run the **Get-Variable** cmdlet, you will see the remaining PowerShell variables.</span></span> <span data-ttu-id="e6051-127">Uma vez que também é uma variável de unidade do PowerShell, também pode apresentar todas as variáveis de PowerShell, escrevendo:</span><span class="sxs-lookup"><span data-stu-id="e6051-127">Since there is also a variable PowerShell drive, you can also display all PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="e6051-128">Utilizar variáveis Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="e6051-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="e6051-129">Apesar de PowerShell não Cmd.exe, é executado num ambiente de shell de comandos e pode utilizar as variáveis mesmas disponíveis em qualquer ambiente do Windows.</span><span class="sxs-lookup"><span data-stu-id="e6051-129">Although PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="e6051-130">Estas variáveis são expostas através de uma unidade com o nome **env**:.</span><span class="sxs-lookup"><span data-stu-id="e6051-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="e6051-131">Pode ver estas variáveis, escrevendo:</span><span class="sxs-lookup"><span data-stu-id="e6051-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="e6051-132">Embora os cmdlets de variável padrão não foram concebidos para funcionar com **env:** variáveis, pode continuar a utilizá-los, especificando o **env:** prefixo.</span><span class="sxs-lookup"><span data-stu-id="e6051-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="e6051-133">Por exemplo, para ver o diretório de raiz do sistema operativo, pode utilizar a shell de comandos **% SystemRoot %** variável do PowerShell, escrevendo:</span><span class="sxs-lookup"><span data-stu-id="e6051-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="e6051-134">Também pode criar e modificar variáveis de ambiente de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6051-134">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="e6051-135">Variáveis de ambiente acedidas a partir do Windows PowerShell está em conformidade com as regras normais nas variáveis de ambiente noutro local do Windows.</span><span class="sxs-lookup"><span data-stu-id="e6051-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>