---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: O objeto ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseaddontoolcollection-object"></a>O objeto ISEAddOnToolCollection

O objeto **ISEAddOnToolCollection** é uma coleção de objetos **ISEAddOnTool**. Um exemplo é o objeto **$psISE.CurrentPowerShellTab.VerticalAddOnTools**.

## <a name="methods"></a>Métodos

### <a name="add-name-controltype-isvisible-"></a>Add\( Name, ControlType, \[IsVisible\] \)

Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.

Adiciona uma nova ferramenta complementar à coleção. Retorna a ferramenta complementar recém-adicionada. Antes de executar esse comando, você deve instalar a ferramenta complementar no computador local e carregar o assembly.

**Name** – cadeia de caracteres, especifica o nome de exibição da ferramenta complementar que é adicionada ao ISE do Windows PowerShell.

**ControlType** – Tipo, especifica o controle que é adicionado.

**\[IsVisible\]** – Booliano opcional, se for definido como **$true**, a ferramenta complementar ficará imediatamente visível no painel de ferramentas associado.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Remove\( Item \)

Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.

Remove a ferramenta complementar especificada da coleção.

**Item** – Microsoft.PowerShell.Host.ISE.ISEAddOnTool, especifica o objeto a ser removido do ISE do Windows PowerShell.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.

Seleciona a guia do PowerShell que o parâmetro **psTab** especifica.

**psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab, a guia PowerShell a ser selecionada.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Remove\( psTab \)

Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.

Remove a guia do PowerShell que o parâmetro **psTab** especifica.

**psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab, a guia PowerShell a ser removida.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Consulte Também

- [O objeto PowerShellTab](The-PowerShellTab-Object.md)
- [Objetivo do modelo de objeto de script do ISE do Windows PowerShell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [A hierarquia de modelo de objeto do ISE](The-ISE-Object-Model-Hierarchy.md)