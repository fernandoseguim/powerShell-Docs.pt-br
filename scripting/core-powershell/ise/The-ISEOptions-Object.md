---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: O objeto ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 56bdd5999b46b6e29e762c2d9a2060cebe3a1299
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="9909a-103">O objeto ISEOptions</span><span class="sxs-lookup"><span data-stu-id="9909a-103">The ISEOptions Object</span></span>
  <span data-ttu-id="9909a-104">O objeto **ISEOptions** representa várias configurações para o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9909a-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="9909a-105">Ele é uma instância da classe **Microsoft.PowerShell.Host.ISE.ISEOptions**.</span><span class="sxs-lookup"><span data-stu-id="9909a-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="9909a-106">O objeto **ISEOptions** fornece os seguintes métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="9909a-106">The **ISEOptions** object provides the following methods and properties.</span></span>

 <span data-ttu-id="9909a-107">**Métodos**</span><span class="sxs-lookup"><span data-stu-id="9909a-107">**Methods**</span></span>

-   [<span data-ttu-id="9909a-108">RestoreDefaultConsoleTokenColors()</span><span class="sxs-lookup"><span data-stu-id="9909a-108">RestoreDefaultConsoleTokenColors()</span></span>](#rdctc)

-   [<span data-ttu-id="9909a-109">RestoreDefaults()</span><span class="sxs-lookup"><span data-stu-id="9909a-109">RestoreDefaults()</span></span>](#rd)

-   [<span data-ttu-id="9909a-110">RestoreDefaultTokenColors()</span><span class="sxs-lookup"><span data-stu-id="9909a-110">RestoreDefaultTokenColors()</span></span>](#rdtc)

-   [<span data-ttu-id="9909a-111">RestoreDefaultXmlTokenColors()</span><span class="sxs-lookup"><span data-stu-id="9909a-111">RestoreDefaultXmlTokenColors()</span></span>](#rdxtc)

 <span data-ttu-id="9909a-112">**Propriedades**</span><span class="sxs-lookup"><span data-stu-id="9909a-112">**Properties**</span></span>

-   [<span data-ttu-id="9909a-113">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="9909a-113">AutoSaveMinuteInterval</span></span>](#asmi)

-   [<span data-ttu-id="9909a-114">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-114">CommandPaneBackgroundColor</span></span>](#cpbc)

-   [<span data-ttu-id="9909a-115">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="9909a-115">CommandPaneUp</span></span>](#cpu)

-   [<span data-ttu-id="9909a-116">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-116">ConsolePaneBackgroundColor</span></span>](#conpbc)

-   [<span data-ttu-id="9909a-117">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-117">ConsolePaneForegroundColor</span></span>](#conpfc)

-   [<span data-ttu-id="9909a-118">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-118">ConsolePaneTextBackgroundColor</span></span>](#conptbc)

-   [<span data-ttu-id="9909a-119">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="9909a-119">ConsoleTokenColors</span></span>](#contc)

-   [<span data-ttu-id="9909a-120">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-120">DebugBackgroundColor</span></span>](#dbc)

-   [<span data-ttu-id="9909a-121">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-121">DebugForegroundColor</span></span>](#dfc)

-   [<span data-ttu-id="9909a-122">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="9909a-122">DefaultOptions</span></span>](#do)

-   [<span data-ttu-id="9909a-123">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-123">ErrorBackgroundColor</span></span>](#ebc)

-   [<span data-ttu-id="9909a-124">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-124">ErrorForegroundColor</span></span>](#efc)

-   [<span data-ttu-id="9909a-125">FontName</span><span class="sxs-lookup"><span data-stu-id="9909a-125">FontName</span></span>](#fn)

-   [<span data-ttu-id="9909a-126">FontSize</span><span class="sxs-lookup"><span data-stu-id="9909a-126">FontSize</span></span>](#fs)

-   [<span data-ttu-id="9909a-127">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="9909a-127">IntellisenseTimeoutInSeconds</span></span>](#itis)

-   [<span data-ttu-id="9909a-128">MruCount</span><span class="sxs-lookup"><span data-stu-id="9909a-128">MruCount</span></span>](#mc)

-   [<span data-ttu-id="9909a-129">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-129">OutputPaneBackgroundColor</span></span>](#opbc)

-   [<span data-ttu-id="9909a-130">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-130">OutputPaneTextForegroundColor</span></span>](#optfc)

-   [<span data-ttu-id="9909a-131">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-131">OutputPaneTextBackgroundColor</span></span>](#optbc)

-   [<span data-ttu-id="9909a-132">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-132">ScriptPaneBackgroundColor</span></span>](#spbc)

-   [<span data-ttu-id="9909a-133">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-133">ScriptPaneForegroundColor</span></span>](#spfc)

-   [<span data-ttu-id="9909a-134">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="9909a-134">SelectedScriptPaneState</span></span>](#ssps)

-   [<span data-ttu-id="9909a-135">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="9909a-135">ShowDefaultSnippets</span></span>](#sds)

-   [<span data-ttu-id="9909a-136">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="9909a-136">ShowIntellisenseInConsolePane</span></span>](#siicp)

-   [<span data-ttu-id="9909a-137">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="9909a-137">ShowIntellisenseInScriptPane</span></span>](#siisp)

-   [<span data-ttu-id="9909a-138">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="9909a-138">ShowLineNumbers</span></span>](#sln)

-   [<span data-ttu-id="9909a-139">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="9909a-139">ShowOutlining</span></span>](#so)

-   [<span data-ttu-id="9909a-140">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="9909a-140">ShowToolBar</span></span>](#stb)

-   [<span data-ttu-id="9909a-141">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="9909a-141">ShowWarningBeforeSavingOnRun</span></span>](#swbsor)

-   [<span data-ttu-id="9909a-142">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="9909a-142">ShowWarningForDuplicateFiles</span></span>](#swfdf)

-   [<span data-ttu-id="9909a-143">TokenColors</span><span class="sxs-lookup"><span data-stu-id="9909a-143">TokenColors</span></span>](#tc)

-   [<span data-ttu-id="9909a-144">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="9909a-144">UseEnterToSelectInConsolePaneIntellisense</span></span>](#uetsicpi)

-   [<span data-ttu-id="9909a-145">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="9909a-145">UseEnterToSelectInScriptPaneIntellisense</span></span>](#uetsispi)

-   [<span data-ttu-id="9909a-146">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="9909a-146">UseLocalHelp</span></span>](#ulh)

-   [<span data-ttu-id="9909a-147">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-147">VerboseBackgroundColor</span></span>](#vbc)

-   [<span data-ttu-id="9909a-148">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-148">VerboseForegroundColor</span></span>](#vfc)

-   [<span data-ttu-id="9909a-149">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-149">WarningBackgroundColor</span></span>](#wbc)

-   [<span data-ttu-id="9909a-150">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-150">WarningForegroundColor</span></span>](#wfc)

-   [<span data-ttu-id="9909a-151">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="9909a-151">XmlTokenColors</span></span>](#xtc)

-   [<span data-ttu-id="9909a-152">Zoom</span><span class="sxs-lookup"><span data-stu-id="9909a-152">Zoom</span></span>](#z)

## <a name="methods"></a><span data-ttu-id="9909a-153">Métodos</span><span class="sxs-lookup"><span data-stu-id="9909a-153">Methods</span></span>

###  <span data-ttu-id="9909a-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="9909a-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="9909a-155">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-156">Restaura os valores padrão das cores do token no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-156">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <span data-ttu-id="9909a-157"><a name="rd"></a> RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="9909a-157"><a name="rd"></a> RestoreDefaults\(\)</span></span>
  <span data-ttu-id="9909a-158">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-159">Restaura os valores padrão das cores de todas as configurações de opções no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-159">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="9909a-160">Ele também redefine o comportamento de várias mensagens de aviso que fornecem a caixa de seleção padrão para impedir que a mensagem seja mostrada novamente.</span><span class="sxs-lookup"><span data-stu-id="9909a-160">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <span data-ttu-id="9909a-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="9909a-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="9909a-162">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-163">Restaura os valores padrão das cores do token no painel de script.</span><span class="sxs-lookup"><span data-stu-id="9909a-163">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <span data-ttu-id="9909a-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="9909a-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="9909a-165">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-165">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-166">Restaura os valores padrão das cores do token para elementos XML exibidos no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9909a-166">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="9909a-167">Consulte também [XmlTokenColors](#xtc).</span><span class="sxs-lookup"><span data-stu-id="9909a-167">Also see [XmlTokenColors](#xtc).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="9909a-168">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9909a-168">Properties</span></span>

###  <span data-ttu-id="9909a-169"><a name="asmi"></a> AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="9909a-169"><a name="asmi"></a> AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="9909a-170">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-170">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-171">Especifica o número de minutos entre as operações de salvamento automático de seus arquivos pelo ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9909a-171">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="9909a-172">O valor padrão é 2 minutos.</span><span class="sxs-lookup"><span data-stu-id="9909a-172">The default value is 2 minutes.</span></span> <span data-ttu-id="9909a-173">O valor é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="9909a-173">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <span data-ttu-id="9909a-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="9909a-175">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="9909a-175">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="9909a-176">Para versões posteriores, consulte [ConsolePaneBackgroundColor](#conpbc).</span><span class="sxs-lookup"><span data-stu-id="9909a-176">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="9909a-177">Especifica a cor da tela de fundo para o painel de comando.</span><span class="sxs-lookup"><span data-stu-id="9909a-177">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="9909a-178">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-178">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <span data-ttu-id="9909a-179"><a name="cpu"></a> CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="9909a-179"><a name="cpu"></a> CommandPaneUp</span></span>
  <span data-ttu-id="9909a-180">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="9909a-180">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="9909a-181">Especifica se o painel de comando está localizado acima do painel de saída.</span><span class="sxs-lookup"><span data-stu-id="9909a-181">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <span data-ttu-id="9909a-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="9909a-183">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-183">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-184">Especifica a cor da tela de fundo do painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-184">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="9909a-185">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-185">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <span data-ttu-id="9909a-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="9909a-187">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-188">Especifica a cor de primeiro plano do texto no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-188">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <span data-ttu-id="9909a-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="9909a-190">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-190">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-191">Especifica a cor da tela de fundo do texto no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-191">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="9909a-192"><a name="contc"></a> ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="9909a-192"><a name="contc"></a> ConsoleTokenColors</span></span>
  <span data-ttu-id="9909a-193">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-193">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-194">Especifica as cores dos tokens do IntelliSense no painel de Console de ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9909a-194">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="9909a-195">Essa propriedade é um objeto de dicionário que contém pares de nome/valor de tipos de token e cores para o painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-195">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="9909a-196">Para alterar as cores dos tokens do IntelliSense no painel de Script, consulte [TokenColors](#tc).</span><span class="sxs-lookup"><span data-stu-id="9909a-196">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tc).</span></span> <span data-ttu-id="9909a-197">Para redefinir as cores aos valores padrão, consulte [RestoreDefaultConsoleTokenColors()](#rdctc).</span><span class="sxs-lookup"><span data-stu-id="9909a-197">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors()](#rdctc).</span></span> <span data-ttu-id="9909a-198">As cores do token podem ser definidas para o seguinte: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="9909a-198">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="9909a-199"><a name="dbc"></a> DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-199"><a name="dbc"></a> DebugBackgroundColor</span></span>
  <span data-ttu-id="9909a-200">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-200">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-201">Especifica a cor da tela de fundo para o texto de depuração que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-201">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="9909a-202">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-202">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="9909a-203"><a name="dfc"></a> DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-203"><a name="dfc"></a> DebugForegroundColor</span></span>
  <span data-ttu-id="9909a-204">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-204">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-205">Especifica a cor de primeiro plano para o texto de depuração que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-205">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="9909a-206">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-206">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <span data-ttu-id="9909a-207"><a name="do"></a> DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="9909a-207"><a name="do"></a> DefaultOptions</span></span>
  <span data-ttu-id="9909a-208">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-208">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-209">Uma coleção de propriedades que especificam os valores padrão a serem usados quando os métodos Reset são usados.</span><span class="sxs-lookup"><span data-stu-id="9909a-209">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3

```

###  <span data-ttu-id="9909a-210"><a name="ebc"></a> ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-210"><a name="ebc"></a> ErrorBackgroundColor</span></span>
  <span data-ttu-id="9909a-211">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-211">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-212">Especifica a cor da tela de fundo para o texto de erro que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-212">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="9909a-213">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-213">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <span data-ttu-id="9909a-214"><a name="efc"></a> ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-214"><a name="efc"></a> ErrorForegroundColor</span></span>
  <span data-ttu-id="9909a-215">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-215">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-216">Especifica a cor de primeiro plano para o texto de erro que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-216">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="9909a-217">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-217">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <span data-ttu-id="9909a-218"><a name="fn"></a> FontName</span><span class="sxs-lookup"><span data-stu-id="9909a-218"><a name="fn"></a> FontName</span></span>
  <span data-ttu-id="9909a-219">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-219">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-220">Especifica o nome da fonte atualmente em uso, tanto no painel do Script quanto no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-220">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <span data-ttu-id="9909a-221"><a name="fs"></a> FontSize</span><span class="sxs-lookup"><span data-stu-id="9909a-221"><a name="fs"></a> FontSize</span></span>
  <span data-ttu-id="9909a-222">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-222">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-223">Especifica o tamanho da fonte como um inteiro.</span><span class="sxs-lookup"><span data-stu-id="9909a-223">Specifies the font size as an integer.</span></span> <span data-ttu-id="9909a-224">Ele é usado no painel de Script, no painel de Comando e no painel de Saída.</span><span class="sxs-lookup"><span data-stu-id="9909a-224">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="9909a-225">O intervalo de valores válidos é de 8 a 32.</span><span class="sxs-lookup"><span data-stu-id="9909a-225">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <span data-ttu-id="9909a-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="9909a-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="9909a-227">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-227">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-228">Especifica o número de segundos que IntelliSense usa para tentar resolver o texto atualmente digitado.</span><span class="sxs-lookup"><span data-stu-id="9909a-228">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="9909a-229">Após esse número de segundos, o IntelliSense expira e permite que você continue digitando.</span><span class="sxs-lookup"><span data-stu-id="9909a-229">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="9909a-230">O valor padrão é de 3 segundos.</span><span class="sxs-lookup"><span data-stu-id="9909a-230">The default value is 3 seconds.</span></span> <span data-ttu-id="9909a-231">O valor é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="9909a-231">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <span data-ttu-id="9909a-232"><a name="mc"></a> MruCount</span><span class="sxs-lookup"><span data-stu-id="9909a-232"><a name="mc"></a> MruCount</span></span>
  <span data-ttu-id="9909a-233">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-233">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-234">Especifica o número de arquivos abertos recentemente que o ISE do Windows PowerShell acompanha e exibe na parte inferior do menu **Abrir Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="9909a-234">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="9909a-235">O valor padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="9909a-235">The default value is 10.</span></span> <span data-ttu-id="9909a-236">O valor é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="9909a-236">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <span data-ttu-id="9909a-237"><a name="opbc"></a> OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-237"><a name="opbc"></a> OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="9909a-238">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="9909a-238">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="9909a-239">Para versões posteriores, consulte [ConsolePaneBackgroundColor](#conpbc).</span><span class="sxs-lookup"><span data-stu-id="9909a-239">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="9909a-240">A propriedade de leitura/gravação que obtém ou define a cor da tela de fundo para o Painel de saída em si.</span><span class="sxs-lookup"><span data-stu-id="9909a-240">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="9909a-241">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-241">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <span data-ttu-id="9909a-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="9909a-243">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="9909a-243">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="9909a-244">Para versões posteriores, consulte [ConsolePaneForegroundColor](#conpfc).</span><span class="sxs-lookup"><span data-stu-id="9909a-244">For later versions, see [ConsolePaneForegroundColor](#conpfc).</span></span>

 <span data-ttu-id="9909a-245">A propriedade de leitura/gravação que muda a cor do primeiro plano do texto no Painel de saída no ISE do Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="9909a-245">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <span data-ttu-id="9909a-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="9909a-247">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="9909a-247">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="9909a-248">Para versões posteriores, consulte [ConsolePaneTextBackgroundColor](#conptbc).</span><span class="sxs-lookup"><span data-stu-id="9909a-248">For later versions, see [ConsolePaneTextBackgroundColor](#conptbc).</span></span>

 <span data-ttu-id="9909a-249">A propriedade de leitura/gravação que muda a cor da tela de fundo do texto no painel Saída.</span><span class="sxs-lookup"><span data-stu-id="9909a-249">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="9909a-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="9909a-251">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-251">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-252">A propriedade de leitura/gravação que obtém ou define a cor da tela de fundo dos arquivos.</span><span class="sxs-lookup"><span data-stu-id="9909a-252">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="9909a-253">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-253">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <span data-ttu-id="9909a-254"><a name="spfc"></a> ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-254"><a name="spfc"></a> ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="9909a-255">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-255">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-256">A propriedade de leitura/gravação que obtém ou define a cor de primeiro plano de arquivos de não script no painel Script.</span><span class="sxs-lookup"><span data-stu-id="9909a-256">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="9909a-257">Para definir a cor de primeiro plano dos arquivos de script, use a propriedade [TokenColors](The-ISEOptions-Object.md#tc).</span><span class="sxs-lookup"><span data-stu-id="9909a-257">To set the foreground color for script files, use the [TokenColors](The-ISEOptions-Object.md#tc) property.</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <span data-ttu-id="9909a-258"><a name="ssps"></a> SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="9909a-258"><a name="ssps"></a> SelectedScriptPaneState</span></span>
  <span data-ttu-id="9909a-259">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-259">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-260">A propriedade de leitura/gravação que obtém ou define a posição do painel Script no visor.</span><span class="sxs-lookup"><span data-stu-id="9909a-260">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="9909a-261">A cadeia pode ser "Maximizada", "Na parte superior" ou à "Direita".</span><span class="sxs-lookup"><span data-stu-id="9909a-261">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <span data-ttu-id="9909a-262"><a name="sds"></a> ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="9909a-262"><a name="sds"></a> ShowDefaultSnippets</span></span>
  <span data-ttu-id="9909a-263">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-264">Especifica se a lista **Ctrl+J** dos trechos de código inclui o conjunto inicial que está incluído no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9909a-264">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="9909a-265">Quando definido como **$false**, somente trechos de código definidos pelo usuário aparecem na lista **Ctrl+J**.</span><span class="sxs-lookup"><span data-stu-id="9909a-265">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="9909a-266">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="9909a-266">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <span data-ttu-id="9909a-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="9909a-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="9909a-268">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-268">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-269">Especifica se o IntelliSense oferece sugestões de sintaxe, parâmetro e valor no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-269">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="9909a-270">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="9909a-270">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <span data-ttu-id="9909a-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="9909a-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="9909a-272">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-272">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-273">Especifica se o IntelliSense oferece sugestões de sintaxe, parâmetro e valor no painel do Script.</span><span class="sxs-lookup"><span data-stu-id="9909a-273">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="9909a-274">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="9909a-274">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <span data-ttu-id="9909a-275"><a name="sln"></a> ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="9909a-275"><a name="sln"></a> ShowLineNumbers</span></span>
  <span data-ttu-id="9909a-276">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-276">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-277">Especifica se o painel de Script exibe os números de linha na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="9909a-277">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="9909a-278">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="9909a-278">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <span data-ttu-id="9909a-279"><a name="so"></a> ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="9909a-279"><a name="so"></a> ShowOutlining</span></span>
  <span data-ttu-id="9909a-280">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-280">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-281">Especifica se o painel de Script exibe colchetes expansíveis e recolhíveis próximos às seções de código na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="9909a-281">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="9909a-282">Quando eles são exibidos, você pode clicar nos ícones de subtração \(-\) ao lado de um bloco de texto para recolhê-los ou clicar no ícone de adição \(+\) para expandir um bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="9909a-282">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="9909a-283">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="9909a-283">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <span data-ttu-id="9909a-284"><a name="stb"></a> ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="9909a-284"><a name="stb"></a> ShowToolBar</span></span>
  <span data-ttu-id="9909a-285">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-286">Especifica se a barra de ferramentas ISE aparece na parte superior da janela de ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9909a-286">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="9909a-287">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="9909a-287">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <span data-ttu-id="9909a-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="9909a-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="9909a-289">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-289">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-290">Especifica se uma mensagem de aviso aparece quando um script é salvo automaticamente antes de ser executado.</span><span class="sxs-lookup"><span data-stu-id="9909a-290">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="9909a-291">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="9909a-291">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <span data-ttu-id="9909a-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="9909a-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="9909a-293">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-293">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-294">Especifica se uma mensagem de aviso aparece quando o mesmo arquivo é aberto em diferentes guias do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9909a-294">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="9909a-295">Se definida como **$true**, para abrir o mesmo arquivo em várias guias exibe a mensagem: "Uma cópia deste arquivo está aberta em outra guia do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9909a-295">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab.</span></span> <span data-ttu-id="9909a-296">As alterações feitas neste arquivo afetarão todas as cópias abertas".</span><span class="sxs-lookup"><span data-stu-id="9909a-296">Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="9909a-297">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="9909a-297">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <span data-ttu-id="9909a-298"><a name="tc"></a> TokenColors</span><span class="sxs-lookup"><span data-stu-id="9909a-298"><a name="tc"></a> TokenColors</span></span>
  <span data-ttu-id="9909a-299">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-299">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-300">Especifica as cores de tokens do IntelliSense no painel de script do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9909a-300">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="9909a-301">Essa propriedade é um objeto de dicionário que contém pares de nome/valor de tipos de token e cores para o painel Script.</span><span class="sxs-lookup"><span data-stu-id="9909a-301">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="9909a-302">Para alterar as cores dos tokens IntelliSense no painel de Console, consulte [ConsoleTokenColors](#contc).</span><span class="sxs-lookup"><span data-stu-id="9909a-302">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#contc).</span></span> <span data-ttu-id="9909a-303">Para redefinir as cores aos valores padrão, consulte [RestoreDefaultTokenColors()](#rdtc).</span><span class="sxs-lookup"><span data-stu-id="9909a-303">To reset the colors to the default values, see [RestoreDefaultTokenColors()](#rdtc).</span></span> <span data-ttu-id="9909a-304">As cores do token podem ser definidas para o seguinte: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="9909a-304">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="9909a-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="9909a-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="9909a-306">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-306">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-307">Especifica se você pode usar a tecla Enter para selecionar uma opção IntelliSense fornecida no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-307">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="9909a-308">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="9909a-308">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <span data-ttu-id="9909a-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="9909a-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="9909a-310">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-310">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-311">Especifica se você pode usar a tecla Enter para selecionar uma opção IntelliSense fornecida no painel Script.</span><span class="sxs-lookup"><span data-stu-id="9909a-311">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="9909a-312">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="9909a-312">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <span data-ttu-id="9909a-313"><a name="ulh"></a> UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="9909a-313"><a name="ulh"></a> UseLocalHelp</span></span>
  <span data-ttu-id="9909a-314">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-314">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-315">Especifica se a Ajuda instalada localmente ou a Ajuda da biblioteca do TechNet online aparece quando você pressiona F1 com o cursor posicionado em uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9909a-315">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="9909a-316">Se definida como **$true**, uma janela pop-up mostra o conteúdo da Ajuda instalada localmente.</span><span class="sxs-lookup"><span data-stu-id="9909a-316">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="9909a-317">Você pode instalar os arquivos de Ajuda, executando o comando `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="9909a-317">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="9909a-318">Se definido como **$false**, seu navegador abrirá uma página na biblioteca do TechNet.</span><span class="sxs-lookup"><span data-stu-id="9909a-318">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <span data-ttu-id="9909a-319"><a name="vbc"></a> VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-319"><a name="vbc"></a> VerboseBackgroundColor</span></span>
  <span data-ttu-id="9909a-320">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-320">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-321">Especifica a cor da tela de fundo para o texto detalhado que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-321">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="9909a-322">É um objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-322">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="9909a-323"><a name="vfc"></a> VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-323"><a name="vfc"></a> VerboseForegroundColor</span></span>
  <span data-ttu-id="9909a-324">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-324">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-325">Especifica a cor de primeiro plano para o texto detalhado que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-325">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="9909a-326">É um objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-326">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <span data-ttu-id="9909a-327"><a name="wbc"></a> WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-327"><a name="wbc"></a> WarningBackgroundColor</span></span>
  <span data-ttu-id="9909a-328">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-328">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-329">Especifica a cor da tela de fundo para o texto de aviso que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="9909a-329">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="9909a-330">É um objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-330">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="9909a-331"><a name="wfc"></a> WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="9909a-331"><a name="wfc"></a> WarningForegroundColor</span></span>
  <span data-ttu-id="9909a-332">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-332">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="9909a-333">Especifica a cor de primeiro plano para o texto detalhado que aparece no painel de Saída.</span><span class="sxs-lookup"><span data-stu-id="9909a-333">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="9909a-334">É um objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="9909a-334">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <span data-ttu-id="9909a-335"><a name="xtc"></a> XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="9909a-335"><a name="xtc"></a> XmlTokenColors</span></span>
  <span data-ttu-id="9909a-336">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-336">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-337">Especifica um objeto de dicionário que contém pares de nome/valor de tipos e cores de token para o conteúdo XML exibido no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9909a-337">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="9909a-338">As cores do token podem ser definidas para o seguinte: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="9909a-338">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="9909a-339">Veja também [RestoreDefaultXmlTokenColors()](#rdxtc).</span><span class="sxs-lookup"><span data-stu-id="9909a-339">Also see [RestoreDefaultXmlTokenColors()](#rdxtc).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <span data-ttu-id="9909a-340"><a name="z"></a> Zoom</span><span class="sxs-lookup"><span data-stu-id="9909a-340"><a name="z"></a> Zoom</span></span>
  <span data-ttu-id="9909a-341">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9909a-341">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="9909a-342">Especifica o tamanho relativo do texto, nos painéis de Console e Script.</span><span class="sxs-lookup"><span data-stu-id="9909a-342">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="9909a-343">O valor padrão é 100.</span><span class="sxs-lookup"><span data-stu-id="9909a-343">The default value is 100.</span></span> <span data-ttu-id="9909a-344">Valores menores podem fazer com que o texto no ISE do Windows PowerShell pareça menor, enquanto números maiores fazem com que o texto pareça maior.</span><span class="sxs-lookup"><span data-stu-id="9909a-344">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="9909a-345">O valor é um número inteiro que varia de 20 a 400.</span><span class="sxs-lookup"><span data-stu-id="9909a-345">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="9909a-346">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="9909a-346">See Also</span></span>
- [<span data-ttu-id="9909a-347">O modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9909a-347">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="9909a-348">Referência de modelo de objeto do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9909a-348">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

