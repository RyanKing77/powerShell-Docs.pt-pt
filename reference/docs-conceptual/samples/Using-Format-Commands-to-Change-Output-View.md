---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar Comandos de Formato para Alterar a Vista de Saída
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: fba37b1d0479bf605d8f2171da27cd1bceb9976e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058272"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="e3fca-103">Utilizar Comandos de Formato para Alterar a Vista de Saída</span><span class="sxs-lookup"><span data-stu-id="e3fca-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="e3fca-104">Windows PowerShell tem um conjunto de cmdlets que permitem controlar quais propriedades são apresentadas para objetos específicos.</span><span class="sxs-lookup"><span data-stu-id="e3fca-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="e3fca-105">Os nomes de todos os cmdlets começam com o verbo **formato**.</span><span class="sxs-lookup"><span data-stu-id="e3fca-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="e3fca-106">Eles permitem-lhe selecionar uma ou mais propriedades para mostrar.</span><span class="sxs-lookup"><span data-stu-id="e3fca-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="e3fca-107">O **formato** cmdlets são **Format-Wide**, **Format-List**, **Format-Table**, e **formato personalizado**.</span><span class="sxs-lookup"><span data-stu-id="e3fca-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="e3fca-108">Descreveremos apenas a **Format-Wide**, **Format-List**, e **Format-Table** cmdlets no guia deste utilizador.</span><span class="sxs-lookup"><span data-stu-id="e3fca-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="e3fca-109">Cada cmdlet de formato tem propriedades predefinidas que serão utilizadas se não especificar as propriedades específicas para apresentar.</span><span class="sxs-lookup"><span data-stu-id="e3fca-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="e3fca-110">Cada cmdlet também utiliza o mesmo nome de parâmetro, **propriedade**para especificar quais propriedades deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="e3fca-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="e3fca-111">Uma vez **Format-Wide** mostra apenas uma única propriedade, seu **propriedade** parâmetro leva apenas um único valor, mas os parâmetros de propriedade da **Format-List** e **Format-Table** aceitará uma lista de nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e3fca-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="e3fca-112">Se usar o comando **Get-Process - nome powershell** com duas instâncias da execução do Windows PowerShell, obtém uma saída como esta:</span><span class="sxs-lookup"><span data-stu-id="e3fca-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="e3fca-113">No restante desta seção, Exploraremos como utilizar **formato** cmdlets para alterar a forma como é apresentado o resultado deste comando.</span><span class="sxs-lookup"><span data-stu-id="e3fca-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="e3fca-114">Usando em todo o formato de saída de Item único</span><span class="sxs-lookup"><span data-stu-id="e3fca-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="e3fca-115">O `Format-Wide` cmdlet, por padrão, exibe a propriedade de padrão de um objeto.</span><span class="sxs-lookup"><span data-stu-id="e3fca-115">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span>
<span data-ttu-id="e3fca-116">As informações associadas com cada objeto são apresentadas numa única coluna:</span><span class="sxs-lookup"><span data-stu-id="e3fca-116">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```output
Format-Custom                          Format-Hex
Format-List                            Format-Table
Format-Wide
```

<span data-ttu-id="e3fca-117">Também pode especificar uma propriedade não predefinido:</span><span class="sxs-lookup"><span data-stu-id="e3fca-117">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```output
Custom                                 Hex
List                                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="e3fca-118">Controlar a exibição de todo o formato com coluna</span><span class="sxs-lookup"><span data-stu-id="e3fca-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="e3fca-119">Com o `Format-Wide` cmdlet, pode apresentar apenas uma única propriedade ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="e3fca-119">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span>
<span data-ttu-id="e3fca-120">Assim, é útil para exibir listas simples que mostram apenas um elemento por linha.</span><span class="sxs-lookup"><span data-stu-id="e3fca-120">This makes it useful for displaying simple lists that show only one element per line.</span></span>
<span data-ttu-id="e3fca-121">Para obter uma lista simple, defina o valor do **coluna** parâmetro 1 digitando:</span><span class="sxs-lookup"><span data-stu-id="e3fca-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 1
```

