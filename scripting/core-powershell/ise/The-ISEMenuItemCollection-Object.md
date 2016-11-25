---
title: O objeto ISEMenuItemCollection
ms.date: 2016-05-11
keywords: PowerShell, cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
translationtype: Human Translation
ms.sourcegitcommit: 6c666e2e23cb74818e37293410dafc9033057733
ms.openlocfilehash: 489c9492e8de213145b71a7963e180fe1a4ad5b6

---

# O objeto ISEMenuItemCollection
  Um objeto **ISEMenuItemCollection** é uma coleção de objetos **ISEMenuItem**. É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Um exemplo é o objeto **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** que é usado para personalizar o menu **Complemento** no ISE (Ambiente de Script Integrado) do Windows PowerShell®.

## Método

### Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Adiciona um item de menu à coleção.

 **DisplayName**
 O nome de exibição do menu a ser adicionado.

 **Action**
 O objeto **System.Management.Automation.ScriptBlock** que especifica a ação associada a este item de menu.

 **Shortcut**
 O atalho de teclado desta ação.

 **Returns**
 O objeto ISEMenuItem que acabou de ser adicionado.

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### Limpar\(\)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Remove todos os submenus do item de menu.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## Consulte Também
- [O objeto ISEMenuItem](The-ISEMenuItem-Object.md) 
- [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo do objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Nov16_HO4-->


