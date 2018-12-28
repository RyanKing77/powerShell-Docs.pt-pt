---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Criar uma Caixa de Entrada Personalizada
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 2d04ad6df65cdb4ff13d136dea47bbba6a01f3a2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404704"
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="228df-103">Criar uma Caixa de Entrada Personalizada</span><span class="sxs-lookup"><span data-stu-id="228df-103">Creating a Custom Input Box</span></span>

<span data-ttu-id="228df-104">Script de uma caixa de entrada personalizada gráfica usando recursos de criação de formulário do Microsoft .NET Framework no Windows PowerShell 3.0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="228df-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="228df-105">Criar uma caixa de entrada personalizada, gráfica</span><span class="sxs-lookup"><span data-stu-id="228df-105">Create a custom, graphical input box</span></span>

<span data-ttu-id="228df-106">Copiar e, em seguida, cole o seguinte no ISE do Windows PowerShell e, em seguida, guarde-o como um script do Windows PowerShell (. ps1).</span><span class="sxs-lookup"><span data-stu-id="228df-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)

$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)

$form.Topmost = $true

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

<span data-ttu-id="228df-107">O script começa com o carregamento de duas classes do .NET Framework: **System. Drawing** e **. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="228df-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="228df-108">Em seguida, iniciar uma nova instância da classe .NET Framework **Form**; que fornece um formulário em branco ou controles de janela para o qual pode começar a adicionar.</span><span class="sxs-lookup"><span data-stu-id="228df-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="228df-109">Depois de criar uma instância da classe Form, atribua valores a três propriedades dessa classe.</span><span class="sxs-lookup"><span data-stu-id="228df-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="228df-110">**Texto.**</span><span class="sxs-lookup"><span data-stu-id="228df-110">**Text.**</span></span> <span data-ttu-id="228df-111">Isso se torna o título da janela.</span><span class="sxs-lookup"><span data-stu-id="228df-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="228df-112">**Tamanho.**</span><span class="sxs-lookup"><span data-stu-id="228df-112">**Size.**</span></span> <span data-ttu-id="228df-113">Este é o tamanho do formulário, em pixéis.</span><span class="sxs-lookup"><span data-stu-id="228df-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="228df-114">O script anterior cria um formulário que é de 300 pixels de largura por 200 pixels de altura.</span><span class="sxs-lookup"><span data-stu-id="228df-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="228df-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="228df-115">**StartingPosition.**</span></span> <span data-ttu-id="228df-116">Esta propriedade opcional é definida como **CenterScreen** no script anterior.</span><span class="sxs-lookup"><span data-stu-id="228df-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="228df-117">Se não adicionar esta propriedade, o Windows seleciona uma localização quando o formulário for aberto.</span><span class="sxs-lookup"><span data-stu-id="228df-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="228df-118">Definindo a **StartingPosition** ao **CenterScreen**, estiver automaticamente a apresentar o formulário no meio da tela sempre que ele carrega.</span><span class="sxs-lookup"><span data-stu-id="228df-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="228df-119">Em seguida, crie uma **OK** botão para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="228df-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="228df-120">Especifique o tamanho e o comportamento do **OK** botão.</span><span class="sxs-lookup"><span data-stu-id="228df-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="228df-121">Neste exemplo, a posição do botão é 120 pixels de limite superior do formulário e 75 pixels da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="228df-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="228df-122">A altura de botão é 23 pixels, enquanto o comprimento de botão for 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="228df-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="228df-123">O script utiliza os tipos de formulários do Windows predefinidos para determinar os comportamentos de botão.</span><span class="sxs-lookup"><span data-stu-id="228df-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="228df-124">Da mesma forma, criar um **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="228df-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="228df-125">O **Cancelar** botão é 120 pixels na parte superior, mas como 150 pixels da margem esquerda da janela.</span><span class="sxs-lookup"><span data-stu-id="228df-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="228df-126">Em seguida, forneça o texto da etiqueta na sua janela que descreve as informações que pretende que os utilizadores forneçam.</span><span class="sxs-lookup"><span data-stu-id="228df-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="228df-127">Adicione o controle (neste caso, uma caixa de texto) que permite que os utilizadores que forneça as informações que descrevi o texto da etiqueta.</span><span class="sxs-lookup"><span data-stu-id="228df-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="228df-128">Existem muitos outros controles, que pode aplicar além de caixas de texto; Para obter mais controles, consulte [Namespacesystem](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) no MSDN.</span><span class="sxs-lookup"><span data-stu-id="228df-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="228df-129">Definir o **Topmost** propriedade **$true** para forçar a janela para abrir sobre outras janelas abertas e caixas de diálogo.</span><span class="sxs-lookup"><span data-stu-id="228df-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="228df-130">Em seguida, adicione esta linha de código para ativar o formulário e defina o foco para a caixa de texto que criou.</span><span class="sxs-lookup"><span data-stu-id="228df-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="228df-131">Adicione a seguinte linha de código para exibir o formulário no Windows.</span><span class="sxs-lookup"><span data-stu-id="228df-131">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="228df-132">Por fim, o código dentro do **se** bloco instrui o Windows o que fazer com o formulário depois dos utilizadores fornecem o texto na caixa de texto e, em seguida, clique no **OK** botão ou prima o **Enter** chave.</span><span class="sxs-lookup"><span data-stu-id="228df-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="228df-133">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="228df-133">See Also</span></span>

- [<span data-ttu-id="228df-134">EI equipe de scripts:  Por que não funcionam nestes exemplos de GUI do PowerShell?</span><span class="sxs-lookup"><span data-stu-id="228df-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="228df-135">GitHub: WinFormsExampleUpdates de Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="228df-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="228df-136">Sugestão de Windows PowerShell da semana:  Criar uma caixa de entrada personalizada</span><span class="sxs-lookup"><span data-stu-id="228df-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](https://technet.microsoft.com/library/ff730941.aspx)