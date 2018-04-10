---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: O objeto PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: c10f9106e31bb05828f1e76554ebe40ddb778340
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="d912e-103">O objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="d912e-103">The PowerShellTab Object</span></span>

<span data-ttu-id="d912e-104">O objeto **PowerShellTab** representa um ambiente de tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d912e-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="d912e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d912e-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="d912e-106">Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="d912e-106">Invoke\( Script \)</span></span>

<span data-ttu-id="d912e-107">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d912e-108">Executa o script determinado na guia PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d912e-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="d912e-109">Esse método só funciona em outras guias do PowerShell, não na guia do PowerShell do qual ele é executado.</span><span class="sxs-lookup"><span data-stu-id="d912e-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="d912e-110">Ele não retorna nenhum objeto ou valor.</span><span class="sxs-lookup"><span data-stu-id="d912e-110">It does not return any object or value.</span></span> <span data-ttu-id="d912e-111">Se o código modificar qualquer variável, essas alterações persistirão na guia na qual o comando foi invocado.</span><span class="sxs-lookup"><span data-stu-id="d912e-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="d912e-112">**Script** – System.Management.Automation.ScriptBlock ou Cadeia de caracteres, o bloco de script a ser executado.</span><span class="sxs-lookup"><span data-stu-id="d912e-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="d912e-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="d912e-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="d912e-114">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d912e-115">Executa o script determinado na guia PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d912e-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="d912e-116">Esse método só funciona em outras guias do PowerShell, não na guia do PowerShell do qual ele é executado.</span><span class="sxs-lookup"><span data-stu-id="d912e-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="d912e-117">O bloco de script é executado e qualquer valor que é devolvido do script é devolvido ao ambiente de execução do qual você invocou o comando.</span><span class="sxs-lookup"><span data-stu-id="d912e-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="d912e-118">Se o comando levar mais tempo para executar do que valor **millesecondsTimeout** especifica, o comando falhará com uma exceção: "A operação expirou".</span><span class="sxs-lookup"><span data-stu-id="d912e-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="d912e-119">**Script** – System.Management.Automation.ScriptBlock ou Cadeia de caracteres, o bloco de script a ser executado.</span><span class="sxs-lookup"><span data-stu-id="d912e-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="d912e-120">**\[useNewScope\]** – Booliano Opcional cujo padrão é **$true** Se for definido como **$true**, um novo escopo será criado dentro do qual o comando será executado.</span><span class="sxs-lookup"><span data-stu-id="d912e-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true** If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="d912e-121">Ele não modifica o ambiente de tempo de execução da guia PowerShell que é especificada pelo comando.</span><span class="sxs-lookup"><span data-stu-id="d912e-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="d912e-122">**\[[millisecondsTimeout]\]** – inteiro opcional padronizado para **500**.</span><span class="sxs-lookup"><span data-stu-id="d912e-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="d912e-123">Se o comando não terminar dentro do tempo especificado, gerará um **TimeoutException** com a mensagem "A operação atingiu o tempo limite".</span><span class="sxs-lookup"><span data-stu-id="d912e-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a><span data-ttu-id="d912e-124">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d912e-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="d912e-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="d912e-125">AddOnsMenu</span></span>

<span data-ttu-id="d912e-126">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d912e-127">A propriedade somente leitura que obtém o menu Complementos para a guia PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d912e-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a><span data-ttu-id="d912e-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="d912e-128">CanInvoke</span></span>

<span data-ttu-id="d912e-129">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d912e-130">A propriedade Boolean somente leitura que retornará um valor **$true** se um script puder ser invocado com o método [Invoke( Script )](#invoke-script-).</span><span class="sxs-lookup"><span data-stu-id="d912e-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a><span data-ttu-id="d912e-131">Consolepane</span><span class="sxs-lookup"><span data-stu-id="d912e-131">Consolepane</span></span>

<span data-ttu-id="d912e-132">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="d912e-133">No ISE do Windows PowerShell 2.0 isso foi chamado de **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="d912e-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="d912e-134">A propriedade somente leitura que obtém o objeto [editor](../ise/The-ISEEditor-Object.md) do painel Console.</span><span class="sxs-lookup"><span data-stu-id="d912e-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="d912e-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d912e-135">DisplayName</span></span>

<span data-ttu-id="d912e-136">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d912e-137">A propriedade de leitura/leitura que obtém ou define o texto exibido na guia PowerShell. Por padrão, as guias são denominadas "PowerShell #", em que # representa um número.</span><span class="sxs-lookup"><span data-stu-id="d912e-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="d912e-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="d912e-138">ExpandedScript</span></span>

<span data-ttu-id="d912e-139">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d912e-140">A propriedade Boolean de leitura/gravação que determina se o painel Script será expandido ou ocultado.</span><span class="sxs-lookup"><span data-stu-id="d912e-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="d912e-141">Arquivos</span><span class="sxs-lookup"><span data-stu-id="d912e-141">Files</span></span>

<span data-ttu-id="d912e-142">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d912e-143">A propriedade somente leitura que obtém a [coleção de arquivos de script](../ise/The-ISEFileCollection-Object.md) abertos na guia PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d912e-143">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="d912e-144">Saída</span><span class="sxs-lookup"><span data-stu-id="d912e-144">Output</span></span>

<span data-ttu-id="d912e-145">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="d912e-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="d912e-146">Em versões mais recentes do ISE do Windows PowerShell, você pode usar o objeto **ConsolePane** para os mesmos fins.</span><span class="sxs-lookup"><span data-stu-id="d912e-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="d912e-147">A propriedade somente leitura que obtém o Painel de saída do [editor](../ise/The-ISEEditor-Object.md) atual.</span><span class="sxs-lookup"><span data-stu-id="d912e-147">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="d912e-148">Prompt</span><span class="sxs-lookup"><span data-stu-id="d912e-148">Prompt</span></span>

<span data-ttu-id="d912e-149">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d912e-150">A propriedade somente leitura que obtém o atual texto de solicitação.</span><span class="sxs-lookup"><span data-stu-id="d912e-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="d912e-151">Observação: a função **Prompt** pode ser substituída pelo perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="d912e-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="d912e-152">Se o resultado for diferente de uma cadeia simples, essa propriedade não retornará nada.</span><span class="sxs-lookup"><span data-stu-id="d912e-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="d912e-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="d912e-153">ShowCommands</span></span>

<span data-ttu-id="d912e-154">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d912e-155">A propriedade de leitura/gravação que indica se o Painel de comandos está sendo exibido no momento.</span><span class="sxs-lookup"><span data-stu-id="d912e-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="d912e-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="d912e-156">StatusText</span></span>

<span data-ttu-id="d912e-157">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d912e-158">A propriedade somente leitura que obtém o texto do status **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="d912e-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="d912e-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="d912e-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="d912e-160">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d912e-161">A propriedade somente leitura que indica se o painel de ferramentas horizontal Complementos está aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="d912e-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="d912e-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="d912e-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="d912e-163">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="d912e-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d912e-164">A propriedade somente leitura que indica se o painel de ferramentas vertical Complementos está aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="d912e-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="d912e-165">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d912e-165">See Also</span></span>

- [<span data-ttu-id="d912e-166">O objeto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="d912e-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="d912e-167">Objetivo do modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d912e-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d912e-168">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="d912e-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)