---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Redirecionar Dados com Cmdlets Out
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: f08879f436ce751b176af020aba21e90f09aa61f
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321014"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="d0d09-103">Redirecionar dados com o Out-\* Cmdlets</span><span class="sxs-lookup"><span data-stu-id="d0d09-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="d0d09-104">Windows PowerShell fornece vários cmdlets que lhe permitam que controlar dados diretamente de saída.</span><span class="sxs-lookup"><span data-stu-id="d0d09-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="d0d09-105">Estes cmdlets partilhar duas características importantes.</span><span class="sxs-lookup"><span data-stu-id="d0d09-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="d0d09-106">Em primeiro lugar, eles geralmente transformam dados de alguma forma de texto.</span><span class="sxs-lookup"><span data-stu-id="d0d09-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="d0d09-107">Eles fazer isso, uma vez que os dados para os componentes de sistema que exigem entrada de texto de saída.</span><span class="sxs-lookup"><span data-stu-id="d0d09-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="d0d09-108">Isso significa que precisam para representar os objetos como texto.</span><span class="sxs-lookup"><span data-stu-id="d0d09-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="d0d09-109">Por conseguinte, o texto esteja formatado como vê-la na janela de consola do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0d09-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="d0d09-110">Em segundo lugar, estes cmdlets usam o verbo de Windows PowerShell **horizontalmente** porque eles enviam informações do Windows PowerShell a algum outro lugar.</span><span class="sxs-lookup"><span data-stu-id="d0d09-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="d0d09-111">O **out-Host** cmdlet não é exceção: a apresentação da janela de anfitrião está fora do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0d09-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="d0d09-112">Isso é importante porque quando dados são enviados para fora do Windows PowerShell, na verdade, é removido.</span><span class="sxs-lookup"><span data-stu-id="d0d09-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="d0d09-113">Pode ver isso se tentar criar um pipeline que páginas os dados para a janela de anfitrião e, em seguida, tentar formatá-lo como uma lista, conforme mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="d0d09-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="d0d09-114">Pode esperar o comando para exibir páginas de informações do processo num formato de lista.</span><span class="sxs-lookup"><span data-stu-id="d0d09-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="d0d09-115">Em vez disso, ele exibe a lista em tabela:</span><span class="sxs-lookup"><span data-stu-id="d0d09-115">Instead, it displays the default tabular list:</span></span>

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

<span data-ttu-id="d0d09-116">O **out-Host** cmdlet envia os dados diretamente para a consola de, pelo que a **Format-List** comando nunca recebe nada para formatar.</span><span class="sxs-lookup"><span data-stu-id="d0d09-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="d0d09-117">A maneira correta de estruturar este comando é colocar o **out-Host** cmdlet no final do pipeline, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="d0d09-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="d0d09-118">Isso faz com que o processamento de dados sejam formatados de uma lista antes de ser paginada e apresentada.</span><span class="sxs-lookup"><span data-stu-id="d0d09-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

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

<span data-ttu-id="d0d09-119">Isto aplica-se a todos os **horizontalmente** cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d0d09-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="d0d09-120">Uma **horizontalmente** cmdlet sempre deve aparecer no final do pipeline.</span><span class="sxs-lookup"><span data-stu-id="d0d09-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="d0d09-121">Todos os **horizontalmente** cmdlets compõem uma saída como texto, usando a formatação em vigor para a janela de consola, incluindo limites de tamanho de linha.</span><span class="sxs-lookup"><span data-stu-id="d0d09-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="d0d09-122">Resultado da consola de paginação (Out-Host)</span><span class="sxs-lookup"><span data-stu-id="d0d09-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="d0d09-123">Por predefinição, o Windows PowerShell envia dados para a janela de anfitrião, o que é exatamente o que o cmdlet out-Host faz.</span><span class="sxs-lookup"><span data-stu-id="d0d09-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="d0d09-124">Usada principalmente para o Out-Host cmdlet é dados de paginação, como discutido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d0d09-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="d0d09-125">Por exemplo, o seguinte comando utiliza out-Host para a página a saída do cmdlet Get-Command:</span><span class="sxs-lookup"><span data-stu-id="d0d09-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="d0d09-126">Também pode utilizar o **mais** função para dados de página.</span><span class="sxs-lookup"><span data-stu-id="d0d09-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="d0d09-127">No Windows PowerShell, **mais** é uma função que chama **out-Host-paginação**.</span><span class="sxs-lookup"><span data-stu-id="d0d09-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="d0d09-128">O comando seguinte demonstra como utilizar o **mais** função para a página a saída de Get-Command:</span><span class="sxs-lookup"><span data-stu-id="d0d09-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="d0d09-129">Se incluir um ou mais nomes de ficheiros como argumentos para a função mais, a função irá ler os ficheiros especificados e seu conteúdo para o anfitrião de página:</span><span class="sxs-lookup"><span data-stu-id="d0d09-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="d0d09-130">Descarte de saída (Out-Null)</span><span class="sxs-lookup"><span data-stu-id="d0d09-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="d0d09-131">O **out-Null** cmdlet foi desenvolvido para eliminar imediatamente qualquer entrada que recebe.</span><span class="sxs-lookup"><span data-stu-id="d0d09-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="d0d09-132">Isto é útil para dados desnecessários obtidas como um efeito colateral de executar um comando de descarte.</span><span class="sxs-lookup"><span data-stu-id="d0d09-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="d0d09-133">Quando escreva o seguinte comando, não recebe nada do comando:</span><span class="sxs-lookup"><span data-stu-id="d0d09-133">When type the following command, you do not get anything back from the command:</span></span>

