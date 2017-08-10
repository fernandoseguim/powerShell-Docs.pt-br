---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: O objeto PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: d4e9374202d352a30b3eb46bcf1e4e40dea49822
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="662c9-103">O objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="662c9-103">The PowerShellTab Object</span></span>
  <span data-ttu-id="662c9-104">O objeto **PowerShellTab** representa um ambiente de tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="662c9-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="662c9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="662c9-105">Methods</span></span>

###  <span data-ttu-id="662c9-106"><a name="invoke"></a> Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="662c9-106"><a name="invoke"></a> Invoke\( Script \)</span></span>
  <span data-ttu-id="662c9-107">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="662c9-108">Executa o script determinado na guia PowerShell.</span><span class="sxs-lookup"><span data-stu-id="662c9-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="662c9-109">Esse método só funciona em outras guias do PowerShell, não na guia do PowerShell do qual ele é executado.</span><span class="sxs-lookup"><span data-stu-id="662c9-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="662c9-110">Ele não retorna nenhum objeto ou valor.</span><span class="sxs-lookup"><span data-stu-id="662c9-110">It does not return any object or value.</span></span> <span data-ttu-id="662c9-111">Se o código modificar qualquer variável, essas alterações persistirão na guia na qual o comando foi invocado.</span><span class="sxs-lookup"><span data-stu-id="662c9-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

 <span data-ttu-id="662c9-112">**Script** – System.Management.Automation.ScriptBlock ou Cadeia de caracteres, o bloco de script a ser executado.</span><span class="sxs-lookup"><span data-stu-id="662c9-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="662c9-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="662c9-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>
  <span data-ttu-id="662c9-114">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="662c9-115">Executa o script determinado na guia PowerShell.</span><span class="sxs-lookup"><span data-stu-id="662c9-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="662c9-116">Esse método só funciona em outras guias do PowerShell, não na guia do PowerShell do qual ele é executado.</span><span class="sxs-lookup"><span data-stu-id="662c9-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="662c9-117">O bloco de script é executado e qualquer valor que é devolvido do script é devolvido ao ambiente de execução do qual você invocou o comando.</span><span class="sxs-lookup"><span data-stu-id="662c9-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="662c9-118">Se o comando levar mais tempo para executar do que valor **millesecondsTimeout** especifica, o comando falhará com uma exceção: "A operação expirou".</span><span class="sxs-lookup"><span data-stu-id="662c9-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

 <span data-ttu-id="662c9-119">**Script** – System.Management.Automation.ScriptBlock ou Cadeia de caracteres, o bloco de script a ser executado.</span><span class="sxs-lookup"><span data-stu-id="662c9-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

 <span data-ttu-id="662c9-120">**\[useNewScope\]** – booliano opcional que assume como padrão **$true**
 Se definido como **$true**, um novo escopo será criado no qual executar o comando.</span><span class="sxs-lookup"><span data-stu-id="662c9-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true**
 If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="662c9-121">Ele não modifica o ambiente de tempo de execução da guia PowerShell que é especificada pelo comando.</span><span class="sxs-lookup"><span data-stu-id="662c9-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

 <span data-ttu-id="662c9-122">**\[[millisecondsTimeout]\]** – inteiro opcional padronizado para **500**.</span><span class="sxs-lookup"><span data-stu-id="662c9-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="662c9-123">Se o comando não terminar dentro do tempo especificado, gerará um **TimeoutException** com a mensagem "A operação atingiu o tempo limite".</span><span class="sxs-lookup"><span data-stu-id="662c9-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type “$x” to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a><span data-ttu-id="662c9-124">Propriedades</span><span class="sxs-lookup"><span data-stu-id="662c9-124">Properties</span></span>

###  <span data-ttu-id="662c9-125"><a name="AddOnsMenu"></a> AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="662c9-125"><a name="AddOnsMenu"></a> AddOnsMenu</span></span>
  <span data-ttu-id="662c9-126">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="662c9-127">A propriedade somente leitura que obtém o menu Complementos para a guia PowerShell.</span><span class="sxs-lookup"><span data-stu-id="662c9-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

