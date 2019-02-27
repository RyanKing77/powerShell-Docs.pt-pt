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
# <a name="how-to-write-a-powershell-script-module"></a>How to Write a PowerShell Script Module (Como Escrever um Módulo de Script do PowerShell)

Um módulo de script é, essencialmente, qualquer válido script do PowerShell salva numa extensão. psm1. Esta extensão permite que o motor do PowerShell utilizar um número de regras e cmdlets em seu arquivo. A maioria desses recursos existem para o ajudar a instalar seu código em outros sistemas, bem como gerir o controlo de âmbito. Também pode utilizar um ficheiro de manifesto de módulo, que pode descrever instalações ainda mais complexas e soluções.

## <a name="writing-a-powershell-script-module"></a>Escrever um módulo de Script do PowerShell

Criar um módulo de script ao guardar um script do PowerShell válido para um ficheiro. psm1 e, em seguida, salvar esse arquivo num diretório localizado onde o PowerShell pode encontrá-la. Nessa pasta que também é possível colocar todos os recursos que necessários para executar o script, bem como um arquivo de manifesto que descreve para o PowerShell como funciona o módulo.

#### <a name="to-create-a-basic-powershell-module"></a>Para criar um módulo do PowerShell básico

1. Escolher um script do PowerShell existente e salve o script com uma extensão. psm1.

   A guardar um script com o. psm1 extensão significa que pode utilizar os cmdlets do módulo, tal como [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), no mesmo. Estes cmdlets existe principalmente para que possa facilmente importar e exportar o seu código em sistemas de outro utilizador. (A solução alternativa seria ao carregar o seu código em outros sistemas e, em seguida, ponto de código-fonte-la na memória Active Directory, o que não é uma solução particularmente dimensionável.) Para obter mais informações, consulte a **Cmdlets do módulo e as variáveis** secção [módulos do Windows PowerShell](./understanding-a-windows-powershell-module.md) tenha em atenção que, por predefinição, todas as funções no seu script estará acessíveis aos utilizadores que importar seu. psm1 ficheiro, mas as propriedades serão não.

   Um exemplo de script do PowerShell, intitulado Show-calendário, está disponível no final deste tópico.

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

2. Se pretender controlar o acesso de usuário a determinadas funções ou propriedades, chame [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) no final do seu script.

   O código de exemplo na parte inferior da página tem apenas uma função, que, por padrão, iria ser exposta. No entanto, é recomendável que chame explicitamente as funções que deseja expor, conforme descrito no seguinte código:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Também pode restringir o que é importado com um manifesto de módulo. Para obter mais informações, consulte [importar um módulo do PowerShell](./importing-a-powershell-module.md) e [como escrever um manifesto de módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Se tiver de módulos que seu próprio módulo tem de ter carregado, pode usá-los com uma chamada para `Import-Module`, na parte superior do seu próprio módulo.

   `Import-Module` é um cmdlet que importa um módulo de destino num sistema. Como tal, ele também é usado posteriormente no procedimento para instalar o seu próprio módulo também. O código de exemplo na parte inferior desta página não utiliza quaisquer módulos de importação. Se refletisse, no entanto, elas seriam listadas na parte superior do ficheiro, conforme descrito no seguinte código:

   ```powershell
   Import-Module GenericModule
   ```

4. Se quiser descrevem seu módulo para o sistema de ajuda do PowerShell, pode fazer isso com os comentários de ajuda padrão dentro do arquivo, ou com um arquivo de ajuda adicional.

   O exemplo de código na parte inferior deste tópico inclui as informações de ajuda nos comentários. Se assim o desejar, também poderia escrever expandidos arquivos XML que contêm conteúdo de ajuda adicional. Para obter mais informações, consulte [ajudar do escrita para o Windows PowerShell módulos](./writing-help-for-windows-powershell-modules.md).

5. Se tiver módulos adicionais, arquivos XML ou outro conteúdo que pretende empacotar com seu módulo, pode fazê-lo com um manifesto de módulo.

   Um manifesto de módulo é um ficheiro que contém os nomes dos outros módulos, esquemas de diretório, números de controlo de versões, dados de autor e outras partes de informações. PowerShell utiliza o ficheiro de manifesto do módulo para organizar e implementar a sua solução. No entanto, devido à natureza relativamente simples deste exemplo, um arquivo de manifesto não foi necessária. Para obter mais informações, consulte [manifestos de módulo](./how-to-write-a-powershell-module-manifest.md).

6. Para instalar e executar seu módulo, salvar o módulo em um dos caminhos de PowerShell apropriados e fazer uma chamada para `Import-Module`.

   Os caminhos onde pode instalar o módulo estão localizados no `$env:PSModulePath` variável global. Por exemplo, seria um caminho comum para guardar um módulo num sistema `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Certifique-se de que crie uma pasta para seu módulo existir no, mesmo se for apenas um ficheiro. psm1 único. Se não tiver guardado o seu módulo a uma destes caminhos, terá de passar a localização do seu módulo na chamada para `Import-Module`. (Caso contrário, PowerShell não seria capaz de encontrá-lo.) A partir do PowerShell 3.0, se tiver efetuado seu módulo em um dos caminhos dos módulos do PowerShell, é necessário não explicitamente importá-lo: a simples presença de um usuário chama sua função e irá carregá-lo automaticamente. Para obter mais informações sobre o caminho do módulo, consulte [importar um módulo do PowerShell](./importing-a-powershell-module.md) e [variável de ambiente de PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Para remover um módulo de serviço do Active Directory, fazer uma chamada para [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

Tenha em atenção que [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) remove seu módulo do Active Directory memória – ele não, na verdade, eliminá-la onde guardou os ficheiros de módulo.

### <a name="show-calendar-code-example"></a>Exemplo de código do calendário show

O exemplo seguinte é um módulo de script simples que contém uma única função denominada calendário Show. Esta função mostra uma representação visual de um calendário. Além disso, o exemplo contém as cadeias de caracteres de ajuda do PowerShell para a sinopse, a descrição, a valores de parâmetro e o exemplo. Tenha em atenção que a última linha de código indica que a função de calendário Show será exportada como um membro do módulo, quando o módulo é importado.

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
