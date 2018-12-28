---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Criar um Seletor de Datas Gráfico
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404668"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="81c25-103">Criar um Seletor de Datas Gráfico</span><span class="sxs-lookup"><span data-stu-id="81c25-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="81c25-104">Utilize o Windows PowerShell 3.0 e versões posteriores para criar um formulário com um controle de calendário-estilo de gráfico, que permite aos utilizadores selecionar um dia do mês.</span><span class="sxs-lookup"><span data-stu-id="81c25-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="81c25-105">Criar um controlo de Seletor de datas gráfico</span><span class="sxs-lookup"><span data-stu-id="81c25-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="81c25-106">Copiar e, em seguida, cole o seguinte no ISE do Windows PowerShell e, em seguida, guarde-o como um script do Windows PowerShell (. ps1).</span><span class="sxs-lookup"><span data-stu-id="81c25-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="81c25-107">O script começa com o carregamento de duas classes do .NET Framework: **System. Drawing** e **. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="81c25-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="81c25-108">Em seguida, iniciar uma nova instância da classe .NET Framework **Windows**; que fornece um formulário em branco ou controles de janela para o qual pode começar a adicionar.</span><span class="sxs-lookup"><span data-stu-id="81c25-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="81c25-109">Depois de criar uma instância da classe Form, atribua valores a três propriedades dessa classe.</span><span class="sxs-lookup"><span data-stu-id="81c25-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="81c25-110">**Texto.**</span><span class="sxs-lookup"><span data-stu-id="81c25-110">**Text.**</span></span> <span data-ttu-id="81c25-111">Isso se torna o título da janela.</span><span class="sxs-lookup"><span data-stu-id="81c25-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="81c25-112">**Tamanho.**</span><span class="sxs-lookup"><span data-stu-id="81c25-112">**Size.**</span></span> <span data-ttu-id="81c25-113">Este é o tamanho do formulário, em pixéis.</span><span class="sxs-lookup"><span data-stu-id="81c25-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="81c25-114">O script anterior cria um formulário que é 243 pixels de largura por 230 pixels de altura.</span><span class="sxs-lookup"><span data-stu-id="81c25-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="81c25-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="81c25-115">**StartingPosition.**</span></span> <span data-ttu-id="81c25-116">Esta propriedade opcional é definida como **CenterScreen** no script anterior.</span><span class="sxs-lookup"><span data-stu-id="81c25-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="81c25-117">Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário for aberto.</span><span class="sxs-lookup"><span data-stu-id="81c25-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="81c25-118">Definindo a **StartingPosition** ao **CenterScreen**, estiver automaticamente a apresentar o formulário no meio da tela sempre que ele carrega.</span><span class="sxs-lookup"><span data-stu-id="81c25-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="81c25-119">Em seguida, criar e, em seguida, adicionar um controle de calendário no seu formulário.</span><span class="sxs-lookup"><span data-stu-id="81c25-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="81c25-120">Neste exemplo, o dia atual não é realçado ou com círculos.</span><span class="sxs-lookup"><span data-stu-id="81c25-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="81c25-121">Os utilizadores podem selecionar apenas um dia no calendário de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="81c25-121">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="81c25-122">Em seguida, crie uma **OK** botão para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="81c25-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="81c25-123">Especifique o tamanho e o comportamento do **OK** botão.</span><span class="sxs-lookup"><span data-stu-id="81c25-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="81c25-124">Neste exemplo, a posição do botão é 165 pixels de limite superior do formulário e 38 pixels da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="81c25-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="81c25-125">A altura de botão é 23 pixels, enquanto o comprimento de botão for 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="81c25-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="81c25-126">O script utiliza os tipos de formulários do Windows predefinidos para determinar os comportamentos de botão.</span><span class="sxs-lookup"><span data-stu-id="81c25-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="81c25-127">Da mesma forma, criar um **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="81c25-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="81c25-128">O **Cancelar** botão é 165 pixels na parte superior, mas 113 pixels da margem esquerda da janela.</span><span class="sxs-lookup"><span data-stu-id="81c25-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="81c25-129">Definir o **Topmost** propriedade **$true** para forçar a janela para abrir sobre outras janelas abertas e caixas de diálogo.</span><span class="sxs-lookup"><span data-stu-id="81c25-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="81c25-130">Adicione a seguinte linha de código para exibir o formulário no Windows.</span><span class="sxs-lookup"><span data-stu-id="81c25-130">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="81c25-131">Por fim, o código dentro do **se** bloco instrui o Windows o que fazer com o formulário depois dos utilizadores selecionar um dia no calendário e, em seguida, clique no **OK** botão ou prima o **Enter** chave.</span><span class="sxs-lookup"><span data-stu-id="81c25-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="81c25-132">Windows PowerShell apresenta a data selecionada para os utilizadores.</span><span class="sxs-lookup"><span data-stu-id="81c25-132">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="81c25-133">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="81c25-133">See Also</span></span>

- [<span data-ttu-id="81c25-134">EI equipe de scripts:  Por que não funcionam nestes exemplos de GUI do PowerShell?</span><span class="sxs-lookup"><span data-stu-id="81c25-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="81c25-135">GitHub: WinFormsExampleUpdates de Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="81c25-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="81c25-136">Sugestão de Windows PowerShell da semana:  Criar um Seletor de datas gráfico</span><span class="sxs-lookup"><span data-stu-id="81c25-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)