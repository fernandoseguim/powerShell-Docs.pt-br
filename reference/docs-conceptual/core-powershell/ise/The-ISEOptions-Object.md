---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: O objeto ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953643"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="8ff7c-103">O objeto ISEOptions</span><span class="sxs-lookup"><span data-stu-id="8ff7c-103">The ISEOptions Object</span></span>

<span data-ttu-id="8ff7c-104">O objeto **ISEOptions** representa várias configurações para o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="8ff7c-105">Ele é uma instância da classe **Microsoft.PowerShell.Host.ISE.ISEOptions**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="8ff7c-106">O objeto **ISEOptions** fornece os seguintes métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="8ff7c-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="8ff7c-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="8ff7c-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="8ff7c-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="8ff7c-109">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-110">Restaura os valores padrão das cores do token no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="8ff7c-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="8ff7c-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="8ff7c-112">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-113">Restaura os valores padrão das cores de todas as configurações de opções no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="8ff7c-114">Ele também redefine o comportamento de várias mensagens de aviso que fornecem a caixa de seleção padrão para impedir que a mensagem seja mostrada novamente.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="8ff7c-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="8ff7c-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="8ff7c-116">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-117">Restaura os valores padrão das cores do token no painel de script.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="8ff7c-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="8ff7c-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="8ff7c-119">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-120">Restaura os valores padrão das cores do token para elementos XML exibidos no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="8ff7c-121">Consulte também [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="8ff7c-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="8ff7c-122">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8ff7c-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="8ff7c-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="8ff7c-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="8ff7c-124">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-125">Especifica o número de minutos entre as operações de salvamento automático de seus arquivos pelo ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="8ff7c-126">O valor padrão é 2 minutos.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-126">The default value is 2 minutes.</span></span> <span data-ttu-id="8ff7c-127">O valor é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="8ff7c-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="8ff7c-129">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="8ff7c-130">Para versões posteriores, consulte [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="8ff7c-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="8ff7c-131">Especifica a cor da tela de fundo para o painel de comando.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="8ff7c-132">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="8ff7c-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="8ff7c-133">CommandPaneUp</span></span>

<span data-ttu-id="8ff7c-134">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="8ff7c-135">Especifica se o painel de comando está localizado acima do painel de saída.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="8ff7c-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="8ff7c-137">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-138">Especifica a cor da tela de fundo do painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="8ff7c-139">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="8ff7c-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="8ff7c-141">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-142">Especifica a cor de primeiro plano do texto no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="8ff7c-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="8ff7c-144">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-145">Especifica a cor da tela de fundo do texto no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="8ff7c-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="8ff7c-146">ConsoleTokenColors</span></span>

<span data-ttu-id="8ff7c-147">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-148">Especifica as cores dos tokens do IntelliSense no painel de Console de ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="8ff7c-149">Essa propriedade é um objeto de dicionário que contém pares de nome/valor de tipos de token e cores para o painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="8ff7c-150">Para alterar as cores dos tokens do IntelliSense no painel de Script, consulte [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="8ff7c-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="8ff7c-151">Para redefinir as cores aos valores padrão, consulte [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="8ff7c-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="8ff7c-152">As cores do token podem ser definidas para o seguinte: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="8ff7c-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-153">DebugBackgroundColor</span></span>

<span data-ttu-id="8ff7c-154">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-155">Especifica a cor da tela de fundo para o texto de depuração que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="8ff7c-156">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="8ff7c-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-157">DebugForegroundColor</span></span>

<span data-ttu-id="8ff7c-158">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-159">Especifica a cor de primeiro plano para o texto de depuração que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="8ff7c-160">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="8ff7c-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="8ff7c-161">DefaultOptions</span></span>

<span data-ttu-id="8ff7c-162">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-163">Uma coleção de propriedades que especificam os valores padrão a serem usados quando os métodos Reset são usados.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```powershell
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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="8ff7c-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="8ff7c-165">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-166">Especifica a cor da tela de fundo para o texto de erro que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="8ff7c-167">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="8ff7c-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-168">ErrorForegroundColor</span></span>

<span data-ttu-id="8ff7c-169">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-170">Especifica a cor de primeiro plano para o texto de erro que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="8ff7c-171">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="8ff7c-172">FontName</span><span class="sxs-lookup"><span data-stu-id="8ff7c-172">FontName</span></span>

<span data-ttu-id="8ff7c-173">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-174">Especifica o nome da fonte atualmente em uso, tanto no painel do Script quanto no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="8ff7c-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="8ff7c-175">FontSize</span></span>

<span data-ttu-id="8ff7c-176">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-177">Especifica o tamanho da fonte como um inteiro.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="8ff7c-178">Ele é usado no painel de Script, no painel de Comando e no painel de Saída.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="8ff7c-179">O intervalo de valores válidos é de 8 a 32.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="8ff7c-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="8ff7c-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="8ff7c-181">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-182">Especifica o número de segundos que IntelliSense usa para tentar resolver o texto atualmente digitado.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="8ff7c-183">Após esse número de segundos, o IntelliSense expira e permite que você continue digitando.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="8ff7c-184">O valor padrão é de 3 segundos.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-184">The default value is 3 seconds.</span></span> <span data-ttu-id="8ff7c-185">O valor é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="8ff7c-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="8ff7c-186">MruCount</span></span>

<span data-ttu-id="8ff7c-187">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-188">Especifica o número de arquivos abertos recentemente que o ISE do Windows PowerShell acompanha e exibe na parte inferior do menu **Abrir Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="8ff7c-189">O valor padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-189">The default value is 10.</span></span> <span data-ttu-id="8ff7c-190">O valor é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="8ff7c-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="8ff7c-192">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="8ff7c-193">Para versões posteriores, consulte [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="8ff7c-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="8ff7c-194">A propriedade de leitura/gravação que obtém ou define a cor da tela de fundo para o Painel de saída em si.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="8ff7c-195">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="8ff7c-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="8ff7c-197">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="8ff7c-198">Para versões posteriores, consulte [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="8ff7c-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="8ff7c-199">A propriedade de leitura/gravação que muda a cor do primeiro plano do texto no Painel de saída no ISE do Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="8ff7c-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="8ff7c-201">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="8ff7c-202">Para versões posteriores, consulte [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="8ff7c-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="8ff7c-203">A propriedade de leitura/gravação que muda a cor da tela de fundo do texto no painel Saída.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="8ff7c-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="8ff7c-205">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-206">A propriedade de leitura/gravação que obtém ou define a cor da tela de fundo dos arquivos.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="8ff7c-207">É uma instância da classe **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="8ff7c-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="8ff7c-209">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-210">A propriedade de leitura/gravação que obtém ou define a cor de primeiro plano de arquivos de não script no painel Script.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="8ff7c-211">Para definir a cor de primeiro plano dos arquivos de script, use [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="8ff7c-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="8ff7c-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="8ff7c-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="8ff7c-213">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-214">A propriedade de leitura/gravação que obtém ou define a posição do painel Script no visor.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="8ff7c-215">A cadeia de caracteres pode ser "Maximizada", "Na parte superior" ou à "Direita".</span><span class="sxs-lookup"><span data-stu-id="8ff7c-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="8ff7c-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="8ff7c-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="8ff7c-217">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-218">Especifica se a lista **Ctrl+J** dos trechos de código inclui o conjunto inicial que está incluído no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="8ff7c-219">Quando definido como **$false**, somente trechos de código definidos pelo usuário aparecem na lista **Ctrl+J**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="8ff7c-220">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-220">The default value is **$true**.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="8ff7c-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="8ff7c-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="8ff7c-222">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-223">Especifica se o IntelliSense oferece sugestões de sintaxe, parâmetro e valor no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="8ff7c-224">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-224">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="8ff7c-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="8ff7c-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="8ff7c-226">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-227">Especifica se o IntelliSense oferece sugestões de sintaxe, parâmetro e valor no painel do Script.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="8ff7c-228">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-228">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="8ff7c-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="8ff7c-229">ShowLineNumbers</span></span>

<span data-ttu-id="8ff7c-230">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-231">Especifica se o painel de Script exibe os números de linha na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="8ff7c-232">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-232">The default value is **$true**.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="8ff7c-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="8ff7c-233">ShowOutlining</span></span>

<span data-ttu-id="8ff7c-234">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-235">Especifica se o painel de Script exibe colchetes expansíveis e recolhíveis próximos às seções de código na margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="8ff7c-236">Quando eles são exibidos, você pode clicar nos ícones de subtração \(-\) ao lado de um bloco de texto para recolhê-los ou clicar no ícone de adição \(+\) para expandir um bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="8ff7c-237">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-237">The default value is **$true**.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="8ff7c-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="8ff7c-238">ShowToolBar</span></span>

<span data-ttu-id="8ff7c-239">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-240">Especifica se a barra de ferramentas ISE aparece na parte superior da janela de ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="8ff7c-241">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-241">The default value is **$true**.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="8ff7c-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="8ff7c-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="8ff7c-243">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-244">Especifica se uma mensagem de aviso aparece quando um script é salvo automaticamente antes de ser executado.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="8ff7c-245">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-245">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="8ff7c-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="8ff7c-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="8ff7c-247">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-248">Especifica se uma mensagem de aviso aparece quando o mesmo arquivo é aberto em diferentes guias do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="8ff7c-249">Se definida como **$true**, para abrir o mesmo arquivo em várias guias exibe a mensagem: "Uma cópia deste arquivo está aberta em outra guia do Windows PowerShell. As alterações feitas neste arquivo afetarão todas as cópias abertas".</span><span class="sxs-lookup"><span data-stu-id="8ff7c-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="8ff7c-250">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-250">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="8ff7c-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="8ff7c-251">TokenColors</span></span>

<span data-ttu-id="8ff7c-252">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-253">Especifica as cores de tokens do IntelliSense no painel de script do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="8ff7c-254">Essa propriedade é um objeto de dicionário que contém pares de nome/valor de tipos de token e cores para o painel Script.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="8ff7c-255">Para alterar as cores dos tokens IntelliSense no painel de Console, consulte [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="8ff7c-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="8ff7c-256">Para redefinir as cores aos valores padrão, consulte [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="8ff7c-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="8ff7c-257">As cores do token podem ser definidas para o seguinte: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="8ff7c-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="8ff7c-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="8ff7c-259">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-260">Especifica se você pode usar a tecla Enter para selecionar uma opção IntelliSense fornecida no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="8ff7c-261">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-261">The default value is **$true**.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="8ff7c-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="8ff7c-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="8ff7c-263">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-264">Especifica se você pode usar a tecla Enter para selecionar uma opção IntelliSense fornecida no painel Script.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="8ff7c-265">O valor padrão é **$true**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-265">The default value is **$true**.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="8ff7c-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="8ff7c-266">UseLocalHelp</span></span>

<span data-ttu-id="8ff7c-267">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-268">Especifica se a Ajuda instalada localmente ou a Ajuda da biblioteca do TechNet online aparece quando você pressiona F1 com o cursor posicionado em uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="8ff7c-269">Se definida como **$true**, uma janela pop-up mostra o conteúdo da Ajuda instalada localmente.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="8ff7c-270">Você pode instalar os arquivos de Ajuda, executando o comando `Update-Help`.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="8ff7c-271">Se definido como **$false**, seu navegador abrirá uma página na biblioteca do TechNet.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="8ff7c-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="8ff7c-273">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-274">Especifica a cor da tela de fundo para o texto detalhado que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="8ff7c-275">É um objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="8ff7c-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-276">VerboseForegroundColor</span></span>

<span data-ttu-id="8ff7c-277">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-278">Especifica a cor de primeiro plano para o texto detalhado que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="8ff7c-279">É um objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="8ff7c-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-280">WarningBackgroundColor</span></span>

<span data-ttu-id="8ff7c-281">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-282">Especifica a cor da tela de fundo para o texto de aviso que aparece no painel de Console.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="8ff7c-283">É um objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="8ff7c-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="8ff7c-284">WarningForegroundColor</span></span>

<span data-ttu-id="8ff7c-285">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8ff7c-286">Especifica a cor de primeiro plano para o texto detalhado que aparece no painel de Saída.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="8ff7c-287">É um objeto **System.Windows.Media.Color**.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="8ff7c-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="8ff7c-288">XmlTokenColors</span></span>

<span data-ttu-id="8ff7c-289">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-290">Especifica um objeto de dicionário que contém pares de nome/valor de tipos e cores de token para o conteúdo XML exibido no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="8ff7c-291">As cores do token podem ser definidas para o seguinte: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="8ff7c-292">Veja também [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="8ff7c-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="8ff7c-293">Zoom</span><span class="sxs-lookup"><span data-stu-id="8ff7c-293">Zoom</span></span>

<span data-ttu-id="8ff7c-294">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8ff7c-295">Especifica o tamanho relativo do texto, nos painéis de Console e Script.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="8ff7c-296">O valor padrão é 100.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-296">The default value is 100.</span></span> <span data-ttu-id="8ff7c-297">Valores menores podem fazer com que o texto no ISE do Windows PowerShell pareça menor, enquanto números maiores fazem com que o texto pareça maior.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="8ff7c-298">O valor é um número inteiro que varia de 20 a 400.</span><span class="sxs-lookup"><span data-stu-id="8ff7c-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="8ff7c-299">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8ff7c-299">See Also</span></span>

- [<span data-ttu-id="8ff7c-300">Objetivo do modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ff7c-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="8ff7c-301">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="8ff7c-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)