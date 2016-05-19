---
title: O objeto ISEAddOnTool
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
---
# O objeto ISEAddOnTool
  Um objeto **ISEAddonTool** representa uma ferramenta complementar instalada que fornece funcionalidade adicional ao ISE do Windows PowerShell. Um exemplo é a ferramenta **Comandos** que você pode exibir clicando **Exibir**, em seguida, em **Mostrar Complemento de Comando**. Esta ferramenta fica, então, acessível a você, manipulando os vários objetos disponíveis **ISEAddOnTool**.

 Cada ferramenta complementar pode ser associada com o painel vertical ou com o painel horizontal. O painel vertical é encaixado na borda direita do ISE do Windows PowerShell. O painel horizontal está encaixado na borda inferior.

 Cada guia PowerShell no ISE do Windows PowerShell pode ter seu próprio conjunto de ferramentas complementares instaladas. Consulte [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md) e [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md) para acessar a coleção de ferramentas disponíveis para a guia selecionada no momento ou as mesmas propriedades em qualquer um dos objetos **PowerShellTab** no objeto do conjunto [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md).

## Métodos
 Não há métodos específicos de ISE do Windows PowerShell disponíveis para objetos desta classe.

## Propriedades

###  <a name="Control"></a> Control
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.

 A propriedade **Controle** fornece acesso de leitura para muitos dos detalhes da ferramenta complementar Comandos.

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

###  <a name="IsVisible"></a> IsVisible
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.

 A propriedade booliana que indica se a ferramenta complementar está atualmente visível no seu painel atribuído. Se estiver visível, você poderá definir a propriedade **IsVisible** como **$false** para ocultar a ferramenta ou definir a propriedade **IsVisible** como **$true** para tornar uma ferramenta complementar visível em sua guia PowerShell. Observe que depois que uma ferramenta complementar é oculta, ela não é mais acessível pelos objetos **CurrentVisibleHorizontalTool** ou **CurrentVisibleVerticalTool** e, portanto, não pode ser tornada visível usando esta propriedade no objeto.

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

###  <a name="name"></a> Nome
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.

 A propriedade somente leitura que recebe o nome da ferramenta complementar.

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## Consulte Também
 [O objeto ISEAddOnToolCollection](The-ISEAddOnToolCollection-Object.md)
 [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
 [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md)
 [A hierarquia de modelo do objeto do ISE](The-ISE-Object-Model-Hierarchy.md)


<!--HONumber=May16_HO2-->


