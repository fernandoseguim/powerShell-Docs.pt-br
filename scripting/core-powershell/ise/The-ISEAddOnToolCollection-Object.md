---
title: O objeto ISEAddOnToolCollection
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
---
# O objeto ISEAddOnToolCollection
  O objeto **ISEAddOnToolCollection** é uma coleção de objetos **ISEAddOnTool**. Um exemplo é o objeto **$psISE.CurrentPowerShellTab.VerticalAddOnTools**.

## Métodos

### Add( Name, ControlType, [IsVisible] )
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 Adiciona uma nova ferramenta complementar à coleção. Retorna a ferramenta complementar recém-adicionada. Antes de executar esse comando, você deve instalar a ferramenta complementar no computador local e carregar o assembly.

 **Name** – Cadeia de caracteres
 Especifica o nome de exibição da ferramenta complementar que é adicionada ao ISE do Windows PowerShell.

 **ControlType** – Tipo
 Especifica o controle que é adicionado.

 **[IsVisible]** – Booliano opcional
 Se definido como **$true**, a ferramenta complementar será imediatamente visível no painel de ferramentas associadas.

```
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)

```

### Remove( Item )
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 Remove a ferramenta complementar especificada da coleção.

 **Item** – Microsoft.PowerShell.Host.ISE.ISEAddOnTool
 Especifica o objeto a ser removido do ISE do Windows PowerShell.

```
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)

```

### SetSelectedPowerShellTab( psTab )
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 Seleciona a guia do PowerShell que o parâmetro **psTab** especifica.

 **psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab
 A guia do PowerShell a ser selecionada.

```

      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"

```

### Remove( psTab )
  Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores. 

 Remove a guia do PowerShell que o parâmetro **psTab** especifica.

 **psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab
 A guia do PowerShell a ser removida.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## Consulte Também
 [O objeto PowerShellTab](The-PowerShellTab-Object.md) 
 [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [A hierarquia de modelo do objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


