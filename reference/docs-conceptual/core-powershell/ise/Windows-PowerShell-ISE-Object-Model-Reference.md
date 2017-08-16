---
ms.date: 2017-06-05T00:00:00.000Z
keywords: PowerShell, cmdlet
title: "Referência de modelo de objeto do ISE do Windows PowerShell"
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: e5d4ae03158d9b5b0efd98db1272bc13872181ac
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2017
---
# <a name="windows-powershell-ise-object-model-reference"></a>Referência de modelo de objeto do ISE do Windows PowerShell
  
## <a name="object-model-reference"></a>Referência de modelo de objeto
 Esta seção fornece uma referência sobre as classes subjacentes que definem os vários objetos no ISE (Ambiente de Script Integrado) do Windows PowerShell®. Para ver os objetos organizados em sua hierarquia, consulte [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md) (A hierarquia do modelo de objeto ISE).

 [O objeto ISEAddOnTool](The-ISEAddOnTool-Object.md) Exemplos: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.

 [The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) [O objeto ISEEditor](The-ISEEditor-Object.md) Exemplos: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.

 [O objeto ISEFile](The-ISEFile-Object.md) Exemplos: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].

 [O objeto ISEFileCollection](The-ISEFileCollection-Object.md) Exemplos: $psISE.PowerShellTabs.Files.

 [O objeto ISEMenuItem](The-ISEMenuItem-Object.md) Exemplos: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].

 [O objeto ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) exemplo: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.

 [O objeto ISEOptions](The-ISEOptions-Object.md) Exemplos: $psISE.Options, $psISE.Options.DefaultOptions.

 [O objeto ObjectModelRoot](The-ObjectModelRoot-Object.md) Exemplo: o objeto $psISE raiz.

 [O objeto PowerShellTab](The-PowerShellTab-Object.md) Exemplos: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].

 [O objeto PowerShellTabCollection](The-PowerShellTabCollection-Object.md) Example: $psISE.PowerShellTabs.

## <a name="see-also"></a>Consulte Também
- [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
