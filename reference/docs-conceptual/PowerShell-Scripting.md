---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Script do PowerShell
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094056"
---
# <a name="powershell"></a><span data-ttu-id="23952-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="23952-103">PowerShell</span></span>

<span data-ttu-id="23952-104">Baseado no .NET Framework, o PowerShell é um shell de linha de comandos baseada em tarefas e linguagem de script; foi concebido especificamente para os administradores de sistemas e usuários avançados, rapidamente a automatizar a administração de vários sistemas operacionais (Linux, macOS, Unix e Windows) e os processos relacionados com os aplicativos executados nesses sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="23952-104">Built on the .NET Framework, PowerShell is a task-based command-line shell and scripting language; it is designed specifically for system administrators and power-users, to rapidly automate the administration of multiple operating systems (Linux, macOS, Unix, and Windows) and the processes related to the applications that run on those operating systems.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="23952-105">O PowerShell é o código-fonte aberto</span><span class="sxs-lookup"><span data-stu-id="23952-105">PowerShell is open source</span></span>

<span data-ttu-id="23952-106">Código-fonte base do PowerShell está agora disponível no GitHub e aberta a contribuições da Comunidade.</span><span class="sxs-lookup"><span data-stu-id="23952-106">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="23952-107">Ver [PowerShell fonte no GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="23952-107">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="23952-108">Pode começar com os bits que necessita em [PowerShell obter](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="23952-108">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="23952-109">Ou, talvez, com um tour rápido, [introdução](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span><span class="sxs-lookup"><span data-stu-id="23952-109">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="23952-110">Metas de design do PowerShell</span><span class="sxs-lookup"><span data-stu-id="23952-110">PowerShell design goals</span></span>
<span data-ttu-id="23952-111">PowerShell foi projetado para melhorar o ambiente de criação de scripts e linha de comandos, eliminando consideravelmente os problemas de longa data e a acrescentar novas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="23952-111">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="23952-112">Capacidade de deteção</span><span class="sxs-lookup"><span data-stu-id="23952-112">Discoverability</span></span>
<span data-ttu-id="23952-113">PowerShell torna mais fácil detetar os seus recursos.</span><span class="sxs-lookup"><span data-stu-id="23952-113">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="23952-114">Por exemplo, para encontrar uma lista de cmdlets que ver e alterar os serviços do Windows, escreva:</span><span class="sxs-lookup"><span data-stu-id="23952-114">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="23952-115">Depois de descobrir qual cmdlet realiza uma tarefa, pode saber mais sobre o cmdlet, utilizando o `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23952-115">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span>
<span data-ttu-id="23952-116">Por exemplo, para apresentar a ajuda sobre o `Get-Service` cmdlet, tipo:</span><span class="sxs-lookup"><span data-stu-id="23952-116">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```
<span data-ttu-id="23952-117">A maioria dos cmdlets emitir objetos que podem ser manipulados e, em seguida, processados em texto para exibição.</span><span class="sxs-lookup"><span data-stu-id="23952-117">Most cmdlets emit objects which can be manipulated and then rendered into text for display.</span></span>
<span data-ttu-id="23952-118">Para compreender totalmente o resultado desse cmdlet, encaminhar o resultado para o `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23952-118">To fully understand the output of that cmdlet, pipe its output to the `Get-Member` cmdlet.</span></span>
<span data-ttu-id="23952-119">Por exemplo, o comando seguinte apresenta informações sobre os membros da saída de objeto pelo `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23952-119">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="23952-120">Consistência</span><span class="sxs-lookup"><span data-stu-id="23952-120">Consistency</span></span>
<span data-ttu-id="23952-121">Gerenciamento de sistemas pode ser um empreendimento complexo e ferramentas que têm uma interface consistente ajudam a controlar a complexidade inerente.</span><span class="sxs-lookup"><span data-stu-id="23952-121">Managing systems can be a complex endeavor and tools that have a consistent interface help to control the inherent complexity.</span></span>
<span data-ttu-id="23952-122">Infelizmente, nem ferramentas da linha de comandos como objetos de COM programável por scripts já são conhecidos sua consistência.</span><span class="sxs-lookup"><span data-stu-id="23952-122">Unfortunately, neither command-line tools nor scriptable COM objects have been known for their consistency.</span></span>

<span data-ttu-id="23952-123">A consistência do PowerShell é um de seus ativos primários.</span><span class="sxs-lookup"><span data-stu-id="23952-123">The consistency of PowerShell is one of its primary assets.</span></span>
<span data-ttu-id="23952-124">Por exemplo, se aprender a utilizar o `Sort-Object` cmdlet, pode usar esse conhecimento para ordenar a saída de qualquer cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23952-124">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span>
<span data-ttu-id="23952-125">Não é necessário que saber as rotinas de classificação diferentes de cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23952-125">You do not have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="23952-126">Além disso, os desenvolvedores de cmdlet não tem a criação de funcionalidades de classificação para os seus cmdlets.</span><span class="sxs-lookup"><span data-stu-id="23952-126">In addition, cmdlet developers do not have to design sorting features for their cmdlets.</span></span>
<span data-ttu-id="23952-127">PowerShell dá a eles uma estrutura que fornece as funcionalidades básicas e força-os para ser consistente sobre muitos aspectos da interface.</span><span class="sxs-lookup"><span data-stu-id="23952-127">PowerShell gives them a framework that provides the basic features and forces them to be consistent about many aspects of the interface.</span></span>
<span data-ttu-id="23952-128">O framework elimina algumas das opções que são normalmente deixadas para o desenvolvedor, mas, em troca, torna o desenvolvimento dos cmdlets robustos e fácil de usar muito mais simples.</span><span class="sxs-lookup"><span data-stu-id="23952-128">The framework eliminates some of the choices that are typically left to the developer, but, in return, it makes the development of robust and easy-to-use cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="23952-129">Ambientes de criação de scripts e interativos</span><span class="sxs-lookup"><span data-stu-id="23952-129">Interactive and Scripting Environments</span></span>
<span data-ttu-id="23952-130">PowerShell é um ambiente de criação de scripts e interativo combinado que lhe dá acesso a ferramentas de linha de comandos e objetos COM e também permite-lhe utilizar o poder do .NET Framework Class Library (FCL).</span><span class="sxs-lookup"><span data-stu-id="23952-130">PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL).</span></span>

<span data-ttu-id="23952-131">Neste ambiente melhora após o Windows linha de comandos, que fornece um ambiente interativo com várias ferramentas de linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="23952-131">This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools.</span></span>
<span data-ttu-id="23952-132">Ele também oferecer melhorias em scripts do Windows Script Host (WSH), que lhe permite utilizar várias ferramentas de linha de comandos e objetos de automação COM, mas não fornecem um ambiente interativo.</span><span class="sxs-lookup"><span data-stu-id="23952-132">It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.</span></span>

<span data-ttu-id="23952-133">Ao combinar o acesso a todos esses recursos, o PowerShell amplia a capacidade do usuário interativo e do escritor de script e torna a administração de sistema mais gerenciáveis.</span><span class="sxs-lookup"><span data-stu-id="23952-133">By combining access to all of these features, PowerShell extends the ability of the interactive user and the script writer, and makes system administration more manageable.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="23952-134">Orientação a objeto</span><span class="sxs-lookup"><span data-stu-id="23952-134">Object Orientation</span></span>
<span data-ttu-id="23952-135">Embora interage com o PowerShell, digitando comandos em texto, o PowerShell se baseia em objetos, e não texto.</span><span class="sxs-lookup"><span data-stu-id="23952-135">Although you interact with PowerShell by typing commands in text, PowerShell is based on objects, not text.</span></span>
<span data-ttu-id="23952-136">A saída de um comando é um objeto.</span><span class="sxs-lookup"><span data-stu-id="23952-136">The output of a command is an object.</span></span>
<span data-ttu-id="23952-137">Pode enviar o objeto de saída para outro comando como entrada.</span><span class="sxs-lookup"><span data-stu-id="23952-137">You can send the output object to another command as its input.</span></span>
<span data-ttu-id="23952-138">Como resultado, o PowerShell fornece uma interface familiar para pessoas experimentadas em outros shells, ao mesmo tempo apresentando um paradigma de linha de comandos novo e poderoso.</span><span class="sxs-lookup"><span data-stu-id="23952-138">As a result, PowerShell provides a familiar interface to people experienced with other shells, while introducing a new and powerful command-line paradigm.</span></span>
<span data-ttu-id="23952-139">Ele estende o conceito de envio de dados entre comandos, permitindo-lhe para enviar a objetos, em vez de texto.</span><span class="sxs-lookup"><span data-stu-id="23952-139">It extends the concept of sending data between commands by enabling you to send objects, rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="23952-140">Transição fácil para a criação de scripts</span><span class="sxs-lookup"><span data-stu-id="23952-140">Easy Transition to Scripting</span></span>
<span data-ttu-id="23952-141">PowerShell facilita facilita a transição de digitar comandos interativamente a criação e execução de scripts.</span><span class="sxs-lookup"><span data-stu-id="23952-141">PowerShell makes it easy to transition from typing commands interactively to creating and running scripts.</span></span>
<span data-ttu-id="23952-142">Pode escrever os comandos na linha de comando do PowerShell para descobrir os comandos que executam uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="23952-142">You can type commands at the PowerShell command prompt to discover the commands that perform a task.</span></span>
<span data-ttu-id="23952-143">Em seguida, pode salvar esses comandos numa transcrição ou um histórico antes de copiá-los para um ficheiro para utilização como um script.</span><span class="sxs-lookup"><span data-stu-id="23952-143">Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.</span></span>
