---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Obter informações sobre os comandos
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 7af83e3a0e776d96e580b442430357b4ea063a72
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405510"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="d3c94-103">Obter informações sobre os comandos</span><span class="sxs-lookup"><span data-stu-id="d3c94-103">Getting information about commands</span></span>

<span data-ttu-id="d3c94-104">O PowerShell `Get-Command` apresenta os comandos que estão disponíveis na sua sessão atual.</span><span class="sxs-lookup"><span data-stu-id="d3c94-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="d3c94-105">Quando executa o `Get-Command` cmdlet, verá algo semelhante à seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d3c94-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

<span data-ttu-id="d3c94-106">Esta saída se parece muito como a saída de ajuda de **cmd.exe**: um resumo em tabela de comandos internos.</span><span class="sxs-lookup"><span data-stu-id="d3c94-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="d3c94-107">No trecho do `Get-Command` comando mostrada acima, cada comando mostrado de saída tem um CommandType de Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d3c94-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="d3c94-108">Um cmdlet é o tipo de comando intrínsecos do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3c94-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="d3c94-109">Este tipo corresponde mais ou menos para comandos como `dir` e `cd` na **cmd.exe** ou os comandos internos de shells do Unix, como bash.</span><span class="sxs-lookup"><span data-stu-id="d3c94-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="d3c94-110">O `Get-Command` cmdlet tem um **sintaxe** parâmetro que retorna a sintaxe de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d3c94-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="d3c94-111">O exemplo seguinte mostra como obter a sintaxe do `Get-Help` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="d3c94-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="d3c94-112">Exibição de comando disponíveis por tipo</span><span class="sxs-lookup"><span data-stu-id="d3c94-112">Displaying available command by type</span></span>

<span data-ttu-id="d3c94-113">O `Get-Command` comando lista apenas os cmdlets na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="d3c94-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="d3c94-114">Na verdade, o PowerShell suporta vários outros tipos de comandos:</span><span class="sxs-lookup"><span data-stu-id="d3c94-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="d3c94-115">Aliases</span><span class="sxs-lookup"><span data-stu-id="d3c94-115">Aliases</span></span>
- <span data-ttu-id="d3c94-116">Funções</span><span class="sxs-lookup"><span data-stu-id="d3c94-116">Functions</span></span>
- <span data-ttu-id="d3c94-117">Scripts</span><span class="sxs-lookup"><span data-stu-id="d3c94-117">Scripts</span></span>

<span data-ttu-id="d3c94-118">Arquivos executáveis externos ou ficheiros que tenham um manipulador de tipo de ficheiros registada, também estão classificados como comandos.</span><span class="sxs-lookup"><span data-stu-id="d3c94-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="d3c94-119">Para obter todos os comandos na sessão, escreva:</span><span class="sxs-lookup"><span data-stu-id="d3c94-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="d3c94-120">Esta lista inclui os comandos externos no seu caminho de pesquisa para que ele pode conter milhares de itens.</span><span class="sxs-lookup"><span data-stu-id="d3c94-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="d3c94-121">É mais útil examinar um conjunto reduzido de comandos.</span><span class="sxs-lookup"><span data-stu-id="d3c94-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="d3c94-122">O asterisco (\*) é utilizado para o caráter universal correspondente nos argumentos de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3c94-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="d3c94-123">O \* significa "corresponde uma ou mais das quaisquer carateres".</span><span class="sxs-lookup"><span data-stu-id="d3c94-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="d3c94-124">Pode digitar `Get-Command a*` para localizar todos os comandos que começam com a letra "a".</span><span class="sxs-lookup"><span data-stu-id="d3c94-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="d3c94-125">Ao contrário de correspondência de carateres universais no **cmd.exe**, universais do PowerShell irão também de coincidir com um período.</span><span class="sxs-lookup"><span data-stu-id="d3c94-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="d3c94-126">Utilize o **CommandType** parâmetro do `Get-Command` para obter comandos nativos de outros tipos.</span><span class="sxs-lookup"><span data-stu-id="d3c94-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="d3c94-127">cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d3c94-127">cmdlet.</span></span>

<span data-ttu-id="d3c94-128">Para obter os aliases de comandos, que são os nicknames atribuídos de comandos, escreva:</span><span class="sxs-lookup"><span data-stu-id="d3c94-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="d3c94-129">Para obter as funções na sessão atual, escreva:</span><span class="sxs-lookup"><span data-stu-id="d3c94-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="d3c94-130">Para ver scripts no caminho de pesquisa do PowerShell, escreva:</span><span class="sxs-lookup"><span data-stu-id="d3c94-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```