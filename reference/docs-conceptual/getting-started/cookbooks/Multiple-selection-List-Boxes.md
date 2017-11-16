---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Caixas de listagem de selecção múltipla"
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: 122014888bc5cf93c1c709b9d534d572037f5ffe
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="multiple-selection-list-boxes"></a>Caixas de listagem de seleção múltipla
Utilize o Windows PowerShell 3.0 e versões posteriores para criar um controlo de caixa de lista de seleção múltipla num formulário personalizado do Windows.

## <a name="create-list-box-controls-that-allow-multiple-selections"></a>Criar a lista de controlos de caixa que permitem que vários seleções
Copiar e, em seguida, cole o seguinte no ISE do Windows PowerShell e, em seguida, guarde-o como um script do Windows PowerShell (. ps1).

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Data Entry Form"
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
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 

$listBox.SelectionMode = "MultiExtended"

[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")

$listBox.Height = 70
$form.Controls.Add($listBox) 
$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

O script começa por carregar duas classes de .NET Framework: **Drawing por uma questão** e **System.Windows.Forms**. Em seguida, iniciar uma nova instância da classe de .NET Framework **Form**; que fornece uma forma em branco ou controla a janela para o qual pode começar a adicionar.

```
$form = New-Object System.Windows.Forms.Form
```

Depois de criar uma instância da classe do formulário, atribua valores a três propriedades desta classe.

- **Texto.** Isto torna-se o título da janela.

- **Tamanho.** Este é o tamanho do formulário, em pixels. O script anterior cria um formulário que é de 300 pixéis wide por 200 pixels altura.

- **StartingPosition.** Esta propriedade opcional é definida como **CenterScreen** no script anterior. Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário é aberto. Ao definir o **StartingPosition** para **CenterScreen**, automaticamente estiver a apresentar o formulário no meio do ecrã de cada vez que carrega.

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

Em seguida, crie um **OK** botão para o formulário. Especifique o tamanho e o comportamento do **OK** botão. Neste exemplo, a posição do botão é 120 pixéis do limite superior do formulário e 75 pixéis do limite esquerdo. A altura do botão é 23 pixéis, enquanto o comprimento do botão for 75 pixéis. O script utiliza tipos de Windows Forms predefinidos para determinar os comportamentos do botão.

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
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

Em seguida, forneça o texto da etiqueta na sua janela que descreve as informações que pretende que os utilizadores forneçam.

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label)
```

Adicione controlo (neste caso, uma caixa de listagem) que permite que os utilizadores que forneça as informações tiver descritos no texto da etiqueta. Existem muitos outros controlos que pode aplicar para além das caixas de texto; Para obter mais controlos, consulte [System.Windows.Forms espaço de nomes](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) no MSDN.

```
$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20)
```


Eis como especificar que pretende permitir que os utilizadores selecionar vários valores da lista.

```
$listBox.SelectionMode = "MultiExtended"
```

Na secção seguinte, especifique os valores que pretende que a caixa de lista para apresentar aos utilizadores.

```
[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")
```

Especifique a altura máxima do controlo de caixa de lista.

```
$listBox.Height = 70
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

Por fim, o código no interior do **se** bloco dá instruções ao Windows o que fazer com o formulário, depois dos utilizadores selecionarem uma ou mais opções da caixa de listagem e, em seguida, clique no **OK** botão ou prima o **Enter**  chave.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a>Consulte Também
- [Hei responsável pelo script Guy: por que razão estes exemplos do PowerShell GUI não funcionam?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: WinFormsExampleUpdates de Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell sugestão da semana: lista de seleção múltipla caixas - e muito mais!](http://technet.microsoft.com/library/ff730950.aspx)

