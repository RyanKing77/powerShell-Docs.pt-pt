---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Selecionar itens a partir de uma caixa de listagem
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: 5b41ebfb193062a17abcc6ad6ddf1a2d9241a39e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="selecting-items-from-a-list-box"></a>Selecionar itens a partir de uma caixa de listagem
Utilize o Windows PowerShell 3.0 e versões posteriores para criar uma caixa de diálogo que permite aos utilizadores selecionar itens a partir de um controlo de caixa de lista.

## <a name="create-a-list-box-control-and-select-items-from-it"></a>Criar um controlo de caixa de lista e selecionar itens a partir do mesmo
Copiar e, em seguida, cole o seguinte no ISE do Windows PowerShell e, em seguida, guarde-o como um script do Windows PowerShell (. ps1).

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80

[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")

$form.Controls.Add($listBox) 

$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

O script começa por carregar duas classes de .NET Framework: **Drawing por uma questão** e **System.Windows.Forms**. Em seguida, iniciar uma nova instância da classe de .NET Framework **Form**; que fornece uma forma em branco ou controla a janela para o qual pode começar a adicionar.

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

Depois de criar uma instância da classe do formulário, atribua valores a três propriedades desta classe.

- **Texto.** Isto torna-se o título da janela.

- **Tamanho.** Este é o tamanho do formulário, em pixels. O script anterior cria um formulário que é de 300 pixéis wide por 200 pixels altura.

- **StartingPosition.** Esta propriedade opcional é definida como **CenterScreen** no script anterior. Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário é aberto. Ao definir o **StartingPosition** para **CenterScreen**, automaticamente estiver a apresentar o formulário no meio do ecrã de cada vez que carrega.

```
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

Em seguida, crie um **OK** botão para o formulário. Especifique o tamanho e o comportamento do **OK** botão. Neste exemplo, a posição do botão é 120 pixéis do limite superior do formulário e 75 pixéis do limite esquerdo. A altura do botão é 23 pixéis, enquanto o comprimento do botão for 75 pixéis. O script utiliza tipos de Windows Forms predefinidos para determinar os comportamentos do botão.

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Da mesma forma, crie um **Cancelar** botão. O **Cancelar** botão é 120 pixéis da parte superior, mas 150 pixéis do limite esquerdo da janela.

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Em seguida, forneça o texto da etiqueta na sua janela que descreve as informações que pretende que os utilizadores forneçam. Neste caso, pretende que os utilizadores para selecionar um computador.

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label)
```

Adicione controlo (neste caso, uma caixa de listagem) que permite que os utilizadores que forneça as informações tiver descritos no texto da etiqueta. Existem muitos outros controlos que pode aplicar para além das caixas de listagem Para obter mais controlos, consulte [System.Windows.Forms espaço de nomes](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) no MSDN.

```
$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80
```

Na secção seguinte, especifique os valores que pretende que a caixa de lista para apresentar aos utilizadores.

> [!NOTE]
> A caixa de listagem criada por este script permite a seleção de apenas um. Para criar um controlo de caixa de lista que permite as seleções múltiplas, especifique um valor para o **SelectionMode** propriedade, de forma semelhante ao seguinte: `$listBox.SelectionMode = "MultiExtended"`. Para obter mais informações, consulte [caixas de listagem de seleção múltipla](Multiple-selection-List-Boxes.md).

```
[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")
```

Adicione o controlo de caixa de lista para o formulário e instruir Windows para abrir o formulário visível outros windows e caixas de diálogo quando for aberta.

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

Adicione a seguinte linha de código para apresentar o formulário no Windows.

```
$result = $form.ShowDialog()
```

Por fim, o código no interior do **se** bloco dá instruções ao Windows o que fazer com o formulário, depois dos utilizadores selecionarem uma opção na caixa de listagem e, em seguida, clique no **OK** botão ou prima o **Enter**chave.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a>Consulte Também
- [Hei responsável pelo script Guy: por que razão estes exemplos do PowerShell GUI não funcionam?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: WinFormsExampleUpdates de Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell sugestão da semana: selecionar itens a partir de uma caixa de listagem](http://technet.microsoft.com/library/ff730949.aspx)