```output
Custom
Hex
List
Table
Wide
```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="e3fca-122">Usando o formato de lista para obter uma exibição de lista</span><span class="sxs-lookup"><span data-stu-id="e3fca-122">Using Format-List for a List View</span></span>

<span data-ttu-id="e3fca-123">O **Format-List** cmdlet apresenta um objeto na forma de obter uma lista, com cada propriedade com o nome e exibidos numa linha separada:</span><span class="sxs-lookup"><span data-stu-id="e3fca-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="e3fca-124">Pode especificar propriedades tantos quantos quiser:</span><span class="sxs-lookup"><span data-stu-id="e3fca-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="e3fca-125">Ao obter as informações detalhadas com o formato de lista com carateres universais</span><span class="sxs-lookup"><span data-stu-id="e3fca-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="e3fca-126">O **Format-List** cmdlet permite-lhe utilizar um caráter universal como o valor do respetivo **propriedade** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e3fca-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="e3fca-127">Isto permite-lhe apresentar informações detalhadas.</span><span class="sxs-lookup"><span data-stu-id="e3fca-127">This lets you display detailed information.</span></span> <span data-ttu-id="e3fca-128">Muitas vezes, os objetos incluem mais informações que precisa, razão pela qual o Windows PowerShell não mostra todos os valores de propriedade por predefinição.</span><span class="sxs-lookup"><span data-stu-id="e3fca-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="e3fca-129">Para mostrar todas as propriedades de um objeto, utilize o **Format-List-propriedade \&#42;** comando.</span><span class="sxs-lookup"><span data-stu-id="e3fca-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="e3fca-130">O comando seguinte gera mais de 60 linhas da saída para um único processo:</span><span class="sxs-lookup"><span data-stu-id="e3fca-130">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="e3fca-131">Embora o **Format-List** comando é útil para mostrar os detalhes, se desejar uma visão geral de saída que inclui o número de itens, uma exibição tabular mais simples, muitas vezes, é mais útil.</span><span class="sxs-lookup"><span data-stu-id="e3fca-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="e3fca-132">Usando o formato de tabela para saída Tabular</span><span class="sxs-lookup"><span data-stu-id="e3fca-132">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="e3fca-133">Se utilizar o **Format-Table** cmdlet com não nomes de propriedade especificado para formatar a saída da **Get-Process** de comando, obtém exatamente a mesma saída como acontece sem executar qualquer formatação.</span><span class="sxs-lookup"><span data-stu-id="e3fca-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="e3fca-134">O motivo é que os processos são normalmente apresentados num formato tabular, assim como a maioria dos objetos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3fca-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="e3fca-135">Melhorando a saída do Format-Table (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="e3fca-135">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="e3fca-136">Embora uma exibição tabular é útil para a exibição muita informação comparável, poderá ser difícil de interpretar se a exibição é demasiado pequena para os dados.</span><span class="sxs-lookup"><span data-stu-id="e3fca-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="e3fca-137">Por exemplo, se tentar exibir o caminho do processo, o ID, nome e empresa, receberá saída truncada para o caminho de processo e a coluna de empresa:</span><span class="sxs-lookup"><span data-stu-id="e3fca-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="e3fca-138">Se especificar a **AutoSize** parâmetro ao executar o **Format-Table** comando, o Windows PowerShell irá calcular a largura das colunas com base em dados reais, pretende apresentar.</span><span class="sxs-lookup"><span data-stu-id="e3fca-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="e3fca-139">Isso faz com que o **caminho** coluna legível, mas a coluna de empresa permanece truncado:</span><span class="sxs-lookup"><span data-stu-id="e3fca-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="e3fca-140">O **Format-Table** cmdlet ainda pode truncar a dados, mas isso apenas será feito isso no final do ecrã.</span><span class="sxs-lookup"><span data-stu-id="e3fca-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="e3fca-141">Propriedades, diferente do apresentado, último recebem tanto tamanho à medida que necessitam para o elemento de dados mais longo apresentar corretamente.</span><span class="sxs-lookup"><span data-stu-id="e3fca-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="e3fca-142">Pode ver que o nome da empresa está visível mas caminho será truncado se alternar os locais dos **caminho** e **empresa** no **propriedade** lista de valores:</span><span class="sxs-lookup"><span data-stu-id="e3fca-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="e3fca-143">O **Format-Table** comando assume que o nearer é uma propriedade para o início da lista de propriedades, é mais importante.</span><span class="sxs-lookup"><span data-stu-id="e3fca-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="e3fca-144">Portanto, ele tenta exibir as propriedades mais próximo início completamente.</span><span class="sxs-lookup"><span data-stu-id="e3fca-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="e3fca-145">Se o **Format-Table** comando não é possível apresentar todas as propriedades, irá remover algumas colunas na exibição e fornecer um aviso.</span><span class="sxs-lookup"><span data-stu-id="e3fca-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="e3fca-146">Pode ver este comportamento se fizer **nome** a última propriedade na lista:</span><span class="sxs-lookup"><span data-stu-id="e3fca-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="e3fca-147">No resultado acima, a coluna ID é truncada para torná-lo a se adaptam a listagem e os cabeçalhos de coluna são empilhados a cópia de segurança.</span><span class="sxs-lookup"><span data-stu-id="e3fca-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="e3fca-148">Redimensionar automaticamente as colunas não sempre faz o que deseja.</span><span class="sxs-lookup"><span data-stu-id="e3fca-148">Automatically resizing the columns does not always do what you want.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="e3fca-149">Saída do Format-Table de encapsulamento de aplicações nas colunas (moldagem)</span><span class="sxs-lookup"><span data-stu-id="e3fca-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="e3fca-150">Pode forçar longas **Format-Table** dados para encapsular dentro de sua coluna de apresentação com o **encapsular** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e3fca-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="e3fca-151">Utilizar o **encapsular** parâmetro sozinho não necessariamente fará o que esperar, uma vez que utiliza as predefinições se não especificar também **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="e3fca-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="e3fca-152">Uma vantagem de utilizar o **encapsular** parâmetro por si só, é que ele não abrandar processamento muito.</span><span class="sxs-lookup"><span data-stu-id="e3fca-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="e3fca-153">Se efetuar uma listagem de arquivos recursiva de um sistema de diretório grandes, poderá demorar muito tempo e utilizar muita memória antes de exibir os primeiros itens de saída, se usar **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="e3fca-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="e3fca-154">Se não estiver preocupado com carga de sistema, em seguida, **AutoSize** funciona bem com o **encapsular** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e3fca-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="e3fca-155">As colunas iniciais são sempre que poderá máximo da largura que precisam para exibir itens numa linha, tal como quando especificar **AutoSize** sem o **encapsular** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e3fca-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="e3fca-156">A única diferença é que a coluna final será moldada se necessário:</span><span class="sxs-lookup"><span data-stu-id="e3fca-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="e3fca-157">Algumas colunas poderão, não, ser apresentadas se especificar as colunas mais amplas em primeiro lugar, portanto, é mais segura especificar os elementos de dados mais pequenas primeiro.</span><span class="sxs-lookup"><span data-stu-id="e3fca-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="e3fca-158">No exemplo seguinte, especificamos o elemento de caminho extremamente grande primeiro e, mesmo com o encapsulamento de aplicações, perdemos ainda o último **nome** coluna:</span><span class="sxs-lookup"><span data-stu-id="e3fca-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="e3fca-159">Organizar a saída da tabela (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="e3fca-159">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="e3fca-160">É o outro parâmetro útil para controle de saída tabular **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="e3fca-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="e3fca-161">Em particular já listagens de tabela podem ser difíceis de comparar.</span><span class="sxs-lookup"><span data-stu-id="e3fca-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="e3fca-162">O **GroupBy** resultado com base num valor de propriedade de grupos de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e3fca-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="e3fca-163">Por exemplo, podemos pode agrupar processos pela empresa para a inspeção mais fácil, omitindo o valor da empresa a partir da lista de propriedade:</span><span class="sxs-lookup"><span data-stu-id="e3fca-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```