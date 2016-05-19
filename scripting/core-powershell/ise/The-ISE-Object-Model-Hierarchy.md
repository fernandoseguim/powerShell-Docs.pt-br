---
title: A hierarquia de modelo do objeto do ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
---
# A hierarquia de modelo do objeto do ISE
  Este tópico mostra a hierarquia de objetos que fazem parte do ISE (Ambiente de Script Integrado) do Windows PowerShell. O ISE do Windows PowerShell está incluído no Windows PowerShell 3.0 e no Windows PowerShell 4.0. Clique um objeto para levá-lo até a documentação de referência da classe que define o objeto.

##  <a name="psISE"></a> **Objeto $psISE**
 O objeto **$psISE** é o [objeto raiz](The-ObjectModelRoot-Object.md) da hierarquia de objeto ISE do Windows PowerShell. Localizado no nível superior, disponibiliza os seguintes objetos para script:

-   **[$psISE.CurrentFile](#currentfile)**

-   **[$psISE.CurrentPowerShellTab](#currentpowershelltab)**

-   **[$psISE.CurrentVisibleHorizontalTool](#CurrentVisibleHorizontalTool)**

-   **[$psISE.CurrentVisibleVerticalTool](#CurrentVisibleVerticalTool)**

-   **[$psISE.Options](#options)**

-   **[$psISE.PowerShellTabs](#powershelltabs)**

##  <a name="CurrentFile"></a> **[$psISE.CurrentFile](The-ISEFile-Object.md)**
 O objeto **$psISE.CurrentFile** é uma instância da classe [ISEFile](The-ISEFile-Object.md) e disponibiliza os seguintes objetos para script:

-   **[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md#Displayname)**

-   **[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)** Este objeto é uma instância da classe [ISEEditor](The-ISEEditor-Object.md) e disponibiliza os seguintes objetos para script:

    -   **[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md#cangotomatch)**

    -   **[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**

    -   **[CaretLine](The-ISEEditor-Object.md#CaretLine)**

    -   **[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**

    -   **[LineCount](The-ISEEditor-Object.md#LineCount)**

    -   **[SelectedText](The-ISEEditor-Object.md#SelectedText)**

    -   **[Texto](The-ISEEditor-Object.md#Text)**

-   **[Codificando](The-ISEFile-Object.md#Encoding)**

-   **[FullPath](The-ISEFile-Object.md#FullPath)**

-   **[IsSaved](The-ISEFile-Object.md#IsSaved)**

-   **[IsUntitled](The-ISEFile-Object.md#IsUntitled)**

##  <a name="CurrentPowerShellTab"></a> **[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**
 O objeto **$psISE.CurrentPowerShellTab** é uma instância da classe [PowerShellTab](The-PowerShellTab-Object.md) e disponibiliza os seguintes objetos para script:

-   **[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)** Este objeto é uma instância da classe [ISEMenuItem](The-ISEMenuItem-Object.md) e disponibiliza os seguintes objetos para scripts:

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.Action](The-ISEMenuItem-Object.md#Action)**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName](The-ISEMenuItem-Object.md#DisplayName)**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.Shortcut](The-ISEMenuItem-Object.md#Shortcut)**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.CanInvoke](The-PowerShellTab-Object.md#CanExecute)**

-   **[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)** Este objeto é uma instância da classe [ISEEditor](The-ISEEditor-Object.md) e disponibiliza os seguintes objetos para scripts:

    -   **[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatch](The-ISEEditor-Object.md#cangotomatch)**

    -   **[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**

    -   **[CaretLine](The-ISEEditor-Object.md#CaretLine)**

    -   **[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**

    -   **[LineCount](The-ISEEditor-Object.md#LineCount)**

    -   **[SelectedText](The-ISEEditor-Object.md#SelectedText)**

    -   **[Texto](The-ISEEditor-Object.md#Text)**

-   **[$psISE.CurrentPowerShellTab.DisplayName](The-PowerShellTab-Object.md#Displayname)**

-   **[$psISE.CurrentPowerShellTab.ExpandedScript](The-PowerShellTab-Object.md#ExpandedScript)**

-   **[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#HorizontalAddOnToolsPaneOpened)**

-   **[$psISE.CurrentPowerShellTab.Prompt](The-PowerShellTab-Object.md#Prompt)**

-   **[$psISE.CurrentPowerShellTab.ShowCommands](The-PowerShellTab-Object.md#ShowCommands)**

-   **[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.StatusText](The-PowerShellTab-Object.md#StatusText)**

-   **[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#VerticalAddOnToolsPaneOpened)**

-   **[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

##  <a name="CurrentVisibleHorizontalTool"></a> **$psISE.CurrentVisibleHorizontalTool**
 O objeto **$psISE.CurrentVisibleHorizontalTool** é uma instância da classe [ISEAddOnTool](The-ISEAddOnTool-Object.md). Ele representa a ferramenta complementar instalada que está encaixada na borda superior da janela do ISE do Windows PowerShell. Esse objeto disponibiliza os seguintes objetos para script:

-   **[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#control)**

-   **[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#isvisible)**

-   **[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**

##  <a name="CurrentVisibleVerticalTool"></a> **$psISE.CurrentVisibleVerticalTool**
 O objeto **$psISE.CurrentVisibleHorizontalTool** é uma instância da classe [ISEAddOnTool](The-ISEAddOnTool-Object.md). Ele representa a ferramenta complementar instalada que está encaixada atualmente na borda superior direita da janela do ISE do Windows PowerShell. Esse objeto disponibiliza os seguintes objetos para script:

-   **[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#control)**

-   **[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#isvisible)**

-   **[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**

##  <a name="Options"></a> **$psISE.Options**
 O objeto **$psISE.Options** disponibiliza os seguintes objetos para script:

-   **[$psISE.Options.AutoSaveMinuteInterval](The-ISEOptions-Object.md#asmi)**

-   **[$psISE.Options.ConsolePaneBackgroundColor](The-ISEOptions-Object.md#cpbc)**

-   **[$psISE.Options.ConsolePaneTextForegroundColor](The-ISEOptions-Object.md#conpfc)**

-   **[$psISE.Options.ConsolePaneTextBackgroundColor](The-ISEOptions-Object.md#conptbc)**

-   **[$psISE.Options.ConsoleTokenColors](The-ISEOptions-Object.md#contc)**

-   **[$psISE.Options.DebugBackgroundColor](The-ISEOptions-Object.md#dbc)**

-   **[$psISE.Options.DebugForegroundColor](The-ISEOptions-Object.md#dfc)**

-   **[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**

-   **[$psISE.Options.ErrorBackgroundColor](The-ISEOptions-Object.md#ebc)**

-   **[$psISE.Options.ErrorForegroundColor](The-ISEOptions-Object.md#efc)**

-   **[$psISE.Options.FontName](The-ISEOptions-Object.md#fn)**

-   **[$psISE.Options.Fontsize](The-ISEOptions-Object.md#fs)**

-   **[$psISE.Options.IntellisenseTimeoutInSeconds](The-ISEOptions-Object.md#itis)**

-   **[$psISE.Options.MRUCount](The-ISEOptions-Object.md#mc)**

-   **[$psISE.Options.ScriptPaneBackgroundColor](The-ISEOptions-Object.md#spbc)**

-   **[$psISE.Options.ScriptPaneForegroundColor](The-ISEOptions-Object.md#spfc)**

-   **[$psISE.Options.SelectedScriptPaneState](The-ISEOptions-Object.md#ssps)**

-   **[$psISE.Options.ShowDefaultSnippets](The-ISEOptions-Object.md#sds)**

-   **[$psISE.Options.ShowIntellisenseInConsolePane](The-ISEOptions-Object.md#siicp)**

-   **[$psISE.Options.ShowIntellisenseInScriptPane](The-ISEOptions-Object.md#siisp)**

-   **[$psISE.Options.ShowLineNumbers](The-ISEOptions-Object.md#sln)**

-   **[$psISE.Options.ShowOutlining](The-ISEOptions-Object.md#so)**

-   **[$psISE.Options.ShowToolBar](The-ISEOptions-Object.md#stb)**

-   **[$psISE.Options.ShowWarningBeforeSavingOnRun](The-ISEOptions-Object.md#swbsor)**

-   **[$psISE.Options.ShowWarningForDuplicateFiles](The-ISEOptions-Object.md#swfdf)**

-   **[$psISE.Options.TokenColors](The-ISEOptions-Object.md#tc)**

-   **[$psISE.Options.UseEnterToSelectConsolePaneIntellisense](The-ISEOptions-Object.md#uetsicpi)**

-   **[$psISE.Options. UseEnterToSelectScriptPaneIntellisense](The-ISEOptions-Object.md#uetsispi)**

-   **[$psISE.Options.UseLocalHelp](The-ISEOptions-Object.md#ulh)**

-   **[$psISE.Options.VerboseBackgroundColor](The-ISEOptions-Object.md#vbc)**

-   **[$psISE.Options.VerboseForegroundColor](The-ISEOptions-Object.md#vfc)**

-   **[$psISE.Options.WarningBackgroundColor](The-ISEOptions-Object.md#wbc)**

-   **[$psISE.Options.WarningForegroundColor](The-ISEOptions-Object.md#wfc)**

-   **[$psISE.Options.XmlTokenColors](The-ISEOptions-Object.md#xtc)**

-   **[$psISE.Options.Zoom](The-ISEOptions-Object.md#z)**

##  <a name="PowerShellTabs"></a> **[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**
 O objeto **$psISE.PowerShellTabs** é uma instância da classe [PowerShellTabCollection](The-PowerShellTabCollection-Object.md). É uma coleção de todas as guias do PowerShell abertas no momento que representam os ambientes de execução disponíveis do Windows PowerShell no computador local ou em computadores remotos conectados. Cada membro da coleção é uma instância da classe [PowerShellTab](The-PowerShellTab-Object.md).

## Consulte Também
 [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
 [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md)


<!--HONumber=May16_HO2-->


