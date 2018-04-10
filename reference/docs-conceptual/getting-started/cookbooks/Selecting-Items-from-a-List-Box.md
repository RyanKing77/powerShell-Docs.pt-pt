---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Selecionar Itens numa Caixa de Listagem
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: 6ff6bff8f6ce4e9236d7877c4cca24a10932cbe0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="30e03-103">Selecionar Itens numa Caixa de Listagem</span><span class="sxs-lookup"><span data-stu-id="30e03-103">Selecting Items from a List Box</span></span>

<span data-ttu-id="30e03-104">Utilize o Windows PowerShell 3.0 e versões posteriores para criar uma caixa de diálogo que permite aos utilizadores selecionar itens a partir de um controlo de caixa de lista.</span><span class="sxs-lookup"><span data-stu-id="30e03-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="30e03-105">Criar um controlo de caixa de lista e selecionar itens a partir do mesmo</span><span class="sxs-lookup"><span data-stu-id="30e03-105">Create a list box control, and select items from it</span></span>

<span data-ttu-id="30e03-106">Copiar e, em seguida, cole o seguinte no ISE do Windows PowerShell e, em seguida, guarde-o como um script do Windows PowerShell (. ps1).</span><span class="sxs-lookup"><span data-stu-id="30e03-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
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
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80

[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')

$form.Controls.Add($listBox)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

<span data-ttu-id="30e03-107">O script começa por carregar duas classes de .NET Framework: **Drawing por uma questão** e **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="30e03-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="30e03-108">Em seguida, iniciar uma nova instância da classe de .NET Framework **Form**; que fornece uma forma em branco ou controla a janela para o qual pode começar a adicionar.</span><span class="sxs-lookup"><span data-stu-id="30e03-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="30e03-109">Depois de criar uma instância da classe do formulário, atribua valores a três propriedades desta classe.</span><span class="sxs-lookup"><span data-stu-id="30e03-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="30e03-110">**Texto.**</span><span class="sxs-lookup"><span data-stu-id="30e03-110">**Text.**</span></span> <span data-ttu-id="30e03-111">Isto torna-se o título da janela.</span><span class="sxs-lookup"><span data-stu-id="30e03-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="30e03-112">**Tamanho.**</span><span class="sxs-lookup"><span data-stu-id="30e03-112">**Size.**</span></span> <span data-ttu-id="30e03-113">Este é o tamanho do formulário, em pixels.</span><span class="sxs-lookup"><span data-stu-id="30e03-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="30e03-114">O script anterior cria um formulário que é de 300 pixéis wide por 200 pixels altura.</span><span class="sxs-lookup"><span data-stu-id="30e03-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="30e03-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="30e03-115">**StartingPosition.**</span></span> <span data-ttu-id="30e03-116">Esta propriedade opcional é definida como **CenterScreen** no script anterior.</span><span class="sxs-lookup"><span data-stu-id="30e03-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="30e03-117">Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário é aberto.</span><span class="sxs-lookup"><span data-stu-id="30e03-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="30e03-118">Ao definir o **StartingPosition** para **CenterScreen**, automaticamente estiver a apresentar o formulário no meio do ecrã de cada vez que carrega.</span><span class="sxs-lookup"><span data-stu-id="30e03-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="30e03-119">Em seguida, crie um **OK** botão para o formulário.</span><span class="sxs-lookup"><span data-stu-id="30e03-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="30e03-120">Especifique o tamanho e o comportamento do **OK** botão.</span><span class="sxs-lookup"><span data-stu-id="30e03-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="30e03-121">Neste exemplo, a posição do botão é 120 pixéis do limite superior do formulário e 75 pixéis do limite esquerdo.</span><span class="sxs-lookup"><span data-stu-id="30e03-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="30e03-122">A altura do botão é 23 pixéis, enquanto o comprimento do botão for 75 pixéis.</span><span class="sxs-lookup"><span data-stu-id="30e03-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="30e03-123">O script utiliza tipos de Windows Forms predefinidos para determinar os comportamentos do botão.</span><span class="sxs-lookup"><span data-stu-id="30e03-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="30e03-124">Da mesma forma, crie um **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="30e03-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="30e03-125">O **Cancelar** botão é 120 pixéis da parte superior, mas 150 pixéis do limite esquerdo da janela.</span><span class="sxs-lookup"><span data-stu-id="30e03-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="30e03-126">Em seguida, forneça o texto da etiqueta na sua janela que descreve as informações que pretende que os utilizadores forneçam.</span><span class="sxs-lookup"><span data-stu-id="30e03-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="30e03-127">Neste caso, pretende que os utilizadores para selecionar um computador.</span><span class="sxs-lookup"><span data-stu-id="30e03-127">In this case, you want users to select a computer.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

<span data-ttu-id="30e03-128">Adicione controlo (neste caso, uma caixa de listagem) que permite que os utilizadores que forneça as informações tiver descritos no texto da etiqueta.</span><span class="sxs-lookup"><span data-stu-id="30e03-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="30e03-129">Existem muitos outros controlos que pode aplicar para além das caixas de listagem Para obter mais controlos, consulte [System.Windows.Forms espaço de nomes](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) no MSDN.</span><span class="sxs-lookup"><span data-stu-id="30e03-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

<span data-ttu-id="30e03-130">Na secção seguinte, especifique os valores que pretende que a caixa de lista para apresentar aos utilizadores.</span><span class="sxs-lookup"><span data-stu-id="30e03-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="30e03-131">A caixa de listagem criada por este script permite a seleção de apenas um.</span><span class="sxs-lookup"><span data-stu-id="30e03-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="30e03-132">Para criar um controlo de caixa de lista que permite as seleções múltiplas, especifique um valor para o **SelectionMode** propriedade, de forma semelhante ao seguinte: `$listBox.SelectionMode = 'MultiExtended'`.</span><span class="sxs-lookup"><span data-stu-id="30e03-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following:  `$listBox.SelectionMode = 'MultiExtended'`.</span></span> <span data-ttu-id="30e03-133">Para obter mais informações, consulte [caixas de listagem de seleção múltipla](Multiple-selection-List-Boxes.md).</span><span class="sxs-lookup"><span data-stu-id="30e03-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

<span data-ttu-id="30e03-134">Adicione o controlo de caixa de lista para o formulário e instruir Windows para abrir o formulário visível outros windows e caixas de diálogo quando for aberta.</span><span class="sxs-lookup"><span data-stu-id="30e03-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="30e03-135">Adicione a seguinte linha de código para apresentar o formulário no Windows.</span><span class="sxs-lookup"><span data-stu-id="30e03-135">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="30e03-136">Por fim, o código no interior do **se** bloco dá instruções ao Windows o que fazer com o formulário, depois dos utilizadores selecionarem uma opção na caixa de listagem e, em seguida, clique no **OK** botão ou prima o **Enter**chave.</span><span class="sxs-lookup"><span data-stu-id="30e03-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="30e03-137">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="30e03-137">See Also</span></span>

- [<span data-ttu-id="30e03-138">Hei responsável pelo script Guy: por que razão estes exemplos do PowerShell GUI não funcionam?</span><span class="sxs-lookup"><span data-stu-id="30e03-138">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="30e03-139">GitHub: WinFormsExampleUpdates de Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="30e03-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="30e03-140">Windows PowerShell sugestão da semana: selecionar itens a partir de uma caixa de listagem</span><span class="sxs-lookup"><span data-stu-id="30e03-140">Windows PowerShell Tip of the Week:  Selecting Items from a List Box</span></span>](http://technet.microsoft.com/library/ff730949.aspx)