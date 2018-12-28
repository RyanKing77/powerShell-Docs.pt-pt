---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Script do PowerShell
ms.openlocfilehash: 07925ce8dcafd33970a703c9b241bf6f76f88d10
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405205"
---
# <a name="powershell"></a><span data-ttu-id="c96b2-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="c96b2-103">PowerShell</span></span>

<span data-ttu-id="c96b2-104">O PowerShell é um shell de linha de comandos baseada em tarefas e linguagem de script parte do .NET.</span><span class="sxs-lookup"><span data-stu-id="c96b2-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="c96b2-105">Os administradores de sistema de ajuda do PowerShell e usuários avançados rapidamente a automatizar tarefas que gerem os sistemas operativos (Linux, macOS e Windows) e os processos.</span><span class="sxs-lookup"><span data-stu-id="c96b2-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="c96b2-106">Comandos do PowerShell permitem-lhe gerir computadores a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c96b2-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="c96b2-107">Fornecedores de PowerShell permitem-lhe aceder aos arquivos de dados, como o registro e tão facilmente quanto acessar o sistema de ficheiros de arquivo, de certificados.</span><span class="sxs-lookup"><span data-stu-id="c96b2-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="c96b2-108">PowerShell inclui um analisador de expressão avançada e uma linguagem de script inteiramente desenvolvida.</span><span class="sxs-lookup"><span data-stu-id="c96b2-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="c96b2-109">O PowerShell é o código-fonte aberto</span><span class="sxs-lookup"><span data-stu-id="c96b2-109">PowerShell is open-source</span></span>

