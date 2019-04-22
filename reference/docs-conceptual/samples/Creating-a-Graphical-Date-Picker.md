---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Criar um Seletor de Datas Gráfico
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: d3b24af935e781a8a36fc346a6108baaed37b6db
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59506806"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="dc94c-103">Criar um Seletor de Datas Gráfico</span><span class="sxs-lookup"><span data-stu-id="dc94c-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="dc94c-104">Utilize o Windows PowerShell 3.0 e versões posteriores para criar um formulário com um controle de calendário-estilo de gráfico, que permite aos utilizadores selecionar um dia do mês.</span><span class="sxs-lookup"><span data-stu-id="dc94c-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="dc94c-105">Criar um controlo de Seletor de datas gráfico</span><span class="sxs-lookup"><span data-stu-id="dc94c-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="dc94c-106">Copiar e, em seguida, cole o seguinte no ISE do Windows PowerShell e, em seguida, guarde-o como um script do Windows PowerShell (. ps1).</span><span class="sxs-lookup"><span data-stu-id="dc94c-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="dc94c-107">O script começa com o carregamento de duas classes do .NET Framework: **System. Drawing** e **. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="dc94c-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span>
<span data-ttu-id="dc94c-108">Em seguida, iniciar uma nova instância da classe .NET Framework **Windows**; que fornece um formulário em branco ou controles de janela para o qual pode começar a adicionar.</span><span class="sxs-lookup"><span data-stu-id="dc94c-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="dc94c-109">Este exemplo atribui valores a quatro propriedades dessa classe, utilizando o **propriedade** propriedade e a tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="dc94c-109">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="dc94c-110">**StartPosition**: Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário for aberto.</span><span class="sxs-lookup"><span data-stu-id="dc94c-110">**StartPosition**: If you don’t add this property, Windows selects a location when the form is opened.</span></span>
   <span data-ttu-id="dc94c-111">Definindo essa propriedade **CenterScreen**, estiver automaticamente a apresentar o formulário no meio da tela sempre que ele carrega.</span><span class="sxs-lookup"><span data-stu-id="dc94c-111">By setting this property to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="dc94c-112">**Tamanho**: Este é o tamanho do formulário, em pixéis.</span><span class="sxs-lookup"><span data-stu-id="dc94c-112">**Size**: This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="dc94c-113">O script anterior cria um formulário que é 243 pixels de largura por 230 pixels de altura.</span><span class="sxs-lookup"><span data-stu-id="dc94c-113">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="dc94c-114">**Texto**: Isso se torna o título da janela.</span><span class="sxs-lookup"><span data-stu-id="dc94c-114">**Text**: This becomes the title of the window.</span></span>

4. <span data-ttu-id="dc94c-115">**Superior**: Definindo essa propriedade `$true`, pode forçar a janela para abrir sobre outras janelas abertas e caixas de diálogo.</span><span class="sxs-lookup"><span data-stu-id="dc94c-115">**Topmost**: By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="dc94c-116">Em seguida, criar e, em seguida, adicionar um controle de calendário no seu formulário.</span><span class="sxs-lookup"><span data-stu-id="dc94c-116">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="dc94c-117">Neste exemplo, o dia atual não é realçado ou com círculos.</span><span class="sxs-lookup"><span data-stu-id="dc94c-117">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="dc94c-118">Os utilizadores podem selecionar apenas um dia no calendário de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="dc94c-118">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="dc94c-119">Em seguida, crie uma **OK** botão para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="dc94c-119">Next, create an **OK** button for your form.</span></span>
<span data-ttu-id="dc94c-120">Especifique o tamanho e o comportamento do **OK** botão.</span><span class="sxs-lookup"><span data-stu-id="dc94c-120">Specify the size and behavior of the **OK** button.</span></span>
<span data-ttu-id="dc94c-121">Neste exemplo, a posição do botão é 165 pixels de limite superior do formulário e 38 pixels da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="dc94c-121">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span>
<span data-ttu-id="dc94c-122">A altura de botão é 23 pixels, enquanto o comprimento de botão for 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="dc94c-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span>
<span data-ttu-id="dc94c-123">O script utiliza os tipos de formulários do Windows predefinidos para determinar os comportamentos de botão.</span><span class="sxs-lookup"><span data-stu-id="dc94c-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="dc94c-124">Da mesma forma, criar um **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="dc94c-124">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="dc94c-125">O **Cancelar** botão é 165 pixels na parte superior, mas 113 pixels da margem esquerda da janela.</span><span class="sxs-lookup"><span data-stu-id="dc94c-125">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="dc94c-126">Adicione a seguinte linha de código para exibir o formulário no Windows.</span><span class="sxs-lookup"><span data-stu-id="dc94c-126">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="dc94c-127">Por fim, o código dentro do `if` bloco instrui o Windows o que fazer com o formulário depois dos utilizadores selecionar um dia no calendário e, em seguida, clique no **OK** botão ou prima o **Enter** chave.</span><span class="sxs-lookup"><span data-stu-id="dc94c-127">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span>
<span data-ttu-id="dc94c-128">Windows PowerShell apresenta a data selecionada para os utilizadores.</span><span class="sxs-lookup"><span data-stu-id="dc94c-128">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="dc94c-129">Veja Também</span><span class="sxs-lookup"><span data-stu-id="dc94c-129">See Also</span></span>

- [<span data-ttu-id="dc94c-130">EI equipe de scripts:  Por que não funcionam nestes exemplos de GUI do PowerShell?</span><span class="sxs-lookup"><span data-stu-id="dc94c-130">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="dc94c-131">GitHub: WinFormsExampleUpdates de Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="dc94c-131">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="dc94c-132">Sugestão de Windows PowerShell da semana:  Criar um Seletor de datas gráfico</span><span class="sxs-lookup"><span data-stu-id="dc94c-132">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)