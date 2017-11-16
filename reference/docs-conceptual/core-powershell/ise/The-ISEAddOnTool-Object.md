---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: O objeto de ISEAddOnTool
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: b813fcac547c8069e84741081a3ceb00044bab87
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2017
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="74800-103">O objeto de ISEAddOnTool</span><span class="sxs-lookup"><span data-stu-id="74800-103">The ISEAddOnTool Object</span></span>
  <span data-ttu-id="74800-104">Um **ISEAddonTool** objeto representa uma ferramenta de suplemento instalado que fornece funcionalidades adicionais toWindows ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74800-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="74800-105">Um exemplo é o **comandos** ferramenta que pode apresentar clicando **vista**, em seguida, **Mostrar suplemento de comando**.</span><span class="sxs-lookup"><span data-stu-id="74800-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="74800-106">Esta ferramenta, em seguida, está acessível para si através da manipulação disponíveis várias **ISEAddOnTool** objetos.</span><span class="sxs-lookup"><span data-stu-id="74800-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

 <span data-ttu-id="74800-107">Cada ferramenta de suplemento pode ser associada ao painel de vertical ou painel de horizontal.</span><span class="sxs-lookup"><span data-stu-id="74800-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="74800-108">O painel vertical está ancorado extremidade direita do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74800-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="74800-109">O painel horizontal está ancorado, o limite inferior.</span><span class="sxs-lookup"><span data-stu-id="74800-109">The horizontal pane is docked to the bottom edge.</span></span>

 <span data-ttu-id="74800-110">Cada separador PowerShell ISE do Windows PowerShell pode ter o seu próprio conjunto de ferramentas de suplemento instalado.</span><span class="sxs-lookup"><span data-stu-id="74800-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="74800-111">Consulte [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) e [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) para aceder à coleção de ferramentas disponíveis para o separador actualmente seleccionado ou o Propriedades do mesmas em qualquer um do **PowerShellTab** objetos no [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) objeto da coleção.</span><span class="sxs-lookup"><span data-stu-id="74800-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="74800-112">Métodos</span><span class="sxs-lookup"><span data-stu-id="74800-112">Methods</span></span>
 <span data-ttu-id="74800-113">Nenhum método do Windows PowerShell ISE específicos estão disponíveis para os objetos desta classe.</span><span class="sxs-lookup"><span data-stu-id="74800-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="74800-114">Propriedades</span><span class="sxs-lookup"><span data-stu-id="74800-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="74800-115">Controlar</span><span class="sxs-lookup"><span data-stu-id="74800-115">Control</span></span>
  <span data-ttu-id="74800-116">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="74800-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="74800-117">O **controlo** propriedade fornece acesso de leitura para muitos dos detalhes da ferramenta de suplemento de comandos.</span><span class="sxs-lookup"><span data-stu-id="74800-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

```
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

### <a name="isvisible"></a><span data-ttu-id="74800-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="74800-118">IsVisible</span></span>
  <span data-ttu-id="74800-119">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="74800-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="74800-120">A propriedade booleana que indica se a ferramenta de suplemento está atualmente visível no respetivo painel atribuído.</span><span class="sxs-lookup"><span data-stu-id="74800-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="74800-121">Se está visível, pode definir o **IsVisible** propriedade **$false** ocultar a ferramenta ou definir o **IsVisible** propriedade para **$true** para tornar uma ferramenta de suplemento visível no respetivo separador do PowerShell. Tenha em atenção que depois de uma ferramenta de suplemento está oculta, já não é acessível através de **CurrentVisibleHorizontalTool** ou **CurrentVisibleVerticalTool** objetos e, por conseguinte, não pode ser tornada visível através da utilização Esta propriedade nesse objecto.</span><span class="sxs-lookup"><span data-stu-id="74800-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

### <a name="name"></a><span data-ttu-id="74800-122">Nome</span><span class="sxs-lookup"><span data-stu-id="74800-122">Name</span></span>
  <span data-ttu-id="74800-123">Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="74800-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="74800-124">A propriedade só de leitura que obtém o nome da ferramenta de suplemento.</span><span class="sxs-lookup"><span data-stu-id="74800-124">The read-only property that gets the name of the add-on tool.</span></span>

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## <a name="see-also"></a><span data-ttu-id="74800-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="74800-125">See Also</span></span>
- [<span data-ttu-id="74800-126">O objeto de ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="74800-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="74800-127">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="74800-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="74800-128">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="74800-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="74800-129">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="74800-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

