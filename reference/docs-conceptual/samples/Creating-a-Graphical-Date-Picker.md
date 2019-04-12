---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Criar um Seletor de Datas Gráfico
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: d3b24af935e781a8a36fc346a6108baaed37b6db
ms.sourcegitcommit: 3f6002e7109373eda31cc65fc84d2600447cb7e9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/11/2019
ms.locfileid: "59506806"
---
# <a name="creating-a-graphical-date-picker"></a>Criar um Seletor de Datas Gráfico

Utilize o Windows PowerShell 3.0 e versões posteriores para criar um formulário com um controle de calendário-estilo de gráfico, que permite aos utilizadores selecionar um dia do mês.

## <a name="create-a-graphical-date-picker-control"></a>Criar um controlo de Seletor de datas gráfico

Copiar e, em seguida, cole o seguinte no ISE do Windows PowerShell e, em seguida, guarde-o como um script do Windows PowerShell (. ps1).

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

O script começa com o carregamento de duas classes do .NET Framework: **System. Drawing** e **. Windows. Forms**.
Em seguida, iniciar uma nova instância da classe .NET Framework **Windows**; que fornece um formulário em branco ou controles de janela para o qual pode começar a adicionar.

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

Este exemplo atribui valores a quatro propriedades dessa classe, utilizando o **propriedade** propriedade e a tabela de hash.

1. **StartPosition**: Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário for aberto.
   Definindo essa propriedade **CenterScreen**, estiver automaticamente a apresentar o formulário no meio da tela sempre que ele carrega.

2. **Tamanho**: Este é o tamanho do formulário, em pixéis.
   O script anterior cria um formulário que é 243 pixels de largura por 230 pixels de altura.

3. **Texto**: Isso se torna o título da janela.

4. **Superior**: Definindo essa propriedade `$true`, pode forçar a janela para abrir sobre outras janelas abertas e caixas de diálogo.

Em seguida, criar e, em seguida, adicionar um controle de calendário no seu formulário.
Neste exemplo, o dia atual não é realçado ou com círculos.
Os utilizadores podem selecionar apenas um dia no calendário de uma só vez.

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

Em seguida, crie uma **OK** botão para seu formulário.
Especifique o tamanho e o comportamento do **OK** botão.
Neste exemplo, a posição do botão é 165 pixels de limite superior do formulário e 38 pixels da margem esquerda.
A altura de botão é 23 pixels, enquanto o comprimento de botão for 75 pixels.
O script utiliza os tipos de formulários do Windows predefinidos para determinar os comportamentos de botão.

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

Da mesma forma, criar um **Cancelar** botão.
O **Cancelar** botão é 165 pixels na parte superior, mas 113 pixels da margem esquerda da janela.

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

Adicione a seguinte linha de código para exibir o formulário no Windows.

```powershell
$result = $form.ShowDialog()
```

Por fim, o código dentro do `if` bloco instrui o Windows o que fazer com o formulário depois dos utilizadores selecionar um dia no calendário e, em seguida, clique no **OK** botão ou prima o **Enter** chave.
Windows PowerShell apresenta a data selecionada para os utilizadores.

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Veja Também

- [EI equipe de scripts:  Por que não funcionam nestes exemplos de GUI do PowerShell?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: WinFormsExampleUpdates de Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Sugestão de Windows PowerShell da semana:  Criar um Seletor de Datas Gráfico](https://technet.microsoft.com/library/ff730942.aspx)