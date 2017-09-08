---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: O objeto PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 482984272b2f1be027cf2be49bdfa2c6e2c52070
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2017
---
# <a name="the-powershelltab-object"></a>O objeto PowerShellTab
  O objeto **PowerShellTab** representa um ambiente de tempo de execução do Windows PowerShell.

## <a name="methods"></a>Métodos

### <a name="invoke-script-"></a>Invoke\( Script \)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Executa o script determinado na guia PowerShell.

> [!NOTE]
>  Esse método só funciona em outras guias do PowerShell, não na guia do PowerShell do qual ele é executado. Ele não retorna nenhum objeto ou valor. Se o código modificar qualquer variável, essas alterações persistirão na guia na qual o comando foi invocado.

 **Script** – System.Management.Automation.ScriptBlock ou Cadeia de caracteres, o bloco de script a ser executado.

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 Executa o script determinado na guia PowerShell.

> [!NOTE]
>  Esse método só funciona em outras guias do PowerShell, não na guia do PowerShell do qual ele é executado. O bloco de script é executado e qualquer valor que é devolvido do script é devolvido ao ambiente de execução do qual você invocou o comando. Se o comando levar mais tempo para executar do que valor **millesecondsTimeout** especifica, o comando falhará com uma exceção: "A operação expirou".

 **Script** – System.Management.Automation.ScriptBlock ou Cadeia de caracteres, o bloco de script a ser executado.

 **\[useNewScope\]** – Booliano Opcional cujo padrão é **$true** Se for definido como **$true**, um novo escopo será criado dentro do qual o comando será executado. Ele não modifica o ambiente de tempo de execução da guia PowerShell que é especificada pelo comando.

 **\[[millisecondsTimeout]\]** – inteiro opcional padronizado para **500**.
Se o comando não terminar dentro do tempo especificado, gerará um **TimeoutException** com a mensagem "A operação atingiu o tempo limite".

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type â€œ$xâ€ to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a>Propriedades

### <a name="addonsmenu"></a>AddOnsMenu
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o menu Complementos para a guia PowerShell.

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

### <a name="caninvoke"></a>CanInvoke
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade Boolean somente leitura que retornará um valor **$true** se um script puder ser invocado com o método [Invoke( Script )]().

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

### <a name="consolepane"></a>Consolepane
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.  No ISE do Windows PowerShell 2.0 isso foi chamado de **CommandPane**.

 A propriedade somente leitura que obtém o objeto [editor](../ise/The-ISEEditor-Object.md) do painel Console.

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

### <a name="displayname"></a>DisplayName
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade de leitura/leitura que obtém ou define o texto exibido na guia PowerShell. Por padrão, as guias são denominadas "PowerShell #", em que # representa um número.

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="expandedscript"></a>ExpandedScript
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade Boolean de leitura/gravação que determina se o painel Script será expandido ou ocultado.

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

### <a name="files"></a>Arquivos
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a [coleção de arquivos de script](../ise/The-ISEFileCollection-Object.md) abertos na guia PowerShell.

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Saída
  Esse recurso está presente no ISE do Windows PowerShell 2.0, mas foi removido ou renomeado em versões posteriores do ISE.  Em versões mais recentes do ISE do Windows PowerShell, você pode usar o objeto **ConsolePane** para os mesmos fins.

 A propriedade somente leitura que obtém o Painel de saída do [editor](../ise/The-ISEEditor-Object.md) atual.

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Prompt
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o atual texto de solicitação. Observação: a função **Prompt** pode ser substituída pelo perfil do usuário. Se o resultado for diferente de uma cadeia simples, essa propriedade não retornará nada.

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 A propriedade de leitura/gravação que indica se o Painel de comandos está sendo exibido no momento.

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

### <a name="statustext"></a>StatusText
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o texto do status **PowerShellTab**.

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 A propriedade somente leitura que indica se o painel de ferramentas horizontal Complementos está aberto no momento.

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 A propriedade somente leitura que indica se o painel de ferramentas vertical Complementos está aberto no momento.

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Consulte Também
- [O objeto PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 
- [O modelo de objeto de script do ISE do Windows PowerShell](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do ISE do Windows PowerShell](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto do ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  
