---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Redirecionar Dados com Cmdlets Out
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 3ca7984e831a995e80cbd8a4d83ae9225c2a4f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952125"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="07a20-103">Redirecionar dados com Out-\* Cmdlets</span><span class="sxs-lookup"><span data-stu-id="07a20-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="07a20-104">O Windows PowerShell oferece vários cmdlets que lhe permitem que controlar diretamente a saída de dados.</span><span class="sxs-lookup"><span data-stu-id="07a20-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="07a20-105">Estes cmdlets partilham características importantes dois.</span><span class="sxs-lookup"><span data-stu-id="07a20-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="07a20-106">Em primeiro lugar, geralmente, estes transformar dados em alguma forma de texto.</span><span class="sxs-lookup"><span data-stu-id="07a20-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="07a20-107">Tal porque estes dados para os componentes de sistema que necessitam de entrada de texto de saída.</span><span class="sxs-lookup"><span data-stu-id="07a20-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="07a20-108">Isto significa que precisam para representar objetos como texto.</span><span class="sxs-lookup"><span data-stu-id="07a20-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="07a20-109">Por conseguinte, o texto é formatado como vê-lo na janela da consola do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07a20-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="07a20-110">Segundo, estes cmdlets utilizam o Windows PowerShell verbo **saída** porque enviam informações a partir do Windows PowerShell para qualquer outro local.</span><span class="sxs-lookup"><span data-stu-id="07a20-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="07a20-111">O **out-anfitrião** cmdlet não é exceção: a apresentação da janela de anfitrião está fora do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07a20-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="07a20-112">Isto é importante porque, quando são enviados dados fora do Windows PowerShell, na realidade é removido.</span><span class="sxs-lookup"><span data-stu-id="07a20-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="07a20-113">Pode ver esta se tentar criar um pipeline que páginas os dados para a janela de anfitrião e, em seguida, tentar formate-o como uma lista, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="07a20-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="07a20-114">Que seria de esperar o comando para apresentar as páginas de informações de processo no formato de lista.</span><span class="sxs-lookup"><span data-stu-id="07a20-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="07a20-115">Em vez disso, apresenta a lista de tabela:</span><span class="sxs-lookup"><span data-stu-id="07a20-115">Instead, it displays the default tabular list:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="07a20-116">O **out-anfitrião** cmdlet envia os dados diretamente para a consola, por isso, o **formato-lista** comando nunca recebe nada para formatar.</span><span class="sxs-lookup"><span data-stu-id="07a20-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="07a20-117">A forma correta de estrutura este comando é colocar o **out-anfitrião** cmdlet no fim do pipeline conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="07a20-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="07a20-118">Isto faz com que os dados de processo a formatados numa lista antes de ser do bloco paginado e apresentada.</span><span class="sxs-lookup"><span data-stu-id="07a20-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="07a20-119">Isto aplica-se a todos os o **saída** cmdlets.</span><span class="sxs-lookup"><span data-stu-id="07a20-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="07a20-120">Um **saída** cmdlet sempre deve aparecer no fim do pipeline.</span><span class="sxs-lookup"><span data-stu-id="07a20-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="07a20-121">Todos os o **saída** cmdlets compor o resultado como texto, utilizando a formatação em vigor para a janela de consola, incluindo limites de comprimento de linha.</span><span class="sxs-lookup"><span data-stu-id="07a20-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="07a20-122">Resultado da consola de paginação (Out-anfitrião)</span><span class="sxs-lookup"><span data-stu-id="07a20-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="07a20-123">Por predefinição, o Windows PowerShell envia dados para a janela de anfitrião, o que é exatamente o que o Out-anfitrião cmdlet does.</span><span class="sxs-lookup"><span data-stu-id="07a20-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="07a20-124">A utilização principal para o Out-anfitrião cmdlet é os dados de paginação que discutimos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="07a20-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="07a20-125">Por exemplo, as seguintes utilizações de comando out-anfitrião para a página a saída do cmdlet Get-Command:</span><span class="sxs-lookup"><span data-stu-id="07a20-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="07a20-126">Também pode utilizar o **mais** função para dados de página.</span><span class="sxs-lookup"><span data-stu-id="07a20-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="07a20-127">No Windows PowerShell, **mais** é uma função que chama **out-alojar-paginação**.</span><span class="sxs-lookup"><span data-stu-id="07a20-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="07a20-128">O comando seguinte demonstra a utilizar o **mais** função para a página a saída de Get-Command:</span><span class="sxs-lookup"><span data-stu-id="07a20-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="07a20-129">Se incluir um ou mais nomes de ficheiros como argumentos para a função mais, a função irá ler os ficheiros especificados e os respetivos conteúdos para o anfitrião de página:</span><span class="sxs-lookup"><span data-stu-id="07a20-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="07a20-130">Rejeitar saída (Out-nulo)</span><span class="sxs-lookup"><span data-stu-id="07a20-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="07a20-131">O **out-nulo** cmdlet foi concebido para eliminar imediatamente qualquer entrada que receber.</span><span class="sxs-lookup"><span data-stu-id="07a20-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="07a20-132">Isto é útil para eliminar dados desnecessários que obtém como um efeito de um comando em execução.</span><span class="sxs-lookup"><span data-stu-id="07a20-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="07a20-133">Quando escrever o seguinte comando, não voltar nada do comando:</span><span class="sxs-lookup"><span data-stu-id="07a20-133">When type the following command, you do not get anything back from the command:</span></span>

