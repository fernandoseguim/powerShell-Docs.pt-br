---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: O objeto PowerShellTabCollection
ms.technology: powershell
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: 38bac3445fd94022f03c0f336bd17f9033dfedc2
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-powershelltabcollection-object"></a>O objeto PowerShellTabCollection
  O objeto da coleção **PowerShellTab** é uma coleção de objetos **PowerShellTab**. Cada objeto **PowerShellTab** funciona como um ambiente de tempo de execução separado. Ele é uma instância da classe Microsoft.PowerShell.Host.ISE.PowerShellTabs. Um exemplo é o objeto **$psISE.PowerShellTabs**.

## <a name="methods"></a>Métodos

### <a name="add"></a>Add\(\)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Adiciona uma nova guia do PowerShell à coleção. Retorna a guia recém-adicionada.

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Remove a guia especificada pelo parâmetro **psTab**.

 **psTab**
 A guia do PowerShell a ser removida.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Seleciona a guia do PowerShell que é especificada pelo parâmetro **psTab** para torná-la a guia ativa do PowerShell no momento.

 **psTab**
 A guia do PowerShell a ser selecionada.

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a>Consulte Também
- [O objeto PowerShellTab](The-PowerShellTab-Object.md) 
- [O modelo de objeto de script do ISE do Windows PowerShell](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do ISE do Windows PowerShell](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto do ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  
