---
title: "Referência de modelo de objeto do ISE do Windows PowerShell"
ms.date: 2016-05-11
keywords: PowerShell, cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
translationtype: Human Translation
ms.sourcegitcommit: 6c666e2e23cb74818e37293410dafc9033057733
ms.openlocfilehash: bc65c69906a514a2490e6e7144a0cd4f377bec16

---

# Referência de modelo de objeto do ISE do Windows PowerShell
  
## Referência de modelo de objeto
 Esta seção fornece uma referência sobre as classes subjacentes que definem os vários objetos no ISE (Ambiente de Script Integrado) do Windows PowerShell®. Para ver os objetos organizados em sua hierarquia, consulte [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md) (A hierarquia do modelo de objeto ISE).

 [O objeto ISEAddOnTool](The-ISEAddOnTool-Object.md)
 Exemplos: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.

 [O objeto ISEAddOnTool](The-ISEAddOnTool-Object.md)
  [O Objeto ISEEditor](The-ISEEditor-Object.md)
 Exemplos: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.

 [O objeto ISEFile](The-ISEFile-Object.md)
 Exemplos: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].

 [O Objeto ISEFileCollection](The-ISEFileCollection-Object.md)
 Exemplos: $psISE.PowerShellTabs.Files.

 [O Objeto ISEMenuItem](The-ISEMenuItem-Object.md)
 Exemplos: $psISE.CurrentPowerShellTab.AddOnsMenu, $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].

 [O objeto ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md)
 Exemplo: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.

 [O objeto ISEOptions](The-ISEOptions-Object.md)
 Exemplos: $psISE.Options, $psISE.Options.DefaultOptions.

 [O objeto ObjectModelRoot](The-ObjectModelRoot-Object.md)
 Exemplo: O objeto raiz $psISE.

 [O objeto PowerShellTab](The-PowerShellTab-Object.md)
 Exemplos: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].

 [O objeto PowerShellTabCollection](The-PowerShellTabCollection-Object.md)
 Exemplo: $psISE.PowerShellTabs.

## Consulte Também
- [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  



<!--HONumber=Oct16_HO3-->


