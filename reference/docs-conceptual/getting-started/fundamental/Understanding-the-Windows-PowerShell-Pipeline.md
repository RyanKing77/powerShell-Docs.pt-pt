---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Noções sobre o Pipeline do Windows PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: c3f1d17432cf3a77c0f5ecae137a4233a28a19d7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="understanding-the-windows-powershell-pipeline"></a><span data-ttu-id="0c56a-103">Noções sobre o Pipeline do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c56a-103">Understanding the Windows PowerShell Pipeline</span></span>
<span data-ttu-id="0c56a-104">Piping em praticamente qualquer lugar funciona no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c56a-104">Piping works virtually everywhere in Windows PowerShell.</span></span> <span data-ttu-id="0c56a-105">Apesar de ver o texto no ecrã, o Windows PowerShell pipe não texto entre comandos.</span><span class="sxs-lookup"><span data-stu-id="0c56a-105">Although you see text on the screen, Windows PowerShell does not pipe text between commands.</span></span> <span data-ttu-id="0c56a-106">Em vez disso, este encaminha objetos.</span><span class="sxs-lookup"><span data-stu-id="0c56a-106">Instead, it pipes objects.</span></span>

<span data-ttu-id="0c56a-107">A notação utilizada para pipelines é semelhante à utilizada na outros shells, por isso, à primeira vista, pode não ser aparente que do Windows PowerShell apresenta um novo.</span><span class="sxs-lookup"><span data-stu-id="0c56a-107">The notation used for pipelines is similar to that used in other shells, so at first glance, it may not be apparent that Windows PowerShell introduces something new.</span></span> <span data-ttu-id="0c56a-108">Por exemplo, se utilizar o **out-anfitrião** cmdlet para forçar uma apresentação da página pela página de saída do comando de outro, a procura de saída apenas como o texto normal apresentado no ecrã, dividido dos páginas:</span><span class="sxs-lookup"><span data-stu-id="0c56a-108">For example, if you use the **Out-Host** cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="0c56a-109">O Out-Host-comando de paginação é um elemento de pipeline útil sempre que ter demorado resultado que pretende apresentar lentamente.</span><span class="sxs-lookup"><span data-stu-id="0c56a-109">The Out-Host -Paging command is a useful pipeline element whenever you have lengthy output that you would like to display slowly.</span></span> <span data-ttu-id="0c56a-110">É especialmente útil se a operação é muito intensivas em CPU.</span><span class="sxs-lookup"><span data-stu-id="0c56a-110">It is especially useful if the operation is very CPU-intensive.</span></span> <span data-ttu-id="0c56a-111">Porque o processamento é transferido para o Out-anfitrião cmdlet quando tem uma página concluída, pronta para apresentar, os cmdlets que precedê-lo no pipeline de parar a operação até a página seguinte do resultado está disponível.</span><span class="sxs-lookup"><span data-stu-id="0c56a-111">Because processing is transferred to the Out-Host cmdlet when it has a complete page ready to display, cmdlets that precede it in the pipeline halt operation until the next page of output is available.</span></span> <span data-ttu-id="0c56a-112">Pode ver esta se utilizar o Gestor de tarefas do Windows para monitorizar a utilização da CPU e memória do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c56a-112">You can see this if you use the Windows Task Manager to monitor CPU and memory use by Windows PowerShell.</span></span>

<span data-ttu-id="0c56a-113">Execute o seguinte comando: **Get-ChildItem c\\Windows-Recurse**.</span><span class="sxs-lookup"><span data-stu-id="0c56a-113">Run the following command: **Get-ChildItem C:\\Windows -Recurse**.</span></span> <span data-ttu-id="0c56a-114">Comparar a utilização da CPU e memória a este comando: **Get-ChildItem c\\Windows-Recurse | Out-alojar-paginação**.</span><span class="sxs-lookup"><span data-stu-id="0c56a-114">Compare the CPU and memory usage to this command: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span></span> <span data-ttu-id="0c56a-115">O que vê no ecrã é o texto, mas isto acontece porque é necessário representar objetos como texto numa janela de consola.</span><span class="sxs-lookup"><span data-stu-id="0c56a-115">What you see on the screen is text, but that is because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="0c56a-116">Isto é apenas uma representação que é realmente a acontecer no interior do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c56a-116">This is just a representation of what is really going on inside Windows PowerShell.</span></span> <span data-ttu-id="0c56a-117">Por exemplo, considere o cmdlet Get-localização.</span><span class="sxs-lookup"><span data-stu-id="0c56a-117">For example, consider the Get-Location cmdlet.</span></span> <span data-ttu-id="0c56a-118">Se escrever **Get-Location** enquanto a sua localização atual é a raiz da unidade C, verá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="0c56a-118">If you type **Get-Location** while your current location is the root of the C drive, you would see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="0c56a-119">Se o Windows PowerShell encaminhados texto, emitir um comando, tal como **Get-Location | Out-anfitrião**, seria passam do **Get-Location** para **out-anfitrião** um conjunto de carateres na ordem são apresentadas onscreen.</span><span class="sxs-lookup"><span data-stu-id="0c56a-119">If Windows PowerShell pipelined text, issuing a command such as **Get-Location | Out-Host**, would pass from **Get-Location** to **Out-Host** a set of characters in the order they are displayed onscreen.</span></span> <span data-ttu-id="0c56a-120">Por outras palavras, se pretendesse ignorar as informações de cabeçalho, **out-anfitrião** receberia primeiro o caráter '**C'**, em seguida, o caráter '**:'**, em seguida, o caráter ' **\\'**.</span><span class="sxs-lookup"><span data-stu-id="0c56a-120">In other words, if you were to ignore the heading information, **Out-Host** would first receive the character '**C'**, then the character '**:'**, then the character '**\\'**.</span></span> <span data-ttu-id="0c56a-121">O **out-anfitrião** cmdlet não foi possível determinar o que significa que a associar a saída de carateres, a **Get-Location** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0c56a-121">The **Out-Host** cmdlet could not determine what meaning to associate with the characters output by the **Get-Location** cmdlet.</span></span>

