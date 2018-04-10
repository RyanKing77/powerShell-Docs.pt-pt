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
---
# <a name="creating-a-graphical-date-picker"></a>Criar um Seletor de Datas Gráfico

Utilize o Windows PowerShell 3.0 e versões posteriores para criar um formulário com um controlo de calendário estilo gráfica, que permite aos utilizadores selecionar um dia do mês.

## <a name="create-a-graphical-date-picker-control"></a>Criar um controlo de selecionador de data gráfica

Copiar e, em seguida, cole o seguinte no ISE do Windows PowerShell e, em seguida, guarde-o como um script do Windows PowerShell (. ps1).

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

O script começa por carregar duas classes de .NET Framework: **Drawing por uma questão** e **System.Windows.Forms**. Em seguida, iniciar uma nova instância da classe de .NET Framework **Windows.Forms.Form**; que fornece uma forma em branco ou controla a janela para o qual pode começar a adicionar.

```powershell
$form = New-Object Windows.Forms.Form
```

Depois de criar uma instância da classe do formulário, atribua valores a três propriedades desta classe.

- **Texto.** Isto torna-se o título da janela.

- **Tamanho.** Este é o tamanho do formulário, em pixels. O script anterior cria um formulário que é 243 pixéis wide por 230 pixels altura.

- **StartingPosition.** Esta propriedade opcional é definida como **CenterScreen** no script anterior. Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário é aberto. Ao definir o **StartingPosition** para **CenterScreen**, automaticamente estiver a apresentar o formulário no meio do ecrã de cada vez que carrega.

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

Em seguida, criar e, em seguida, adicionar um controlo de calendário do formulário. Neste exemplo, o dia atual não realçado ou não está dentro de um círculo. Os utilizadores podem selecionar apenas um dia no calendário em simultâneo.

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Em seguida, crie um **OK** botão para o formulário. Especifique o tamanho e o comportamento do **OK** botão. Neste exemplo, a posição do botão é 165 pixels limite superior do formulário e 38 pixéis do limite esquerdo. A altura do botão é 23 pixéis, enquanto o comprimento do botão for 75 pixéis. O script utiliza tipos de Windows Forms predefinidos para determinar os comportamentos do botão.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Da mesma forma, crie um **Cancelar** botão. O **Cancelar** botão está 165 pixels da parte superior, mas 113 pixéis do limite esquerdo da janela.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Definir o **Topmost** propriedade **$true** para forçar a janela para o abrir visível outros windows abertas e caixas de diálogo.

```powershell
$form.Topmost = $true
```

Adicione a seguinte linha de código para apresentar o formulário no Windows.

```powershell
$result = $form.ShowDialog()
```

Por fim, o código no interior do **se** bloco dá instruções ao Windows o que fazer com o formulário, depois dos utilizadores selecionar um dia no calendário e, em seguida, clique no **OK** botão ou prima o **Enter** chave. Windows PowerShell apresenta a data selecionada para os utilizadores.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Consulte Também

- [Hei responsável pelo script Guy: por que razão estes exemplos do PowerShell GUI não funcionam?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: WinFormsExampleUpdates de Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell sugestão da semana: criar um Seletor de data gráfica](http://technet.microsoft.com/library/ff730942.aspx)