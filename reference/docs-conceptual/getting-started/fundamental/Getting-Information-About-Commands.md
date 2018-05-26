---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Obter Informações sobre os Comandos
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: c51579fe2cdf4f2a0d3248d1aaf3f1f9cac83868
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/25/2018
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="a6c2f-103">Obter Informações sobre os Comandos</span><span class="sxs-lookup"><span data-stu-id="a6c2f-103">Getting Information About Commands</span></span>
<span data-ttu-id="a6c2f-104">O Windows PowerShell `Get-Command` cmdlet obtém todos os comandos que estão disponíveis na sua sessão atual.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-104">The Windows PowerShell `Get-Command` cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="a6c2f-105">Quando escrever `Get-Command` na linha de comandos do PowerShell, aparece um resultado semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="a6c2f-105">When you type `Get-Command` at a PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="a6c2f-106">Isto de saída procura muito semelhante a saída de ajuda do Cmd.exe: um resumo dos comandos internos tabular.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="a6c2f-107">No excerpt do **Get-Command** comando saída mostrada acima, cada comando mostrado tem um CommandType de Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="a6c2f-108">Um cmdlet é o tipo de comando intrínseco do Windows PowerShell - um tipo que corresponde aproximadamente ao **dir** e **cd** comandos da Cmd.exe e built-ins no shells de UNIX como BASH.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="a6c2f-109">Na saída do `Get-Command` comando, todas as definições de terminar com nas reticências (…) para indicar que o PowerShell não é possível apresentar todo o conteúdo no espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-109">In the output of the `Get-Command` command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="a6c2f-110">Quando o Windows PowerShell apresenta uma saída, formata o resultado como texto e, em seguida, dispõe para verificar os dados ajustar corretamente a janela.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="a6c2f-111">Serão abordadas isto mais tarde na secção ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="a6c2f-112">O `Get-Command` cmdlet tem um **sintaxe** parâmetro que obtém a sintaxe de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-112">The `Get-Command` cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="a6c2f-113">Para obter a sintaxe do cmdlet Get-Help, utilize o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="a6c2f-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

```
Get-Command Get-Help -Syntax

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a><span data-ttu-id="a6c2f-114">Apresentar os tipos de comando disponíveis</span><span class="sxs-lookup"><span data-stu-id="a6c2f-114">Displaying Available Command Types</span></span>
<span data-ttu-id="a6c2f-115">O **Get-Command** comando não listar todos os comandos que está disponível no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-115">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="a6c2f-116">Em vez disso, o **Get-Command** comando lista apenas os cmdlets na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-116">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="a6c2f-117">O Windows PowerShell, na verdade, suporta vários outros tipos de comandos.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-117">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="a6c2f-118">Aliases, funções e scripts são também comandos do Windows PowerShell, embora estes não são abordados em detalhe no Guia do utilizador do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-118">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="a6c2f-119">Ficheiros externos que são executável ou que têm um processador de tipo de ficheiros registada, também estão classificados como comandos.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-119">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="a6c2f-120">Para obter todos os comandos na sessão, escreva:</span><span class="sxs-lookup"><span data-stu-id="a6c2f-120">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="a6c2f-121">Porque esta lista inclui ficheiros externos no seu caminho de pesquisa, pode conter a milhares de itens.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-121">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="a6c2f-122">É mais útil ver um conjunto de comandos reduzido.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-122">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="a6c2f-123">Para obter comandos nativos de outros tipos, utilize o **CommandType** parâmetro o `Get-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-123">To get native commands of other types, use the **CommandType** parameter of the `Get-Command` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="a6c2f-124">O asterisco (\*) é utilizado para correspondência nos argumentos de comando do Windows PowerShell de caracteres universais.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-124">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="a6c2f-125">O \* significa "corresponde uma ou mais caracteres".</span><span class="sxs-lookup"><span data-stu-id="a6c2f-125">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="a6c2f-126">Pode escrever `Get-Command a*` para localizar todos os comandos que começam com a letra "a".</span><span class="sxs-lookup"><span data-stu-id="a6c2f-126">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="a6c2f-127">Ao contrário do caráter universal correspondente no Cmd.exe, universal do Windows PowerShell irá também de coincidir com um período.</span><span class="sxs-lookup"><span data-stu-id="a6c2f-127">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="a6c2f-128">Para obter os aliases de comando, que são os nicknames atribuídos de comandos, escreva:</span><span class="sxs-lookup"><span data-stu-id="a6c2f-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="a6c2f-129">Para obter as funções na sessão atual, escreva:</span><span class="sxs-lookup"><span data-stu-id="a6c2f-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="a6c2f-130">Para apresentar scripts no caminho de pesquisa do Windows PowerShell, escreva:</span><span class="sxs-lookup"><span data-stu-id="a6c2f-130">To display scripts in Windows PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```
