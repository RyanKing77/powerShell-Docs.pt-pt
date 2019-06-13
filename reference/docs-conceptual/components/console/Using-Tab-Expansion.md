---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar a Expansão por Tabulação
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031021"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="cc9fa-103">Utilizar a Expansão por Tabulação</span><span class="sxs-lookup"><span data-stu-id="cc9fa-103">Using Tab Expansion</span></span>

<span data-ttu-id="cc9fa-104">Shells de linha de comandos, muitas vezes, proporcionam uma forma para concluir os nomes de ficheiros de longos ou comandos automaticamente, acelerar a entrada de comando e o fornecimento de sugestões.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="cc9fa-105">PowerShell permite-lhe o preenchimento nos nomes de ficheiros e nomes de cmdlet ao premir o <kbd>separador</kbd> chave.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-105">PowerShell allows you to fill in file names and cmdlet names by pressing the <kbd>Tab</kbd> key.</span></span>

> [!NOTE]
> <span data-ttu-id="cc9fa-106">Expansão da tabulação é controlado pela função interna TabExpansion ou TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="cc9fa-107">Uma vez que esta função pode ser modificada ou substituída, essa discussão é um guia para o comportamento da configuração predefinida do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="cc9fa-108">Para preencher automaticamente um nome de ficheiro ou caminho as opções disponíveis, escreva parte do nome e prima a <kbd>separador</kbd> chave.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-108">To fill in a filename or path from the available choices automatically, type part of the name and press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="cc9fa-109">PowerShell expandirá automaticamente o nome para a primeira correspondência que encontra.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="cc9fa-110">Premir a <kbd>separador</kbd> chave repetidamente passará por todas as opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-110">Pressing the <kbd>Tab</kbd> key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="cc9fa-111">A expansão da tabulação de nomes de cmdlet é ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="cc9fa-112">Para utilizar a expansão da tabulação no nome de um cmdlet, escreva a primeira parte inteira do nome (o verbo) e o hífen que o sucede.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="cc9fa-113">Pode preencher mais o nome de uma correspondência parcial.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="cc9fa-114">Por exemplo, se digitar `get-co` e, em seguida, prima a <kbd>separador</kbd> chave, PowerShell irá automaticamente expandir esta opção para o `Get-Command` cmdlet (Observe que ele também altera o caso de letras para o formato padrão).</span><span class="sxs-lookup"><span data-stu-id="cc9fa-114">For example, if you type `get-co` and then press the <kbd>Tab</kbd> key, PowerShell will automatically expand this to the `Get-Command` cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="cc9fa-115">Se pressionar <kbd>separador</kbd> chave novamente, PowerShell substitui isso com o apenas outro cmdlet nome correspondente, `Get-Content`.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-115">If you press <kbd>Tab</kbd> key again, PowerShell replaces this with the only other matching cmdlet name, `Get-Content`.</span></span>

<span data-ttu-id="cc9fa-116">Pode usar repetidamente expansão da tabulação na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="cc9fa-117">Por exemplo, pode utilizar a expansão da tabulação no nome do `Get-Content` cmdlet ao introduzir:</span><span class="sxs-lookup"><span data-stu-id="cc9fa-117">For example, you can use tab expansion on the name of the `Get-Content` cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="cc9fa-118">Quando pressiona o <kbd>separador</kbd> chave, o comando se expande para:</span><span class="sxs-lookup"><span data-stu-id="cc9fa-118">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="cc9fa-119">Pode, em seguida, parcialmente especifique o caminho para o ficheiro de registo de configuração do Active Directory e utilizar a expansão da tabulação novamente:</span><span class="sxs-lookup"><span data-stu-id="cc9fa-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="cc9fa-120">Quando pressiona o <kbd>separador</kbd> chave, o comando se expande para:</span><span class="sxs-lookup"><span data-stu-id="cc9fa-120">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="cc9fa-121">Uma limitação do processo de expansão do separador é que os separadores sempre são interpretados como tentativas para concluir uma palavra.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="cc9fa-122">Se copiar e colar exemplos de comandos para a consola do PowerShell, certifique-se de que o exemplo não contém separadores; Se existir, os resultados imprevisíveis e certamente não será o que pretendia.</span><span class="sxs-lookup"><span data-stu-id="cc9fa-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>
