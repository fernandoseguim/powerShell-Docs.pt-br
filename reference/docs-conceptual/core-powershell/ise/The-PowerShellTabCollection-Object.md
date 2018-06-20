---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: O objeto PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953065"
---
# <a name="the-powershelltabcollection-object"></a>O objeto PowerShellTabCollection

O objeto da coleção **PowerShellTab** é uma coleção de objetos **PowerShellTab**. Cada objeto **PowerShellTab** funciona como um ambiente de tempo de execução separado. Ele é uma instância da classe Microsoft.PowerShell.Host.ISE.PowerShellTabs. Um exemplo é o objeto **$psISE.PowerShellTabs**.

## <a name="methods"></a>Métodos

### <a name="add"></a>Add\(\)

Suportado no Windows PowerShell ISE 2.0 e posteriores.

Adiciona uma nova guia do PowerShell à coleção. Retorna a guia recém-adicionada.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Suportado no Windows PowerShell ISE 2.0 e posteriores.

Remove a guia especificada pelo parâmetro **psTab**.

**psTab** A guia do PowerShell a ser removida.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

Suportado no Windows PowerShell ISE 2.0 e posteriores.

Seleciona a guia do PowerShell que é especificada pelo parâmetro **psTab** para torná-la a guia ativa do PowerShell no momento.

**psTab** A guia do PowerShell a ser selecionada.

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a>Consulte Também

- [O objeto PowerShellTab](The-PowerShellTab-Object.md)
- [Objetivo do modelo de objeto de script do ISE do Windows PowerShell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [A hierarquia de modelo de objeto do ISE](The-ISE-Object-Model-Hierarchy.md)