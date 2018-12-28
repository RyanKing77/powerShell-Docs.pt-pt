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
# <a name="creating-a-graphical-date-picker"></a>Criar um Seletor de Datas Gráfico

Utilize o Windows PowerShell 3.0 e versões posteriores para criar um formulário com um controle de calendário-estilo de gráfico, que permite aos utilizadores selecionar um dia do mês.

## <a name="create-a-graphical-date-picker-control"></a>Criar um controlo de Seletor de datas gráfico

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

O script começa com o carregamento de duas classes do .NET Framework: **System. Drawing** e **. Windows. Forms**. Em seguida, iniciar uma nova instância da classe .NET Framework **Windows**; que fornece um formulário em branco ou controles de janela para o qual pode começar a adicionar.

```powershell
$form = New-Object Windows.Forms.Form
```

Depois de criar uma instância da classe Form, atribua valores a três propriedades dessa classe.

- **Texto.** Isso se torna o título da janela.

- **Tamanho.** Este é o tamanho do formulário, em pixéis. O script anterior cria um formulário que é 243 pixels de largura por 230 pixels de altura.

- **StartingPosition.** Esta propriedade opcional é definida como **CenterScreen** no script anterior. Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário for aberto. Definindo a **StartingPosition** ao **CenterScreen**, estiver automaticamente a apresentar o formulário no meio da tela sempre que ele carrega.

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

Em seguida, criar e, em seguida, adicionar um controle de calendário no seu formulário. Neste exemplo, o dia atual não é realçado ou com círculos. Os utilizadores podem selecionar apenas um dia no calendário de uma só vez.

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Em seguida, crie uma **OK** botão para seu formulário. Especifique o tamanho e o comportamento do **OK** botão. Neste exemplo, a posição do botão é 165 pixels de limite superior do formulário e 38 pixels da margem esquerda. A altura de botão é 23 pixels, enquanto o comprimento de botão for 75 pixels. O script utiliza os tipos de formulários do Windows predefinidos para determinar os comportamentos de botão.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Da mesma forma, criar um **Cancelar** botão. O **Cancelar** botão é 165 pixels na parte superior, mas 113 pixels da margem esquerda da janela.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Definir o **Topmost** propriedade **$true** para forçar a janela para abrir sobre outras janelas abertas e caixas de diálogo.

```powershell
$form.Topmost = $true
```

Adicione a seguinte linha de código para exibir o formulário no Windows.

```powershell
$result = $form.ShowDialog()
```

Por fim, o código dentro do **se** bloco instrui o Windows o que fazer com o formulário depois dos utilizadores selecionar um dia no calendário e, em seguida, clique no **OK** botão ou prima o **Enter** chave. Windows PowerShell apresenta a data selecionada para os utilizadores.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Consulte Também

- [EI equipe de scripts:  Por que não funcionam nestes exemplos de GUI do PowerShell?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: WinFormsExampleUpdates de Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Sugestão de Windows PowerShell da semana:  Criar um Seletor de datas gráfico](https://technet.microsoft.com/library/ff730942.aspx)