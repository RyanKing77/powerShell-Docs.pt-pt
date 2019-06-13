---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Outros Objetos de Scripting Úteis
ms.openlocfilehash: 8d1d10b518d1aadd6aec831b512802558f8fc075
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030041"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="41618-103">Outros Objetos de Scripting Úteis</span><span class="sxs-lookup"><span data-stu-id="41618-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="41618-104">Os objetos seguintes fornecem funcionalidades adicionais de scripts no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41618-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="41618-105">Não são parte dos **$psISE** hierarquia.</span><span class="sxs-lookup"><span data-stu-id="41618-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="41618-106">Objetos de Scripting úteis</span><span class="sxs-lookup"><span data-stu-id="41618-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="41618-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="41618-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="41618-108">Existem algumas limitações em como o Windows PowerShell ISE interage com aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="41618-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="41618-109">Um comando ou um script de automatização que requer intervenção do usuário poderá não funcionar da forma funciona a partir da consola do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41618-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="41618-110">Pode querer bloquear estes comandos ou scripts a partir de em execução no painel de comando do Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="41618-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="41618-111">O **$psUnsupportedConsoleApplications** objeto mantém uma lista desses comandos.</span><span class="sxs-lookup"><span data-stu-id="41618-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="41618-112">Se tentar executar os comandos nesta lista, receberá uma mensagem que não são suportados.</span><span class="sxs-lookup"><span data-stu-id="41618-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="41618-113">O script a seguir adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="41618-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="41618-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="41618-114">$psLocalHelp</span></span>

<span data-ttu-id="41618-115">Este é um objeto de dicionário que mantém um mapeamento sensível ao contexto entre tópicos de ajuda e seus links associado no ficheiro de ajuda HTML compilado local.</span><span class="sxs-lookup"><span data-stu-id="41618-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="41618-116">É utilizado para localizar a ajuda local para um tópico específico.</span><span class="sxs-lookup"><span data-stu-id="41618-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="41618-117">Pode adicionar ou eliminar tópicos desta lista.</span><span class="sxs-lookup"><span data-stu-id="41618-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="41618-118">O exemplo de código seguinte mostra alguns exemplos pares chave-valor que estão contidas na `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="41618-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="41618-119">O script a seguir adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="41618-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="41618-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="41618-120">$psOnlineHelp</span></span>

<span data-ttu-id="41618-121">Este é um objeto de dicionário que mantém um mapeamento sensível ao contexto entre os títulos de tópico de tópicos de ajuda e suas URLs externos associados.</span><span class="sxs-lookup"><span data-stu-id="41618-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="41618-122">É utilizado para localizar a ajuda para um determinado tópico na web.</span><span class="sxs-lookup"><span data-stu-id="41618-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="41618-123">Pode adicionar ou eliminar tópicos desta lista.</span><span class="sxs-lookup"><span data-stu-id="41618-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="41618-124">O script a seguir adiciona uma entrada à lista.</span><span class="sxs-lookup"><span data-stu-id="41618-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="41618-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="41618-125">See Also</span></span>

[<span data-ttu-id="41618-126">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="41618-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
