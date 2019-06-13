---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objeto ISEAddOnTool
ms.openlocfilehash: c71602d200b941ed4fb142b9c35f0fe68982e3e9
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028993"
---
# <a name="the-iseaddontool-object"></a>Objeto ISEAddOnTool

Uma **ISEAddonTool** objeto representa uma ferramenta do suplemento instalado que fornece funcionalidade adicional toWindows ISE do PowerShell. Um exemplo é o **comandos** ferramenta que pode ser exibida ao clicar em **vista**, em seguida, **Mostrar suplemento de comando**. Essa ferramenta, em seguida, está acessível para ao manipular as disponíveis várias **ISEAddOnTool** objetos.

Cada ferramenta do suplemento pode ser associada com o painel vertical ou horizontal painel. O painel de vertical é encaixado na borda direita do ISE do Windows PowerShell. O painel horizontal é encaixado na borda da parte inferior.

Cada separador do PowerShell no ISE do Windows PowerShell pode ter seu próprio conjunto de ferramentas de suplemento instalado. Ver [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) e [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) para acessar a coleção de ferramentas disponíveis para o separador atualmente selecionado ou o as mesmas propriedades em qualquer um da **PowerShellTab** objetos na [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) objeto da coleção.

## <a name="methods"></a>Métodos

Não há nenhum método do Windows PowerShell ISE específicas disponíveis para objetos dessa classe.

## <a name="properties"></a>Propriedades

### <a name="control"></a>Controlar

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

O **controle** propriedade fornece acesso de leitura para muitos dos detalhes da ferramenta do suplemento de comandos.

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

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

A propriedade booleana que indica se a ferramenta do suplemento é atualmente visível no seu painel atribuído. Se estiver visível, pode definir o **IsVisible** propriedade **$false** para ocultar a ferramenta ou definir o **IsVisible** propriedade para **$true** para tornar uma ferramenta do suplemento visível no respetivo separador do PowerShell. Tenha em atenção que depois de uma ferramenta de suplementos está oculta, já não é acessível através da **CurrentVisibleHorizontalTool** ou **CurrentVisibleVerticalTool** objetos e, portanto, não pode se tornar visível através da utilização Esta propriedade nesse objeto.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Nome

Suportado no Windows PowerShell ISE 3.0 e posteriores e não está presente em versões anteriores.

A propriedade só de leitura que obtém o nome da ferramenta do suplemento.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a>Veja Também

- [Objeto ISEAddOnToolCollection](The-ISEAddOnToolCollection-Object.md)
- [Objetivo do ISE do Windows PowerShell Scripting o modelo de objeto](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)
