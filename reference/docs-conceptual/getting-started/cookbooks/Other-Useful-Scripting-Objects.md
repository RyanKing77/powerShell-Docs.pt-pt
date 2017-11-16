---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Outros objetos de Scripting útil"
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="10af3-103">Outros objetos de Scripting útil</span><span class="sxs-lookup"><span data-stu-id="10af3-103">Other Useful Scripting Objects</span></span>
  <span data-ttu-id="10af3-104">Os seguintes objetos fornecem funcionalidades adicionais de script no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10af3-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="10af3-105">Não são parte do **$psISE** hierarquia.</span><span class="sxs-lookup"><span data-stu-id="10af3-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="10af3-106">Objetos de script útil</span><span class="sxs-lookup"><span data-stu-id="10af3-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="10af3-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="10af3-107">$psUnsupportedConsoleApplications</span></span>
 <span data-ttu-id="10af3-108">Existem algumas limitações na forma como o ISE do Windows PowerShell interage com aplicações de consola.</span><span class="sxs-lookup"><span data-stu-id="10af3-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="10af3-109">Um comando ou um script de automatização requer intervenção do utilizador poderá não funcionar da forma que funciona a partir da consola do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10af3-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="10af3-110">Pode querer bloquear estes comandos ou scripts sejam executadas no painel de comando do Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="10af3-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="10af3-111">O **$psUnsupportedConsoleApplications** objeto mantém uma lista desses comandos.</span><span class="sxs-lookup"><span data-stu-id="10af3-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="10af3-112">Se tentar executar os comandos nesta lista, receberá uma mensagem que não são suportados.</span><span class="sxs-lookup"><span data-stu-id="10af3-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="10af3-113">O seguinte script adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="10af3-113">The following script adds an entry to the list.</span></span>

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a><span data-ttu-id="10af3-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="10af3-114">$psLocalHelp</span></span>
 <span data-ttu-id="10af3-115">Este é um objeto de dicionário que mantém um mapeamento sensíveis ao contexto de entre tópicos de ajuda e as respetivas ligações associadas no ficheiro de ajuda de HTML compilado local.</span><span class="sxs-lookup"><span data-stu-id="10af3-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="10af3-116">É utilizado para localizar a local a ajuda para um tópico específico.</span><span class="sxs-lookup"><span data-stu-id="10af3-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="10af3-117">Pode adicionar ou eliminar tópicos desta lista.</span><span class="sxs-lookup"><span data-stu-id="10af3-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="10af3-118">Exemplo de código seguinte mostra alguns exemplos de pares chave-valor que estão contidas num **$psLocalHelp**.</span><span class="sxs-lookup"><span data-stu-id="10af3-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="10af3-119">Saída de Exemplo</span><span class="sxs-lookup"><span data-stu-id="10af3-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="10af3-120">Chave: Adicionar-computador</span><span class="sxs-lookup"><span data-stu-id="10af3-120">Key : Add-Computer</span></span>|<span data-ttu-id="10af3-121">Valor: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="10af3-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="10af3-122">Chave: Adicionar conteúdo</span><span class="sxs-lookup"><span data-stu-id="10af3-122">Key : Add-Content</span></span>|<span data-ttu-id="10af3-123">Valor: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="10af3-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

 <span data-ttu-id="10af3-124">O seguinte script adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="10af3-124">The following script adds an entry to the list.</span></span>

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="10af3-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="10af3-125">$psOnlineHelp</span></span>
 <span data-ttu-id="10af3-126">Este é um objeto de dicionário que mantém um mapeamento sensíveis ao contexto entre os títulos de tópico de tópicos de ajuda e os URLs externos associados.</span><span class="sxs-lookup"><span data-stu-id="10af3-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="10af3-127">É utilizado para localizar a ajuda para um tópico específico na web.</span><span class="sxs-lookup"><span data-stu-id="10af3-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="10af3-128">Pode adicionar ou eliminar tópicos desta lista.</span><span class="sxs-lookup"><span data-stu-id="10af3-128">You can add or delete topics from this list.</span></span>

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="10af3-129">Saída de Exemplo</span><span class="sxs-lookup"><span data-stu-id="10af3-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="10af3-130">Chave: Adicionar-computador</span><span class="sxs-lookup"><span data-stu-id="10af3-130">Key : Add-Computer</span></span>|<span data-ttu-id="10af3-131">Valor: http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="10af3-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="10af3-132">Chave: Adicionar conteúdo</span><span class="sxs-lookup"><span data-stu-id="10af3-132">Key : Add-Content</span></span>|<span data-ttu-id="10af3-133">Valor: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="10af3-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="10af3-134">O seguinte script adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="10af3-134">The following script adds an entry to the list.</span></span>

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="10af3-135">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="10af3-135">See Also</span></span>
- [<span data-ttu-id="10af3-136">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="10af3-136">The Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
