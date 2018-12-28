---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEAddOnTool
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: e091f37601c7a4fdaf5deff8c668b18ee7369e74
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405514"
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="1e23b-103">Objeto ISEAddOnTool</span><span class="sxs-lookup"><span data-stu-id="1e23b-103">The ISEAddOnTool Object</span></span>

<span data-ttu-id="1e23b-104">Uma **ISEAddonTool** objeto representa uma ferramenta do suplemento instalado que fornece funcionalidade adicional toWindows ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e23b-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="1e23b-105">Um exemplo é o **comandos** ferramenta que pode ser exibida ao clicar em **vista**, em seguida, **Mostrar suplemento de comando**.</span><span class="sxs-lookup"><span data-stu-id="1e23b-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="1e23b-106">Essa ferramenta, em seguida, está acessível para ao manipular as disponíveis várias **ISEAddOnTool** objetos.</span><span class="sxs-lookup"><span data-stu-id="1e23b-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

<span data-ttu-id="1e23b-107">Cada ferramenta do suplemento pode ser associada com o painel vertical ou horizontal painel.</span><span class="sxs-lookup"><span data-stu-id="1e23b-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="1e23b-108">O painel de vertical é encaixado na borda direita do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e23b-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="1e23b-109">O painel horizontal é encaixado na borda da parte inferior.</span><span class="sxs-lookup"><span data-stu-id="1e23b-109">The horizontal pane is docked to the bottom edge.</span></span>

<span data-ttu-id="1e23b-110">Cada separador do PowerShell no ISE do Windows PowerShell pode ter seu próprio conjunto de ferramentas de suplemento instalado.</span><span class="sxs-lookup"><span data-stu-id="1e23b-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="1e23b-111">Ver [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) e [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) para acessar a coleção de ferramentas disponíveis para o separador atualmente selecionado ou o as mesmas propriedades em qualquer um da **PowerShellTab** objetos na [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) objeto da coleção.</span><span class="sxs-lookup"><span data-stu-id="1e23b-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="1e23b-112">Métodos</span><span class="sxs-lookup"><span data-stu-id="1e23b-112">Methods</span></span>

<span data-ttu-id="1e23b-113">Não há nenhum método do Windows PowerShell ISE específicas disponíveis para objetos dessa classe.</span><span class="sxs-lookup"><span data-stu-id="1e23b-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="1e23b-114">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1e23b-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="1e23b-115">Controlar</span><span class="sxs-lookup"><span data-stu-id="1e23b-115">Control</span></span>

<span data-ttu-id="1e23b-116">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="1e23b-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="1e23b-117">O **controle** propriedade fornece acesso de leitura para muitos dos detalhes da ferramenta do suplemento de comandos.</span><span class="sxs-lookup"><span data-stu-id="1e23b-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher
```

### <a name="isvisible"></a><span data-ttu-id="1e23b-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="1e23b-118">IsVisible</span></span>

<span data-ttu-id="1e23b-119">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="1e23b-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="1e23b-120">A propriedade booleana que indica se a ferramenta do suplemento é atualmente visível no seu painel atribuído.</span><span class="sxs-lookup"><span data-stu-id="1e23b-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="1e23b-121">Se estiver visível, pode definir o **IsVisible** propriedade **$false** para ocultar a ferramenta ou definir o **IsVisible** propriedade para **$true** para tornar uma ferramenta do suplemento visível no respetivo separador do PowerShell. Tenha em atenção que depois de uma ferramenta de suplementos está oculta, já não é acessível através da **CurrentVisibleHorizontalTool** ou **CurrentVisibleVerticalTool** objetos e, portanto, não pode se tornar visível através da utilização Esta propriedade nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="1e23b-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a><span data-ttu-id="1e23b-122">Nome</span><span class="sxs-lookup"><span data-stu-id="1e23b-122">Name</span></span>

<span data-ttu-id="1e23b-123">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="1e23b-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="1e23b-124">A propriedade só de leitura que obtém o nome da ferramenta do suplemento.</span><span class="sxs-lookup"><span data-stu-id="1e23b-124">The read-only property that gets the name of the add-on tool.</span></span>

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a><span data-ttu-id="1e23b-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="1e23b-125">See Also</span></span>

- [<span data-ttu-id="1e23b-126">Objeto ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="1e23b-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="1e23b-127">Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="1e23b-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="1e23b-128">Hierarquia do Modelo de Objeto ISE</span><span class="sxs-lookup"><span data-stu-id="1e23b-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)