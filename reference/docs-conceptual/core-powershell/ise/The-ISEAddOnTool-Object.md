---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: O objeto ISEAddOnTool
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: 15f0cdd1425b9f87edeb0404fc385275e4a9d1d8
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="fe996-103">O objeto ISEAddOnTool</span><span class="sxs-lookup"><span data-stu-id="fe996-103">The ISEAddOnTool Object</span></span>
  <span data-ttu-id="fe996-104">Um objeto **ISEAddonTool** representa uma ferramenta complementar instalada que fornece funcionalidade adicional ao ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe996-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="fe996-105">Um exemplo é a ferramenta **Comandos** que você pode exibir clicando em **Exibir** e em **Mostrar Complemento de Comando**.</span><span class="sxs-lookup"><span data-stu-id="fe996-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="fe996-106">Esta ferramenta fica, então, acessível a você, manipulando os vários objetos disponíveis **ISEAddOnTool**.</span><span class="sxs-lookup"><span data-stu-id="fe996-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

 <span data-ttu-id="fe996-107">Cada ferramenta complementar pode ser associada ao painel vertical ou ao painel horizontal.</span><span class="sxs-lookup"><span data-stu-id="fe996-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="fe996-108">O painel vertical é encaixado na borda direita do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe996-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="fe996-109">O painel horizontal está encaixado na borda inferior.</span><span class="sxs-lookup"><span data-stu-id="fe996-109">The horizontal pane is docked to the bottom edge.</span></span>

 <span data-ttu-id="fe996-110">Cada guia PowerShell no ISE do Windows PowerShell pode ter seu próprio conjunto de ferramentas complementares instaladas.</span><span class="sxs-lookup"><span data-stu-id="fe996-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="fe996-111">Consulte [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md) e [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md) para acessar a coleção de ferramentas disponíveis para a guia selecionada no momento ou as mesmas propriedades em qualquer um dos objetos **PowerShellTab** no objeto do conjunto [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md).</span><span class="sxs-lookup"><span data-stu-id="fe996-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="fe996-112">Métodos</span><span class="sxs-lookup"><span data-stu-id="fe996-112">Methods</span></span>
 <span data-ttu-id="fe996-113">Não há métodos específicos de ISE do Windows PowerShell disponíveis para objetos desta classe.</span><span class="sxs-lookup"><span data-stu-id="fe996-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="fe996-114">Propriedades</span><span class="sxs-lookup"><span data-stu-id="fe996-114">Properties</span></span>

###  <span data-ttu-id="fe996-115"><a name="Control"></a> Control</span><span class="sxs-lookup"><span data-stu-id="fe996-115"><a name="Control"></a> Control</span></span>
  <span data-ttu-id="fe996-116">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="fe996-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="fe996-117">A propriedade **Control** fornece acesso de leitura a muitos dos detalhes da ferramenta complementar Comandos.</span><span class="sxs-lookup"><span data-stu-id="fe996-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

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

###  <span data-ttu-id="fe996-118"><a name="IsVisible"></a> IsVisible</span><span class="sxs-lookup"><span data-stu-id="fe996-118"><a name="IsVisible"></a> IsVisible</span></span>
  <span data-ttu-id="fe996-119">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="fe996-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="fe996-120">A propriedade Boolean que indica se a ferramenta complementar está atualmente visível no seu painel atribuído.</span><span class="sxs-lookup"><span data-stu-id="fe996-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="fe996-121">Se estiver visível, você poderá definir a propriedade **IsVisible** como **$false** para ocultar a ferramenta ou definir a propriedade **IsVisible** como **$true** para tornar uma ferramenta complementar visível em sua guia PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe996-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab.</span></span> <span data-ttu-id="fe996-122">Observe que depois que uma ferramenta complementar é ocultada, ela não poderá mais ser acessada pelos objetos **CurrentVisibleHorizontalTool** ou **CurrentVisibleVerticalTool** e, portanto, não pode ser tornada visível usando esta propriedade no objeto.</span><span class="sxs-lookup"><span data-stu-id="fe996-122">Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

###  <span data-ttu-id="fe996-123"><a name="name"></a> Name</span><span class="sxs-lookup"><span data-stu-id="fe996-123"><a name="name"></a> Name</span></span>
  <span data-ttu-id="fe996-124">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="fe996-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="fe996-125">A propriedade somente leitura que obtém o nome da ferramenta complementar.</span><span class="sxs-lookup"><span data-stu-id="fe996-125">The read-only property that gets the name of the add-on tool.</span></span>

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## <a name="see-also"></a><span data-ttu-id="fe996-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="fe996-126">See Also</span></span>
- [<span data-ttu-id="fe996-127">O objeto ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="fe996-127">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="fe996-128">O modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe996-128">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="fe996-129">Referência de modelo de objeto do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe996-129">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="fe996-130">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="fe996-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

