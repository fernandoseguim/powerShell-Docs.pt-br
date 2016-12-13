---
title: O objeto PowerShellTabCollection
ms.date: 2016-05-11
keywords: PowerShell, cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: 79edc4e41522b187cd6421be0bd897663b42bb44
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
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

  