<span data-ttu-id="0c56a-122">Em vez de utilizar o texto para permitir que os comandos num pipeline comunicar, o Windows PowerShell utiliza objetos.</span><span class="sxs-lookup"><span data-stu-id="0c56a-122">Instead of using text to let commands in a pipeline communicate, Windows PowerShell uses objects.</span></span> <span data-ttu-id="0c56a-123">De ponto de vista de um utilizador, objetos de pacote informações relacionadas com um formulário que torna mais fácil manipular informações como uma unidade e extrair itens específicos que precisa.</span><span class="sxs-lookup"><span data-stu-id="0c56a-123">From the standpoint of a user, objects package related information into a form that makes it easier to manipulate the information as a unit, and extract specific items that you need.</span></span>

<span data-ttu-id="0c56a-124">O **Get-Location** comando não devolve o texto que contém o caminho atual.</span><span class="sxs-lookup"><span data-stu-id="0c56a-124">The **Get-Location** command does not return text that contains the current path.</span></span> <span data-ttu-id="0c56a-125">Devolve um pacote de informações chamados um **PathInfo** objeto que contém o caminho atual, juntamente com outras informações.</span><span class="sxs-lookup"><span data-stu-id="0c56a-125">It returns a package of information called a **PathInfo** object that contains the current path along with some other information.</span></span> <span data-ttu-id="0c56a-126">O **out-anfitrião** cmdlet, em seguida, envia esta **PathInfo** objeto para o ecrã e o Windows PowerShell decide que as informações a apresentar e como apresentá-lo com base nas suas regras de formatação.</span><span class="sxs-lookup"><span data-stu-id="0c56a-126">The **Out-Host** cmdlet then sends this **PathInfo** object to the screen, and Windows PowerShell decides what information to display and how to display it based on its formatting rules.</span></span>

<span data-ttu-id="0c56a-127">Na verdade, as informações de cabeçalho de saída pelo **Get-Location** cmdlet é adicionado apenas no final do processo, como parte do processo de formatação os dados para apresentar onscreen.</span><span class="sxs-lookup"><span data-stu-id="0c56a-127">In fact, the heading information output by the **Get-Location** cmdlet is added only at the end of the process, as part of the process of formatting the data for onscreen display.</span></span> <span data-ttu-id="0c56a-128">O que vê onscreen são um resumo de informações e não uma representação do objeto de saída completa.</span><span class="sxs-lookup"><span data-stu-id="0c56a-128">What you see onscreen is a summary of information, and not a complete representation of the output object.</span></span>

<span data-ttu-id="0c56a-129">Uma vez que poderá obter mais informações resultado de um Windows PowerShell comando que é o que veem apresentados na janela da consola, como pode obter os elementos não visível?</span><span class="sxs-lookup"><span data-stu-id="0c56a-129">Given that there may be more information output from a Windows PowerShell command than what we see displayed in the console window, how can you retrieve the non-visible elements?</span></span> <span data-ttu-id="0c56a-130">Como visualizar os dados adicionais</span><span class="sxs-lookup"><span data-stu-id="0c56a-130">How do you view the extra data?</span></span> <span data-ttu-id="0c56a-131">E e se pretende ver os dados num formato diferente do Windows PowerShell um normalmente utiliza?</span><span class="sxs-lookup"><span data-stu-id="0c56a-131">And what if you want to view the data in a format different than the one Windows PowerShell normally uses?</span></span>

<span data-ttu-id="0c56a-132">O resto deste capítulo descreve como pode detetar a estrutura dos objetos específicos do Windows PowerShell, selecionar itens específicos e formatação-los para apresentar mais fácil e como enviar estas informações para localizações de saída alternativo, tal como ficheiros e impressoras.</span><span class="sxs-lookup"><span data-stu-id="0c56a-132">The rest of this chapter discusses how you can discover the structure of specific Windows PowerShell objects, selecting specific items and formatting them for easier display, and how to send this information to alternative output locations such as files and printers.</span></span>