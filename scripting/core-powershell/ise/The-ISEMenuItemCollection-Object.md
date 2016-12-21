---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet
ms.date: 2016-12-12
title: O objeto ISEMenuItemCollection
ms.technology: powershell
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 45e9123df5f22f37d2a76e49db6df5aa98824e1c
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-isemenuitemcollection-object"></a>O objeto ISEMenuItemCollection
  Um objeto **ISEMenuItemCollection** é uma coleção de objetos **ISEMenuItem**. É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Um exemplo é o objeto **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** que é usado para personalizar o menu **Complemento** no ISE (Ambiente de Script Integrado) do Windows PowerShell®.

## <a name="method"></a>Método

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)
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

### <a name="clear"></a>Clear\(\)
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 Remove todos os submenus do item de menu.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>Consulte Também
- [O objeto ISEMenuItem](The-ISEMenuItem-Object.md) 
- [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [A hierarquia de modelo de objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  
