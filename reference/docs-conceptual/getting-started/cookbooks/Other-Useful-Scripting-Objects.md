---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Outros Objetos de Scripting Úteis
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 0e87e9919199e011ab5abec5b07dccc8494ad64a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949830"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="180f0-103">Outros Objetos de Scripting Úteis</span><span class="sxs-lookup"><span data-stu-id="180f0-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="180f0-104">Os seguintes objetos fornecem funcionalidades adicionais de script no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="180f0-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="180f0-105">Não são parte do **$psISE** hierarquia.</span><span class="sxs-lookup"><span data-stu-id="180f0-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="180f0-106">Objetos de script útil</span><span class="sxs-lookup"><span data-stu-id="180f0-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="180f0-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="180f0-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="180f0-108">Existem algumas limitações na forma como o ISE do Windows PowerShell interage com aplicações de consola.</span><span class="sxs-lookup"><span data-stu-id="180f0-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="180f0-109">Um comando ou um script de automatização requer intervenção do utilizador poderá não funcionar da forma que funciona a partir da consola do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="180f0-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="180f0-110">Pode querer bloquear estes comandos ou scripts sejam executadas no painel de comando do Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="180f0-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="180f0-111">O **$psUnsupportedConsoleApplications** objeto mantém uma lista desses comandos.</span><span class="sxs-lookup"><span data-stu-id="180f0-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="180f0-112">Se tentar executar os comandos nesta lista, receberá uma mensagem que não são suportados.</span><span class="sxs-lookup"><span data-stu-id="180f0-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="180f0-113">O seguinte script adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="180f0-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="180f0-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="180f0-114">$psLocalHelp</span></span>

<span data-ttu-id="180f0-115">Este é um objeto de dicionário que mantém um mapeamento sensíveis ao contexto de entre tópicos de ajuda e as respetivas ligações associadas no ficheiro de ajuda de HTML compilado local.</span><span class="sxs-lookup"><span data-stu-id="180f0-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="180f0-116">É utilizado para localizar a local a ajuda para um tópico específico.</span><span class="sxs-lookup"><span data-stu-id="180f0-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="180f0-117">Pode adicionar ou eliminar tópicos desta lista.</span><span class="sxs-lookup"><span data-stu-id="180f0-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="180f0-118">Exemplo de código seguinte mostra alguns exemplos de pares chave-valor que estão contidas num **$psLocalHelp**.</span><span class="sxs-lookup"><span data-stu-id="180f0-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="sample-output"></a><span data-ttu-id="180f0-119">Saída de Exemplo</span><span class="sxs-lookup"><span data-stu-id="180f0-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="180f0-120">Chave: Adicionar-computador</span><span class="sxs-lookup"><span data-stu-id="180f0-120">Key : Add-Computer</span></span>|<span data-ttu-id="180f0-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="180f0-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="180f0-122">Chave: Adicionar conteúdo</span><span class="sxs-lookup"><span data-stu-id="180f0-122">Key : Add-Content</span></span>|<span data-ttu-id="180f0-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="180f0-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

<span data-ttu-id="180f0-124">O seguinte script adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="180f0-124">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="180f0-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="180f0-125">$psOnlineHelp</span></span>

<span data-ttu-id="180f0-126">Este é um objeto de dicionário que mantém um mapeamento sensíveis ao contexto entre os títulos de tópico de tópicos de ajuda e os URLs externos associados.</span><span class="sxs-lookup"><span data-stu-id="180f0-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="180f0-127">É utilizado para localizar a ajuda para um tópico específico na web.</span><span class="sxs-lookup"><span data-stu-id="180f0-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="180f0-128">Pode adicionar ou eliminar tópicos desta lista.</span><span class="sxs-lookup"><span data-stu-id="180f0-128">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

### <a name="sample-output"></a><span data-ttu-id="180f0-129">Saída de Exemplo</span><span class="sxs-lookup"><span data-stu-id="180f0-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="180f0-130">Chave: Adicionar-computador</span><span class="sxs-lookup"><span data-stu-id="180f0-130">Key : Add-Computer</span></span>|<span data-ttu-id="180f0-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="180f0-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="180f0-132">Chave: Adicionar conteúdo</span><span class="sxs-lookup"><span data-stu-id="180f0-132">Key : Add-Content</span></span>|<span data-ttu-id="180f0-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="180f0-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="180f0-134">O seguinte script adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="180f0-134">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="180f0-135">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="180f0-135">See Also</span></span>

- [<span data-ttu-id="180f0-136">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="180f0-136">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)