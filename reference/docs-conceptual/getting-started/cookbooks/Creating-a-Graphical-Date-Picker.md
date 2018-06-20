---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Criar um Seletor de Datas Gráfico
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 3727c90c314a6fc1b3a338ec60e44259f153d954
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954845"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="7a176-103">Criar um Seletor de Datas Gráfico</span><span class="sxs-lookup"><span data-stu-id="7a176-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="7a176-104">Utilize o Windows PowerShell 3.0 e versões posteriores para criar um formulário com um controlo de calendário estilo gráfica, que permite aos utilizadores selecionar um dia do mês.</span><span class="sxs-lookup"><span data-stu-id="7a176-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="7a176-105">Criar um controlo de selecionador de data gráfica</span><span class="sxs-lookup"><span data-stu-id="7a176-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="7a176-106">Copiar e, em seguida, cole o seguinte no ISE do Windows PowerShell e, em seguida, guarde-o como um script do Windows PowerShell (. ps1).</span><span class="sxs-lookup"><span data-stu-id="7a176-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="7a176-107">O script começa por carregar duas classes de .NET Framework: **Drawing por uma questão** e **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="7a176-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="7a176-108">Em seguida, iniciar uma nova instância da classe de .NET Framework **Windows.Forms.Form**; que fornece uma forma em branco ou controla a janela para o qual pode começar a adicionar.</span><span class="sxs-lookup"><span data-stu-id="7a176-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="7a176-109">Depois de criar uma instância da classe do formulário, atribua valores a três propriedades desta classe.</span><span class="sxs-lookup"><span data-stu-id="7a176-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="7a176-110">**Texto.**</span><span class="sxs-lookup"><span data-stu-id="7a176-110">**Text.**</span></span> <span data-ttu-id="7a176-111">Isto torna-se o título da janela.</span><span class="sxs-lookup"><span data-stu-id="7a176-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="7a176-112">**Tamanho.**</span><span class="sxs-lookup"><span data-stu-id="7a176-112">**Size.**</span></span> <span data-ttu-id="7a176-113">Este é o tamanho do formulário, em pixels.</span><span class="sxs-lookup"><span data-stu-id="7a176-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="7a176-114">O script anterior cria um formulário que é 243 pixéis wide por 230 pixels altura.</span><span class="sxs-lookup"><span data-stu-id="7a176-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="7a176-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="7a176-115">**StartingPosition.**</span></span> <span data-ttu-id="7a176-116">Esta propriedade opcional é definida como **CenterScreen** no script anterior.</span><span class="sxs-lookup"><span data-stu-id="7a176-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="7a176-117">Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário é aberto.</span><span class="sxs-lookup"><span data-stu-id="7a176-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="7a176-118">Ao definir o **StartingPosition** para **CenterScreen**, automaticamente estiver a apresentar o formulário no meio do ecrã de cada vez que carrega.</span><span class="sxs-lookup"><span data-stu-id="7a176-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="7a176-119">Em seguida, criar e, em seguida, adicionar um controlo de calendário do formulário.</span><span class="sxs-lookup"><span data-stu-id="7a176-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="7a176-120">Neste exemplo, o dia atual não realçado ou não está dentro de um círculo.</span><span class="sxs-lookup"><span data-stu-id="7a176-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="7a176-121">Os utilizadores podem selecionar apenas um dia no calendário em simultâneo.</span><span class="sxs-lookup"><span data-stu-id="7a176-121">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="7a176-122">Em seguida, crie um **OK** botão para o formulário.</span><span class="sxs-lookup"><span data-stu-id="7a176-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="7a176-123">Especifique o tamanho e o comportamento do **OK** botão.</span><span class="sxs-lookup"><span data-stu-id="7a176-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="7a176-124">Neste exemplo, a posição do botão é 165 pixels limite superior do formulário e 38 pixéis do limite esquerdo.</span><span class="sxs-lookup"><span data-stu-id="7a176-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="7a176-125">A altura do botão é 23 pixéis, enquanto o comprimento do botão for 75 pixéis.</span><span class="sxs-lookup"><span data-stu-id="7a176-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="7a176-126">O script utiliza tipos de Windows Forms predefinidos para determinar os comportamentos do botão.</span><span class="sxs-lookup"><span data-stu-id="7a176-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="7a176-127">Da mesma forma, crie um **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="7a176-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="7a176-128">O **Cancelar** botão está 165 pixels da parte superior, mas 113 pixéis do limite esquerdo da janela.</span><span class="sxs-lookup"><span data-stu-id="7a176-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="7a176-129">Definir o **Topmost** propriedade **$true** para forçar a janela para o abrir visível outros windows abertas e caixas de diálogo.</span><span class="sxs-lookup"><span data-stu-id="7a176-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="7a176-130">Adicione a seguinte linha de código para apresentar o formulário no Windows.</span><span class="sxs-lookup"><span data-stu-id="7a176-130">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="7a176-131">Por fim, o código no interior do **se** bloco dá instruções ao Windows o que fazer com o formulário, depois dos utilizadores selecionar um dia no calendário e, em seguida, clique no **OK** botão ou prima o **Enter** chave.</span><span class="sxs-lookup"><span data-stu-id="7a176-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="7a176-132">Windows PowerShell apresenta a data selecionada para os utilizadores.</span><span class="sxs-lookup"><span data-stu-id="7a176-132">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="7a176-133">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="7a176-133">See Also</span></span>

- [<span data-ttu-id="7a176-134">Hei responsável pelo script Guy: por que razão estes exemplos do PowerShell GUI não funcionam?</span><span class="sxs-lookup"><span data-stu-id="7a176-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="7a176-135">GitHub: WinFormsExampleUpdates de Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="7a176-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="7a176-136">Windows PowerShell sugestão da semana: criar um Seletor de data gráfica</span><span class="sxs-lookup"><span data-stu-id="7a176-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](http://technet.microsoft.com/library/ff730942.aspx)