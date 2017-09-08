---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: A hierarquia de modelo do objeto do ISE
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
ms.openlocfilehash: b6e251eac7db56896490362392e0a1c4c10a8d4a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2017
---
# <a name="the-ise-object-model-hierarchy"></a>A hierarquia de modelo do objeto do ISE
  Este tópico mostra a hierarquia de objetos que fazem parte do ISE (Ambiente de Script Integrado) do Windows PowerShell. O ISE do Windows PowerShell está incluído no Windows PowerShell 3.0 e no Windows PowerShell 4.0. Clique um objeto para levá-lo até a documentação de referência da classe que define o objeto.

##  <a name="psise-object"></a>**Objeto $psISE**
 O objeto **$psISE** é o [objeto raiz](The-ObjectModelRoot-Object.md) da hierarquia de objeto ISE do Windows PowerShell. Localizado no nível superior, disponibiliza os seguintes objetos para script:

-   **[$psISE.CurrentFile]()**

-   **[$psISE.CurrentPowerShellTab]()**

-   **[$psISE.CurrentVisibleHorizontalTool]()**

-   **[$psISE.CurrentVisibleVerticalTool]()**

-   **[$psISE.Options]()**

-   **[$psISE.PowerShellTabs]()**

##  <a name="psisecurrentfilethe-isefile-objectmd"></a>**[$psISE.CurrentFile](The-ISEFile-Object.md)**
 O objeto **$psISE.CurrentFile** é uma instância da classe [ISEFile](The-ISEFile-Object.md) e disponibiliza os seguintes objetos para script:

-   **[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**

-   **[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)** Este objeto é uma instância da classe [ISEEditor](The-ISEEditor-Object.md) e disponibiliza os seguintes objetos para script:

    -   **[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**

    -   **[CaretColumn](The-ISEEditor-Object.md)**

    -   **[CaretLine](The-ISEEditor-Object.md)**

    -   **[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**

    -   **[LineCount](The-ISEEditor-Object.md)**

    -   **[SelectedText](The-ISEEditor-Object.md)**

    -   **[Text](The-ISEEditor-Object.md)**

-   **[EncodingThe-ISEFile-Object.md]()**

-   **[FullPathThe-ISEFile-Object.md]()**

-   **[IsSavedThe-ISEFile-Object.md]()**

-   **[IsUntitledThe-ISEFile-Object.md]()**

##  <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**
 O objeto **$psISE.CurrentPowerShellTab** é uma instância da classe [PowerShellTab](The-PowerShellTab-Object.md) e disponibiliza os seguintes objetos para script:

-   **[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)** Este objeto é uma instância da classe [ISEMenuItem](The-ISEMenuItem-Object.md) e disponibiliza os seguintes objetos para scripts:

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)** Este objeto é uma instância da classe [ISEEditor](The-ISEEditor-Object.md) e disponibiliza os seguintes objetos para scripts:

    -   **[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**

    -   **[CaretColumnThe-ISEEditor-Object.md]()**

    -   **[CaretLineThe-ISEEditor-Object.md]()**

    -   **[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**

    -   **[LineCountThe-ISEEditor-Object.md]()**

    -   **[SelectedTextThe-ISEEditor-Object.md]()**

    -   **[TextThe-ISEEditor-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**

-   **[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

##  <a name="psisecurrentvisiblehorizontaltool"></a>**$psISE.CurrentVisibleHorizontalTool**
 O objeto **$psISE.CurrentVisibleHorizontalTool** é uma instância da classe [ISEAddOnTool](The-ISEAddOnTool-Object.md). Ele representa a ferramenta complementar instalada que está encaixada atualmente na borda superior da janela do ISE do Windows PowerShell. Esse objeto disponibiliza os seguintes objetos para script:

-   **[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**

##  <a name="psisecurrentvisibleverticaltool"></a>**$psISE.CurrentVisibleVerticalTool**
 O objeto **$psISE.CurrentVisibleHorizontalTool** é uma instância da classe [ISEAddOnTool](The-ISEAddOnTool-Object.md). Ele representa a ferramenta complementar instalada que está encaixada atualmente na borda superior direita da janela do ISE do Windows PowerShell. Esse objeto disponibiliza os seguintes objetos para script:

-   **[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**

-   **[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**

##  <a name="psiseoptions"></a>**$psISE.Options**
 O objeto **$psISE.Options** disponibiliza os seguintes objetos para script:

-   **[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**

-   **[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**

-   **[$psISE.Options. UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**

-   **[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**

##  <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**
 O objeto **$psISE.PowerShellTabs** é uma instância da classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md). É uma coleção de todas as guias do PowerShell abertas no momento que representam os ambientes de execução disponíveis do Windows PowerShell no computador local ou em computadores remotos conectados. Cada membro da coleção é uma instância da classe [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="see-also"></a>Consulte Também
- [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md)

