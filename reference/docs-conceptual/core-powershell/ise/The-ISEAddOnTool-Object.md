---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEAddOnTool
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: e091f37601c7a4fdaf5deff8c668b18ee7369e74
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseaddontool-object"></a>Objeto ISEAddOnTool

Um **ISEAddonTool** objeto representa uma ferramenta de suplemento instalado que fornece funcionalidades adicionais toWindows ISE do PowerShell. Um exemplo é o **comandos** ferramenta que pode apresentar clicando **vista**, em seguida, **Mostrar suplemento de comando**. Esta ferramenta, em seguida, está acessível para si através da manipulação disponíveis várias **ISEAddOnTool** objetos.

Cada ferramenta de suplemento pode ser associada ao painel de vertical ou painel de horizontal. O painel vertical está ancorado extremidade direita do ISE do Windows PowerShell. O painel horizontal está ancorado, o limite inferior.

Cada separador PowerShell ISE do Windows PowerShell pode ter o seu próprio conjunto de ferramentas de suplemento instalado. Consulte [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) e [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) para aceder à coleção de ferramentas disponíveis para o separador actualmente seleccionado ou o Propriedades do mesmas em qualquer um do **PowerShellTab** objetos no [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) objeto da coleção.

## <a name="methods"></a>Métodos

Nenhum método do Windows PowerShell ISE específicos estão disponíveis para os objetos desta classe.

## <a name="properties"></a>Propriedades

### <a name="control"></a>Controlar

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

O **controlo** propriedade fornece acesso de leitura para muitos dos detalhes da ferramenta de suplemento de comandos.

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

### <a name="isvisible"></a>IsVisible

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

A propriedade booleana que indica se a ferramenta de suplemento está atualmente visível no respetivo painel atribuído. Se está visível, pode definir o **IsVisible** propriedade **$false** ocultar a ferramenta ou definir o **IsVisible** propriedade para **$true** para tornar uma ferramenta de suplemento visível no respetivo separador do PowerShell. Tenha em atenção que depois de uma ferramenta de suplemento está oculta, já não é acessível através de **CurrentVisibleHorizontalTool** ou **CurrentVisibleVerticalTool** objetos e, por conseguinte, não pode ser tornada visível através da utilização Esta propriedade nesse objecto.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Nome

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente nas versões anteriores.

A propriedade só de leitura que obtém o nome da ferramenta de suplemento.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a>Consulte Também

- [O objeto de ISEAddOnToolCollection](The-ISEAddOnToolCollection-Object.md)
- [Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)