<span data-ttu-id="c96b2-110">Código-fonte base do PowerShell está agora disponível no GitHub e aberta a contribuições da Comunidade.</span><span class="sxs-lookup"><span data-stu-id="c96b2-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="c96b2-111">Ver [PowerShell fonte no GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="c96b2-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="c96b2-112">Pode começar com os bits que necessita em [PowerShell obter](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="c96b2-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="c96b2-113">Ou, talvez, com uma visita guiada às [introdução ao](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="c96b2-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="c96b2-114">Metas de design do PowerShell</span><span class="sxs-lookup"><span data-stu-id="c96b2-114">PowerShell design goals</span></span>

<span data-ttu-id="c96b2-115">PowerShell foi projetado para melhorar o ambiente de criação de scripts e linha de comandos, eliminando consideravelmente os problemas de longa data e a acrescentar novas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="c96b2-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="c96b2-116">Capacidade de deteção</span><span class="sxs-lookup"><span data-stu-id="c96b2-116">Discoverability</span></span>

<span data-ttu-id="c96b2-117">PowerShell torna mais fácil detetar os seus recursos.</span><span class="sxs-lookup"><span data-stu-id="c96b2-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="c96b2-118">Por exemplo, para encontrar uma lista de cmdlets que ver e alterar os serviços do Windows, escreva:</span><span class="sxs-lookup"><span data-stu-id="c96b2-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="c96b2-119">Depois de descobrir qual cmdlet realiza uma tarefa, pode saber mais sobre o cmdlet, utilizando o `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c96b2-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="c96b2-120">Por exemplo, para apresentar a ajuda sobre o `Get-Service` cmdlet, tipo:</span><span class="sxs-lookup"><span data-stu-id="c96b2-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="c96b2-121">A maioria dos cmdlets retorno objetos que podem ser manipulados e, em seguida, composto como texto para exibição.</span><span class="sxs-lookup"><span data-stu-id="c96b2-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="c96b2-122">Para compreender totalmente a saída de um cmdlet, encaminhar a saída para o `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c96b2-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="c96b2-123">Por exemplo, o comando seguinte apresenta informações sobre os membros da saída de objeto pelo `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c96b2-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="c96b2-124">Consistência</span><span class="sxs-lookup"><span data-stu-id="c96b2-124">Consistency</span></span>

<span data-ttu-id="c96b2-125">Gerenciamento de sistemas pode ser uma tarefa complexa.</span><span class="sxs-lookup"><span data-stu-id="c96b2-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="c96b2-126">Ferramentas que têm uma interface consistente que ajudam a controlar a complexidade inerente.</span><span class="sxs-lookup"><span data-stu-id="c96b2-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="c96b2-127">Infelizmente, as ferramentas da linha de comandos e objetos de COM programável por scripts não são conhecidos por sua consistência.</span><span class="sxs-lookup"><span data-stu-id="c96b2-127">Unfortunately, command-line tools and scriptable COM objects aren't known for their consistency.</span></span>

<span data-ttu-id="c96b2-128">A consistência do PowerShell é um de seus ativos primários.</span><span class="sxs-lookup"><span data-stu-id="c96b2-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="c96b2-129">Por exemplo, se aprender a utilizar o `Sort-Object` cmdlet, pode usar esse conhecimento para ordenar a saída de qualquer cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c96b2-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="c96b2-130">Não precisa de saber as rotinas de classificação diferentes de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c96b2-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="c96b2-131">Além disso, os desenvolvedores de cmdlet não precisam de recursos de classificação para os seus cmdlets de design.</span><span class="sxs-lookup"><span data-stu-id="c96b2-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="c96b2-132">PowerShell fornece uma estrutura com as funcionalidades básicas que força a consistência.</span><span class="sxs-lookup"><span data-stu-id="c96b2-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="c96b2-133">O framework elimina algumas opções que restam para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="c96b2-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="c96b2-134">Mas, em troca, torna o desenvolvimento dos cmdlets muito mais simples.</span><span class="sxs-lookup"><span data-stu-id="c96b2-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="c96b2-135">Ambientes de criação de scripts e interativos</span><span class="sxs-lookup"><span data-stu-id="c96b2-135">Interactive and scripting environments</span></span>

<span data-ttu-id="c96b2-136">Linha de comandos do Windows fornece um shell interativo com o acesso a ferramentas de linha de comandos e scripts básica.</span><span class="sxs-lookup"><span data-stu-id="c96b2-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="c96b2-137">Windows Script Host (WSH) tem ferramentas de linha de comando programável por scripts e objetos de automação COM, mas não fornece um shell interativo.</span><span class="sxs-lookup"><span data-stu-id="c96b2-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="c96b2-138">PowerShell combina um shell interativo e um ambiente de script.</span><span class="sxs-lookup"><span data-stu-id="c96b2-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="c96b2-139">PowerShell pode acessar as ferramentas da linha de comandos, objetos COM e bibliotecas de classes do .NET.</span><span class="sxs-lookup"><span data-stu-id="c96b2-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="c96b2-140">Esta combinação de funcionalidades estende os recursos do usuário interativo, o escritor de script e o administrador de sistema.</span><span class="sxs-lookup"><span data-stu-id="c96b2-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="c96b2-141">Orientação a objeto</span><span class="sxs-lookup"><span data-stu-id="c96b2-141">Object orientation</span></span>

<span data-ttu-id="c96b2-142">PowerShell baseia-se no objeto não texto.</span><span class="sxs-lookup"><span data-stu-id="c96b2-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="c96b2-143">A saída de um comando é um objeto.</span><span class="sxs-lookup"><span data-stu-id="c96b2-143">The output of a command is an object.</span></span> <span data-ttu-id="c96b2-144">Pode enviar o objeto de saída, através do pipeline para outro comando como entrada.</span><span class="sxs-lookup"><span data-stu-id="c96b2-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="c96b2-145">Este pipeline fornece uma interface familiar para as pessoas experientes com outros shells.</span><span class="sxs-lookup"><span data-stu-id="c96b2-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="c96b2-146">PowerShell expande este conceito ao enviar objetos em vez de texto.</span><span class="sxs-lookup"><span data-stu-id="c96b2-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="c96b2-147">Transição fácil para a criação de scripts</span><span class="sxs-lookup"><span data-stu-id="c96b2-147">Easy transition to scripting</span></span>

<span data-ttu-id="c96b2-148">Facilita de capacidade de deteção de comando do PowerShell facilita a transição de digitar comandos interativamente a criação e execução de scripts.</span><span class="sxs-lookup"><span data-stu-id="c96b2-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="c96b2-149">Transcrições de PowerShell e o histórico facilitam a copiar os comandos para um ficheiro para utilização como um script.</span><span class="sxs-lookup"><span data-stu-id="c96b2-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
