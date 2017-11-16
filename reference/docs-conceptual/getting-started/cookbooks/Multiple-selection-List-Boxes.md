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
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="5c299-103">Caixas de listagem de seleção múltipla</span><span class="sxs-lookup"><span data-stu-id="5c299-103">Multiple-selection List Boxes</span></span>
<span data-ttu-id="5c299-104">Utilize o Windows PowerShell 3.0 e versões posteriores para criar um controlo de caixa de lista de seleção múltipla num formulário personalizado do Windows.</span><span class="sxs-lookup"><span data-stu-id="5c299-104">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="5c299-105">Criar a lista de controlos de caixa que permitem que vários seleções</span><span class="sxs-lookup"><span data-stu-id="5c299-105">Create list box controls that allow multiple selections</span></span>
<span data-ttu-id="5c299-106">Copiar e, em seguida, cole o seguinte no ISE do Windows PowerShell e, em seguida, guarde-o como um script do Windows PowerShell (. ps1).</span><span class="sxs-lookup"><span data-stu-id="5c299-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="5c299-107">O script começa por carregar duas classes de .NET Framework: **Drawing por uma questão** e **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="5c299-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="5c299-108">Em seguida, iniciar uma nova instância da classe de .NET Framework **Form**; que fornece uma forma em branco ou controla a janela para o qual pode começar a adicionar.</span><span class="sxs-lookup"><span data-stu-id="5c299-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="5c299-109">Depois de criar uma instância da classe do formulário, atribua valores a três propriedades desta classe.</span><span class="sxs-lookup"><span data-stu-id="5c299-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="5c299-110">**Texto.**</span><span class="sxs-lookup"><span data-stu-id="5c299-110">**Text.**</span></span> <span data-ttu-id="5c299-111">Isto torna-se o título da janela.</span><span class="sxs-lookup"><span data-stu-id="5c299-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="5c299-112">**Tamanho.**</span><span class="sxs-lookup"><span data-stu-id="5c299-112">**Size.**</span></span> <span data-ttu-id="5c299-113">Este é o tamanho do formulário, em pixels.</span><span class="sxs-lookup"><span data-stu-id="5c299-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="5c299-114">O script anterior cria um formulário que é de 300 pixéis wide por 200 pixels altura.</span><span class="sxs-lookup"><span data-stu-id="5c299-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="5c299-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="5c299-115">**StartingPosition.**</span></span> <span data-ttu-id="5c299-116">Esta propriedade opcional é definida como **CenterScreen** no script anterior.</span><span class="sxs-lookup"><span data-stu-id="5c299-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="5c299-117">Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário é aberto.</span><span class="sxs-lookup"><span data-stu-id="5c299-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="5c299-118">Ao definir o **StartingPosition** para **CenterScreen**, automaticamente estiver a apresentar o formulário no meio do ecrã de cada vez que carrega.</span><span class="sxs-lookup"><span data-stu-id="5c299-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="5c299-119">Em seguida, crie um **OK** botão para o formulário.</span><span class="sxs-lookup"><span data-stu-id="5c299-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="5c299-120">Especifique o tamanho e o comportamento do **OK** botão.</span><span class="sxs-lookup"><span data-stu-id="5c299-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="5c299-121">Neste exemplo, a posição do botão é 120 pixéis do limite superior do formulário e 75 pixéis do limite esquerdo.</span><span class="sxs-lookup"><span data-stu-id="5c299-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="5c299-122">A altura do botão é 23 pixéis, enquanto o comprimento do botão for 75 pixéis.</span><span class="sxs-lookup"><span data-stu-id="5c299-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="5c299-123">O script utiliza tipos de Windows Forms predefinidos para determinar os comportamentos do botão.</span><span class="sxs-lookup"><span data-stu-id="5c299-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="5c299-124">Da mesma forma, crie um **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="5c299-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="5c299-125">O **Cancelar** botão é 120 pixéis da parte superior, mas 150 pixéis do limite esquerdo da janela.</span><span class="sxs-lookup"><span data-stu-id="5c299-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="5c299-126">Em seguida, forneça o texto da etiqueta na sua janela que descreve as informações que pretende que os utilizadores forneçam.</span><span class="sxs-lookup"><span data-stu-id="5c299-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label)
```

<span data-ttu-id="5c299-127">Adicione controlo (neste caso, uma caixa de listagem) que permite que os utilizadores que forneça as informações tiver descritos no texto da etiqueta.</span><span class="sxs-lookup"><span data-stu-id="5c299-127">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="5c299-128">Existem muitos outros controlos que pode aplicar para além das caixas de texto; Para obter mais controlos, consulte [System.Windows.Forms espaço de nomes](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) no MSDN.</span><span class="sxs-lookup"><span data-stu-id="5c299-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```
$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20)
```


<span data-ttu-id="5c299-129">Eis como especificar que pretende permitir que os utilizadores selecionar vários valores da lista.</span><span class="sxs-lookup"><span data-stu-id="5c299-129">Here’s how you specify that you want to allow users to select multiple values from the list.</span></span>

```
$listBox.SelectionMode = "MultiExtended"
```

<span data-ttu-id="5c299-130">Na secção seguinte, especifique os valores que pretende que a caixa de lista para apresentar aos utilizadores.</span><span class="sxs-lookup"><span data-stu-id="5c299-130">In the next section, you specify the values you want the list box to display to users.</span></span>

```
[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")
```

<span data-ttu-id="5c299-131">Especifique a altura máxima do controlo de caixa de lista.</span><span class="sxs-lookup"><span data-stu-id="5c299-131">Specify the maximum height of the list box control.</span></span>

```
$listBox.Height = 70
```

<span data-ttu-id="5c299-132">Adicione o controlo de caixa de lista para o formulário e instruir Windows para abrir o formulário visível outros windows e caixas de diálogo quando for aberta.</span><span class="sxs-lookup"><span data-stu-id="5c299-132">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

<span data-ttu-id="5c299-133">Adicione a seguinte linha de código para apresentar o formulário no Windows.</span><span class="sxs-lookup"><span data-stu-id="5c299-133">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="5c299-134">Por fim, o código no interior do **se** bloco dá instruções ao Windows o que fazer com o formulário, depois dos utilizadores selecionarem uma ou mais opções da caixa de listagem e, em seguida, clique no **OK** botão ou prima o **Enter**  chave.</span><span class="sxs-lookup"><span data-stu-id="5c299-134">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="5c299-135">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5c299-135">See Also</span></span>
- [<span data-ttu-id="5c299-136">Hei responsável pelo script Guy: por que razão estes exemplos do PowerShell GUI não funcionam?</span><span class="sxs-lookup"><span data-stu-id="5c299-136">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="5c299-137">GitHub: WinFormsExampleUpdates de Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="5c299-137">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="5c299-138">Windows PowerShell sugestão da semana: lista de seleção múltipla caixas - e muito mais!</span><span class="sxs-lookup"><span data-stu-id="5c299-138">Windows PowerShell Tip of the Week:  Multi-Select List Boxes - And More!</span></span>](http://technet.microsoft.com/library/ff730950.aspx)