```powershell
Get-Command | Out-Null
```

<span data-ttu-id="d0d09-134">O **out-Null** cmdlet não elimine a saída de erro.</span><span class="sxs-lookup"><span data-stu-id="d0d09-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="d0d09-135">Por exemplo, se introduzir o comando seguinte, é apresentada uma mensagem informando-o de que o Windows PowerShell não reconhece "NotACommand é":</span><span class="sxs-lookup"><span data-stu-id="d0d09-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="d0d09-136">Dados de impressão (Out-impressora)</span><span class="sxs-lookup"><span data-stu-id="d0d09-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="d0d09-137">Pode imprimir dados ao utilizar o **Out-impressora** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d0d09-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="d0d09-138">O **Out-impressora** cmdlet irá utilizar a sua impressora padrão se não fornecer um nome da impressora.</span><span class="sxs-lookup"><span data-stu-id="d0d09-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="d0d09-139">Pode usar qualquer impressora baseados em Windows, especificando seu nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="d0d09-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="d0d09-140">Não é necessário para qualquer tipo de mapeamento de portas de impressora ou até mesmo uma impressora física real.</span><span class="sxs-lookup"><span data-stu-id="d0d09-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="d0d09-141">Por exemplo, se tiver ferramentas Microsoft Office de geração de imagens documento instaladas, pode enviar os dados para um ficheiro de imagem ao escrever:</span><span class="sxs-lookup"><span data-stu-id="d0d09-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="d0d09-142">Guardar os dados (out-File)</span><span class="sxs-lookup"><span data-stu-id="d0d09-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="d0d09-143">Pode enviar a saída para um ficheiro em vez da janela de consola utilizando o **out-File** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d0d09-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="d0d09-144">A seguinte linha de comando envia uma lista de processos para o ficheiro **c:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="d0d09-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="d0d09-145">Os resultados de utilizar o **out-File** cmdlet pode não ser o que esperar se forem utilizadas para redirecionamento de saída tradicional.</span><span class="sxs-lookup"><span data-stu-id="d0d09-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="d0d09-146">Para compreender seu comportamento, deve estar ciente de contexto no qual o **out-File** opera de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d0d09-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="d0d09-147">Por predefinição, o **out-File** cmdlet cria um ficheiro Unicode.</span><span class="sxs-lookup"><span data-stu-id="d0d09-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="d0d09-148">Esta é a predefinição de melhor a longo prazo, mas significa que as ferramentas que esperam ficheiros ASCII não funcionará corretamente com o formato de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="d0d09-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="d0d09-149">Pode alterar o formato de saída padrão em ASCII, utilizando o **Encoding** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="d0d09-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="d0d09-150">**Out-file** conteúdos como resultado da consola do formatos de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="d0d09-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="d0d09-151">Isso faz com que a saída para ser truncado, tal como numa janela de consola, na maioria das circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="d0d09-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="d0d09-152">Por exemplo, se executar o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d0d09-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="d0d09-153">A saída terá o seguinte aspeto:</span><span class="sxs-lookup"><span data-stu-id="d0d09-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="d0d09-154">Para obter o resultado que não o força inclui de linha de acordo com a largura da tela, pode utilizar o **largura** parâmetro para especificar a largura da linha.</span><span class="sxs-lookup"><span data-stu-id="d0d09-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="d0d09-155">Uma vez **largura** é um parâmetro de número inteiro de 32 bits, o valor máximo, ele pode ter é 2147483647.</span><span class="sxs-lookup"><span data-stu-id="d0d09-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="d0d09-156">Escreva o seguinte para definir a largura da linha para este valor máximo:</span><span class="sxs-lookup"><span data-stu-id="d0d09-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="d0d09-157">O **out-File** cmdlet é mais útil quando pretende guardar a saída tal como seria ter apresentado na consola.</span><span class="sxs-lookup"><span data-stu-id="d0d09-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="d0d09-158">Para obter mais controle sobre o formato de saída, precisa de ferramentas mais avançadas.</span><span class="sxs-lookup"><span data-stu-id="d0d09-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="d0d09-159">Vamos ver aqueles no capítulo seguinte, juntamente com alguns detalhes sobre a manipulação de objetos.</span><span class="sxs-lookup"><span data-stu-id="d0d09-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>