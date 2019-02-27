---
title: Como escrever um módulo de Script do PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: e8b7151538235cdf7183b78aa8df7e596d6bcfd9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848917"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="52482-102">How to Write a PowerShell Script Module (Como Escrever um Módulo de Script do PowerShell)</span><span class="sxs-lookup"><span data-stu-id="52482-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="52482-103">Um módulo de script é, essencialmente, qualquer válido script do PowerShell salva numa extensão. psm1.</span><span class="sxs-lookup"><span data-stu-id="52482-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="52482-104">Esta extensão permite que o motor do PowerShell utilizar um número de regras e cmdlets em seu arquivo.</span><span class="sxs-lookup"><span data-stu-id="52482-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="52482-105">A maioria desses recursos existem para o ajudar a instalar seu código em outros sistemas, bem como gerir o controlo de âmbito.</span><span class="sxs-lookup"><span data-stu-id="52482-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="52482-106">Também pode utilizar um ficheiro de manifesto de módulo, que pode descrever instalações ainda mais complexas e soluções.</span><span class="sxs-lookup"><span data-stu-id="52482-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="52482-107">Escrever um módulo de Script do PowerShell</span><span class="sxs-lookup"><span data-stu-id="52482-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="52482-108">Criar um módulo de script ao guardar um script do PowerShell válido para um ficheiro. psm1 e, em seguida, salvar esse arquivo num diretório localizado onde o PowerShell pode encontrá-la.</span><span class="sxs-lookup"><span data-stu-id="52482-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="52482-109">Nessa pasta que também é possível colocar todos os recursos que necessários para executar o script, bem como um arquivo de manifesto que descreve para o PowerShell como funciona o módulo.</span><span class="sxs-lookup"><span data-stu-id="52482-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="52482-110">Para criar um módulo do PowerShell básico</span><span class="sxs-lookup"><span data-stu-id="52482-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="52482-111">Escolher um script do PowerShell existente e salve o script com uma extensão. psm1.</span><span class="sxs-lookup"><span data-stu-id="52482-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="52482-112">A guardar um script com o. psm1 extensão significa que pode utilizar os cmdlets do módulo, tal como [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), no mesmo.</span><span class="sxs-lookup"><span data-stu-id="52482-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="52482-113">Estes cmdlets existe principalmente para que possa facilmente importar e exportar o seu código em sistemas de outro utilizador.</span><span class="sxs-lookup"><span data-stu-id="52482-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="52482-114">(A solução alternativa seria ao carregar o seu código em outros sistemas e, em seguida, ponto de código-fonte-la na memória Active Directory, o que não é uma solução particularmente dimensionável.) Para obter mais informações, consulte a **Cmdlets do módulo e as variáveis** secção [módulos do Windows PowerShell](./understanding-a-windows-powershell-module.md) tenha em atenção que, por predefinição, todas as funções no seu script estará acessíveis aos utilizadores que importar seu. psm1 ficheiro, mas as propriedades serão não.</span><span class="sxs-lookup"><span data-stu-id="52482-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script will be accessible to users who import your .psm1 file, but properties will not.</span></span>

   <span data-ttu-id="52482-115">Um exemplo de script do PowerShell, intitulado Show-calendário, está disponível no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="52482-115">An example PowerShell script, entitled Show-Calendar, is available at the end of this topic.</span></span>

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. <span data-ttu-id="52482-116">Se pretender controlar o acesso de usuário a determinadas funções ou propriedades, chame [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) no final do seu script.</span><span class="sxs-lookup"><span data-stu-id="52482-116">If you wish to control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="52482-117">O código de exemplo na parte inferior da página tem apenas uma função, que, por padrão, iria ser exposta.</span><span class="sxs-lookup"><span data-stu-id="52482-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="52482-118">No entanto, é recomendável que chame explicitamente as funções que deseja expor, conforme descrito no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="52482-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="52482-119">Também pode restringir o que é importado com um manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="52482-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="52482-120">Para obter mais informações, consulte [importar um módulo do PowerShell](./importing-a-powershell-module.md) e [como escrever um manifesto de módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="52482-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="52482-121">Se tiver de módulos que seu próprio módulo tem de ter carregado, pode usá-los com uma chamada para `Import-Module`, na parte superior do seu próprio módulo.</span><span class="sxs-lookup"><span data-stu-id="52482-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="52482-122">`Import-Module` é um cmdlet que importa um módulo de destino num sistema.</span><span class="sxs-lookup"><span data-stu-id="52482-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="52482-123">Como tal, ele também é usado posteriormente no procedimento para instalar o seu próprio módulo também.</span><span class="sxs-lookup"><span data-stu-id="52482-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="52482-124">O código de exemplo na parte inferior desta página não utiliza quaisquer módulos de importação.</span><span class="sxs-lookup"><span data-stu-id="52482-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="52482-125">Se refletisse, no entanto, elas seriam listadas na parte superior do ficheiro, conforme descrito no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="52482-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="52482-126">Se quiser descrevem seu módulo para o sistema de ajuda do PowerShell, pode fazer isso com os comentários de ajuda padrão dentro do arquivo, ou com um arquivo de ajuda adicional.</span><span class="sxs-lookup"><span data-stu-id="52482-126">If you want to describe your module to the PowerShell Help system, you can do so either with the standard help comments inside the file, or with an additional Help file.</span></span>

   <span data-ttu-id="52482-127">O exemplo de código na parte inferior deste tópico inclui as informações de ajuda nos comentários.</span><span class="sxs-lookup"><span data-stu-id="52482-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="52482-128">Se assim o desejar, também poderia escrever expandidos arquivos XML que contêm conteúdo de ajuda adicional.</span><span class="sxs-lookup"><span data-stu-id="52482-128">If you so choose, you could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="52482-129">Para obter mais informações, consulte [ajudar do escrita para o Windows PowerShell módulos](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="52482-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="52482-130">Se tiver módulos adicionais, arquivos XML ou outro conteúdo que pretende empacotar com seu módulo, pode fazê-lo com um manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="52482-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="52482-131">Um manifesto de módulo é um ficheiro que contém os nomes dos outros módulos, esquemas de diretório, números de controlo de versões, dados de autor e outras partes de informações.</span><span class="sxs-lookup"><span data-stu-id="52482-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="52482-132">PowerShell utiliza o ficheiro de manifesto do módulo para organizar e implementar a sua solução.</span><span class="sxs-lookup"><span data-stu-id="52482-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="52482-133">No entanto, devido à natureza relativamente simples deste exemplo, um arquivo de manifesto não foi necessária.</span><span class="sxs-lookup"><span data-stu-id="52482-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="52482-134">Para obter mais informações, consulte [manifestos de módulo](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="52482-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="52482-135">Para instalar e executar seu módulo, salvar o módulo em um dos caminhos de PowerShell apropriados e fazer uma chamada para `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="52482-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="52482-136">Os caminhos onde pode instalar o módulo estão localizados no `$env:PSModulePath` variável global.</span><span class="sxs-lookup"><span data-stu-id="52482-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="52482-137">Por exemplo, seria um caminho comum para guardar um módulo num sistema `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="52482-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="52482-138">Certifique-se de que crie uma pasta para seu módulo existir no, mesmo se for apenas um ficheiro. psm1 único.</span><span class="sxs-lookup"><span data-stu-id="52482-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="52482-139">Se não tiver guardado o seu módulo a uma destes caminhos, terá de passar a localização do seu módulo na chamada para `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="52482-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="52482-140">(Caso contrário, PowerShell não seria capaz de encontrá-lo.) A partir do PowerShell 3.0, se tiver efetuado seu módulo em um dos caminhos dos módulos do PowerShell, é necessário não explicitamente importá-lo: a simples presença de um usuário chama sua função e irá carregá-lo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="52482-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module on one of the PowerShell module paths, you do not need to explicitly import it: simply having a user call your function will automatically load it.</span></span> <span data-ttu-id="52482-141">Para obter mais informações sobre o caminho do módulo, consulte [importar um módulo do PowerShell](./importing-a-powershell-module.md) e [variável de ambiente de PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="52482-141">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="52482-142">Para remover um módulo de serviço do Active Directory, fazer uma chamada para [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="52482-142">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

<span data-ttu-id="52482-143">Tenha em atenção que [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) remove seu módulo do Active Directory memória – ele não, na verdade, eliminá-la onde guardou os ficheiros de módulo.</span><span class="sxs-lookup"><span data-stu-id="52482-143">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="52482-144">Exemplo de código do calendário show</span><span class="sxs-lookup"><span data-stu-id="52482-144">Show-Calendar code example</span></span>

<span data-ttu-id="52482-145">O exemplo seguinte é um módulo de script simples que contém uma única função denominada calendário Show.</span><span class="sxs-lookup"><span data-stu-id="52482-145">The following example is a simple script module that contains a single function named Show-Calendar.</span></span> <span data-ttu-id="52482-146">Esta função mostra uma representação visual de um calendário.</span><span class="sxs-lookup"><span data-stu-id="52482-146">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="52482-147">Além disso, o exemplo contém as cadeias de caracteres de ajuda do PowerShell para a sinopse, a descrição, a valores de parâmetro e o exemplo.</span><span class="sxs-lookup"><span data-stu-id="52482-147">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="52482-148">Tenha em atenção que a última linha de código indica que a função de calendário Show será exportada como um membro do módulo, quando o módulo é importado.</span><span class="sxs-lookup"><span data-stu-id="52482-148">Note that the last line of code indicates that the Show-Calendar function will be exported as a module member when the module is imported.</span></span>

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("'n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " 'n" + $padding + $header + "'n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
