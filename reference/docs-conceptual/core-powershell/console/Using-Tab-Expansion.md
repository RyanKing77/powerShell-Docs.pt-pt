---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar a Expansão por Tabulação
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 3d047bf0691c8a304d7637aa50fba6ae99709a82
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949235"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="24502-103">Utilizar a Expansão por Tabulação</span><span class="sxs-lookup"><span data-stu-id="24502-103">Using Tab Expansion</span></span>

<span data-ttu-id="24502-104">Shells da linha de comandos, muitas vezes, fornecem uma forma para concluir automaticamente, os nomes dos ficheiros de longos ou comandos acelerar a entrada de comando e fornecer.</span><span class="sxs-lookup"><span data-stu-id="24502-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing .</span></span> <span data-ttu-id="24502-105">Windows PowerShell permite-lhe preencher os nomes de ficheiros e nomes de cmdlet, premindo o **separador** chave.</span><span class="sxs-lookup"><span data-stu-id="24502-105">Windows PowerShell allows you to fill in file names and cmdlet names by pressing the **Tab** key.</span></span>

> [!NOTE]
> <span data-ttu-id="24502-106">Separador expansão é controlada pela função interna TabExpansion ou TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="24502-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="24502-107">Uma vez que esta função pode ser modificada ou substituí-lo, este debate é um guia para o comportamento da configuração predefinida do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24502-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="24502-108">Para preencher automaticamente um nome de ficheiro ou caminho as escolhas disponíveis, escreva parte do nome e prima a **separador** chave.</span><span class="sxs-lookup"><span data-stu-id="24502-108">To fill in a filename or path from the available choices automatically, type part of the name and press the **Tab** key.</span></span> <span data-ttu-id="24502-109">PowerShell irá expandir automaticamente o nome para a correspondência primeiro que encontra.</span><span class="sxs-lookup"><span data-stu-id="24502-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="24502-110">Premir o **separador** chave repetidamente irá percorrer todas as escolhas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="24502-110">Pressing the **Tab** key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="24502-111">A expansão de separador de nomes de cmdlet é ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="24502-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="24502-112">Para utilizar a expansão de separador no nome do cmdlet, escreva a parte do primeiro toda o nome de (o verbo) e o hífen seguinte.</span><span class="sxs-lookup"><span data-stu-id="24502-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="24502-113">Pode preencher mais o nome de uma correspondência parcial.</span><span class="sxs-lookup"><span data-stu-id="24502-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="24502-114">Por exemplo, se escrever **get-co** e, em seguida, prima a **separador** chave, PowerShell será automaticamente expandido para o **Get-Command** cmdlet (tenha em atenção que também altera as maiúsculas e minúsculas de letras ao respetivo formulário standard).</span><span class="sxs-lookup"><span data-stu-id="24502-114">For example, if you type **get-co** and then press the **Tab** key, PowerShell will automatically expand this to the **Get-Command** cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="24502-115">Se premir **separador** chave novamente, PowerShell substitui isto com o apenas outro cmdlet nome correspondente, **Get-Content**.</span><span class="sxs-lookup"><span data-stu-id="24502-115">If you press **Tab** key again, PowerShell replaces this with the only other matching cmdlet name, **Get-Content**.</span></span>

<span data-ttu-id="24502-116">Pode utilizar a expansão de separador repetidamente na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="24502-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="24502-117">Por exemplo, pode utilizar a expansão de separador no nome do **Get-Content** cmdlet introduzindo:</span><span class="sxs-lookup"><span data-stu-id="24502-117">For example, you can use tab expansion on the name of the **Get-Content** cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="24502-118">Quando prime o **separador** chave, o comando expande para:</span><span class="sxs-lookup"><span data-stu-id="24502-118">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="24502-119">Pode, em seguida, parcialmente especifique o caminho para o ficheiro de registo de configuração do Active Directory e utilizar a expansão de separador novamente:</span><span class="sxs-lookup"><span data-stu-id="24502-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="24502-120">Quando prime o **separador** chave, o comando expande para:</span><span class="sxs-lookup"><span data-stu-id="24502-120">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="24502-121">Uma limitação do processo de expansão de separador é que os separadores são sempre interpretados como tentativas para concluir uma palavra.</span><span class="sxs-lookup"><span data-stu-id="24502-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="24502-122">Se copiar e colar exemplos de comando para uma consola do PowerShell, certifique-se de que o exemplo contém separadores; Se tiver, os resultados imprevisíveis e quase certamente não serão os esperados.</span><span class="sxs-lookup"><span data-stu-id="24502-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>