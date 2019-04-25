---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Caixas de Listagem de Seleção Múltipla
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: a762145dc197ec7e1424b2fbdcef5e7380d13803
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057964"
---
# <a name="multiple-selection-list-boxes"></a>Caixas de listagem de seleção múltipla

Utilize o Windows PowerShell 3.0 e versões posteriores para criar um controle de caixa de lista de seleção múltipla num formulário personalizado do Windows.

## <a name="create-list-box-controls-that-allow-multiple-selections"></a>Criar lista de controles de caixa permitem múltiplas seleções

Copiar e, em seguida, cole o seguinte no ISE do Windows PowerShell e, em seguida, guarde-o como um script do Windows PowerShell (. ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)

$listBox.SelectionMode = 'MultiExtended'

[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')

$listBox.Height = 70
$form.Controls.Add($listBox)
$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

O script começa com o carregamento de duas classes do .NET Framework: **System. Drawing** e **. Windows. Forms**. Em seguida, iniciar uma nova instância da classe .NET Framework **Form**; que fornece um formulário em branco ou controles de janela para o qual pode começar a adicionar.

```powershell
$form = New-Object System.Windows.Forms.Form
```

Depois de criar uma instância da classe Form, atribua valores a três propriedades dessa classe.

- **Text.** Isso se torna o título da janela.

- **Size.** Este é o tamanho do formulário, em pixéis. O script anterior cria um formulário que é de 300 pixels de largura por 200 pixels de altura.

- **StartingPosition.** Esta propriedade opcional é definida como **CenterScreen** no script anterior. Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário for aberto. Definindo a **StartingPosition** ao **CenterScreen**, estiver automaticamente a apresentar o formulário no meio da tela sempre que ele carrega.

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Em seguida, crie uma **OK** botão para seu formulário. Especifique o tamanho e o comportamento do **OK** botão. Neste exemplo, a posição do botão é 120 pixels de limite superior do formulário e 75 pixels da margem esquerda. A altura de botão é 23 pixels, enquanto o comprimento de botão for 75 pixels. O script utiliza os tipos de formulários do Windows predefinidos para determinar os comportamentos de botão.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Da mesma forma, criar um **Cancelar** botão. O **Cancelar** botão é 120 pixels na parte superior, mas como 150 pixels da margem esquerda da janela.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Em seguida, forneça o texto da etiqueta na sua janela que descreve as informações que pretende que os utilizadores forneçam.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

Adicione o controle (neste caso, uma caixa de listagem), que permite que os utilizadores que forneça as informações que descrevi o texto da etiqueta. Existem muitos outros controles, que pode aplicar além de caixas de texto; Para obter mais controles, consulte [Namespacesystem](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) no MSDN.

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

Eis como especificar que pretende permitir que os usuários selecionar diversos valores da lista.

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

Na próxima seção, especifique os valores que pretende que a caixa de listagem a apresentar aos utilizadores.

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

Especifique a altura máxima do controle de caixa de lista.

```powershell
$listBox.Height = 70
```

Adicionar o controle de caixa de lista ao seu formulário e instruir o Windows para abrir o formulário sobre outras janelas e caixas de diálogo quando for aberta.

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

Adicione a seguinte linha de código para exibir o formulário no Windows.

```powershell
$result = $form.ShowDialog()
```

Por fim, o código dentro do **se** bloco instrui o Windows o que fazer com o formulário depois de selecionar uma ou mais opções na caixa de lista de utilizadores e, em seguida, clique no **OK** botão ou prima o **Enter**  chave.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a>Veja Também

- [EI equipe de scripts:  Por que não funcionam nestes exemplos de GUI do PowerShell?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: WinFormsExampleUpdates de Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Sugestão de Windows PowerShell da semana:  Caixas de listagem de seleção múltipla - e muito mais!](https://technet.microsoft.com/library/ff730950.aspx)