###  <span data-ttu-id="662c9-128"><a name="CanExecute"></a> CanInvoke</span><span class="sxs-lookup"><span data-stu-id="662c9-128"><a name="CanExecute"></a> CanInvoke</span></span>
  <span data-ttu-id="662c9-129">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="662c9-130">A propriedade Boolean somente leitura que retornará um valor **$true** se um script puder ser invocado com o método [Invoke( Script )](#invoke).</span><span class="sxs-lookup"><span data-stu-id="662c9-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke) method.</span></span>

```
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab. 
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psise.PowerShellTabs[1] 
$secondTab.CanInvoke 
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke

```

###  <span data-ttu-id="662c9-131"><a name="Commandpane"></a> Consolepane</span><span class="sxs-lookup"><span data-stu-id="662c9-131"><a name="Commandpane"></a> Consolepane</span></span>
  <span data-ttu-id="662c9-132">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="662c9-133">No ISE do Windows PowerShell 2.0 isso foi chamado de **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="662c9-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

 <span data-ttu-id="662c9-134">A propriedade somente leitura que obtém o objeto [editor](../ise/The-ISEEditor-Object.md) do painel Console.</span><span class="sxs-lookup"><span data-stu-id="662c9-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

###  <span data-ttu-id="662c9-135"><a name="Displayname"></a> DisplayName</span><span class="sxs-lookup"><span data-stu-id="662c9-135"><a name="Displayname"></a> DisplayName</span></span>
  <span data-ttu-id="662c9-136">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="662c9-137">A propriedade de leitura/leitura que obtém ou define o texto exibido na guia PowerShell.</span><span class="sxs-lookup"><span data-stu-id="662c9-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab.</span></span> <span data-ttu-id="662c9-138">Por padrão, as guias são denominadas "PowerShell #", em que # representa um número.</span><span class="sxs-lookup"><span data-stu-id="662c9-138">By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

###  <span data-ttu-id="662c9-139"><a name="ExpandedScript"></a> ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="662c9-139"><a name="ExpandedScript"></a> ExpandedScript</span></span>
  <span data-ttu-id="662c9-140">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="662c9-141">A propriedade Boolean de leitura/gravação que determina se o painel Script será expandido ou ocultado.</span><span class="sxs-lookup"><span data-stu-id="662c9-141">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

###  <span data-ttu-id="662c9-142"><a name="Files"></a> Files</span><span class="sxs-lookup"><span data-stu-id="662c9-142"><a name="Files"></a> Files</span></span>
  <span data-ttu-id="662c9-143">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="662c9-144">A propriedade somente leitura que obtém a [coleção de arquivos de script](../ise/The-ISEFileCollection-Object.md) abertos na guia PowerShell.</span><span class="sxs-lookup"><span data-stu-id="662c9-144">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

###  <span data-ttu-id="662c9-145"><a name="Output"></a> Output</span><span class="sxs-lookup"><span data-stu-id="662c9-145"><a name="Output"></a> Output</span></span>
  <span data-ttu-id="662c9-146">Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.</span><span class="sxs-lookup"><span data-stu-id="662c9-146">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="662c9-147">Em versões mais recentes do ISE do Windows PowerShell, você pode usar o objeto **ConsolePane** para os mesmos fins.</span><span class="sxs-lookup"><span data-stu-id="662c9-147">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

 <span data-ttu-id="662c9-148">A propriedade somente leitura que obtém o Painel de saída do [editor](../ise/The-ISEEditor-Object.md) atual.</span><span class="sxs-lookup"><span data-stu-id="662c9-148">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

###  <span data-ttu-id="662c9-149"><a name="Prompt"></a> Prompt</span><span class="sxs-lookup"><span data-stu-id="662c9-149"><a name="Prompt"></a> Prompt</span></span>
  <span data-ttu-id="662c9-150">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-150">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="662c9-151">A propriedade somente leitura que obtém o atual texto de solicitação.</span><span class="sxs-lookup"><span data-stu-id="662c9-151">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="662c9-152">Observação: a função **Prompt** pode ser substituído pelo perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="662c9-152">Note: the **Prompt** function can be overridden by the user’s profile.</span></span> <span data-ttu-id="662c9-153">Se o resultado for diferente de uma cadeia simples, essa propriedade não retornará nada.</span><span class="sxs-lookup"><span data-stu-id="662c9-153">If the result is other than a simple string, then this property returns nothing.</span></span>

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

###  <span data-ttu-id="662c9-154"><a name="ShowCommands"></a> ShowCommands</span><span class="sxs-lookup"><span data-stu-id="662c9-154"><a name="ShowCommands"></a> ShowCommands</span></span>
  <span data-ttu-id="662c9-155">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="662c9-156">A propriedade de leitura/gravação que indica se o Painel de comandos está sendo exibido no momento.</span><span class="sxs-lookup"><span data-stu-id="662c9-156">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

###  <span data-ttu-id="662c9-157"><a name="StatusText"></a> StatusText</span><span class="sxs-lookup"><span data-stu-id="662c9-157"><a name="StatusText"></a> StatusText</span></span>
  <span data-ttu-id="662c9-158">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="662c9-159">A propriedade somente leitura que obtém o texto do status **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="662c9-159">The read-only property that gets the **PowerShellTab** status text.</span></span>

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

###  <span data-ttu-id="662c9-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="662c9-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span></span>
  <span data-ttu-id="662c9-161">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-161">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="662c9-162">A propriedade somente leitura que indica se o painel de ferramentas horizontal Complementos está aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="662c9-162">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

###  <span data-ttu-id="662c9-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span><span class="sxs-lookup"><span data-stu-id="662c9-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span></span>
  <span data-ttu-id="662c9-164">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="662c9-164">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="662c9-165">A propriedade somente leitura que indica se o painel de ferramentas vertical Complementos está aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="662c9-165">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="662c9-166">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="662c9-166">See Also</span></span>
- [<span data-ttu-id="662c9-167">O objeto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="662c9-167">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md) 
- [<span data-ttu-id="662c9-168">O modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="662c9-168">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="662c9-169">Referência de modelo de objeto do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="662c9-169">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="662c9-170">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="662c9-170">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