```powreshell
Get-Command | Out-Null
```

<span data-ttu-id="07a20-134">O **out-nulo** cmdlet não rejeição a saída de erro.</span><span class="sxs-lookup"><span data-stu-id="07a20-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="07a20-135">Por exemplo, se introduzir o seguinte comando, será apresentada uma mensagem informando-o de que o Windows PowerShell não reconhece 'NotACommand é':</span><span class="sxs-lookup"><span data-stu-id="07a20-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="07a20-136">Dados de impressão (Out-impressoras)</span><span class="sxs-lookup"><span data-stu-id="07a20-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="07a20-137">Pode imprimir dados utilizando o **Out-impressora** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="07a20-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="07a20-138">O **Out-impressora** cmdlet utilizará a impressora predefinida se não fornecer um nome de impressora.</span><span class="sxs-lookup"><span data-stu-id="07a20-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="07a20-139">Pode utilizar qualquer impressora baseado no Windows, especificando o nome a apresentar.</span><span class="sxs-lookup"><span data-stu-id="07a20-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="07a20-140">Não é necessário para qualquer tipo de mapeamento de portas de impressora ou mesmo uma impressora física real.</span><span class="sxs-lookup"><span data-stu-id="07a20-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="07a20-141">Por exemplo, se tiver as Microsoft Office documento processamento de imagens as ferramentas instaladas, pode enviar os dados para um ficheiro de imagem, escrevendo:</span><span class="sxs-lookup"><span data-stu-id="07a20-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="07a20-142">Os dados (out-File)</span><span class="sxs-lookup"><span data-stu-id="07a20-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="07a20-143">Pode enviar o resultado para um ficheiro em vez da janela de consola utilizando o **out-File** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="07a20-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="07a20-144">A seguinte linha de comandos envia uma lista de processos para o ficheiro **c:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="07a20-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="07a20-145">Os resultados de utilizar o **out-File** cmdlet não pode ser o que esperar se forem utilizados para redirecionamento de saída tradicional.</span><span class="sxs-lookup"><span data-stu-id="07a20-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="07a20-146">Para compreender o respetivo comportamento, tem de ser informados da contexto no qual o **out-File** cmdlet funciona.</span><span class="sxs-lookup"><span data-stu-id="07a20-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="07a20-147">Por predefinição, o **out-File** cmdlet cria um ficheiro Unicode.</span><span class="sxs-lookup"><span data-stu-id="07a20-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="07a20-148">Esta é a predefinição melhor longa run, mas significa que as ferramentas que esperam ficheiros ASCII não funcionarão corretamente com o formato de saída predefinido.</span><span class="sxs-lookup"><span data-stu-id="07a20-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="07a20-149">Pode alterar o formato de saída predefinido para ASCII utilizando o **codificação** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="07a20-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="07a20-150">**Out-file** formatos de ficheiro de conteúdo para o aspeto do resultado da consola.</span><span class="sxs-lookup"><span data-stu-id="07a20-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="07a20-151">Isto faz com que o resultado a ser truncado tal como faz parte de uma janela da consola na maior parte das circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="07a20-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="07a20-152">Por exemplo, se executar o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="07a20-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="07a20-153">O resultado será ter este aspeto:</span><span class="sxs-lookup"><span data-stu-id="07a20-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="07a20-154">Para obter o resultado não forçar a linha encapsula num wrapper para corresponder a largura do ecrã, pode utilizar o **largura** parâmetro para especificar a largura da linha.</span><span class="sxs-lookup"><span data-stu-id="07a20-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="07a20-155">Porque **largura** é um parâmetro de número inteiro de 32 bits, o valor máximo pode ter é 2147483647.</span><span class="sxs-lookup"><span data-stu-id="07a20-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="07a20-156">Escreva o seguinte para definir a largura da linha para este valor máximo:</span><span class="sxs-lookup"><span data-stu-id="07a20-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="07a20-157">O **out-File** cmdlet é mais útil quando pretende guardar a saída tal como faria ter apresentado na consola.</span><span class="sxs-lookup"><span data-stu-id="07a20-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="07a20-158">Para melhorar o controlo sobre o formato de saída, terá de ferramentas mais avançadas.</span><span class="sxs-lookup"><span data-stu-id="07a20-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="07a20-159">Iremos abordar os o capítulo seguinte, juntamente com alguns detalhes sobre a manipulação de objeto.</span><span class="sxs-lookup"><span data-stu-id="07a20-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>