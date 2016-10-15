---
title: O objeto ISEMenuItem
ms.date: 2016-05-11
keywords: PowerShell, cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
translationtype: Human Translation
ms.sourcegitcommit: fe3d7885b7c031a24a737f58523c8018cfc36146
ms.openlocfilehash: 43477d0742612f331f74833a1d70e69692b5b8e7

---

# O objeto ISEMenuItem
  Um objeto **ISEMenuItem** é uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItem. Todos os objetos de menu **Complementos** são instância da classe **Microsoft.PowerShell.Host.ISE.ISEMenuItem**.

## Propriedades

###  <a name="DisplayName"></a> DisplayName
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o nome de exibição do item de menu.

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

###  <a name="Action"></a> Ação
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o bloco de script. Quando você clicar no item de menu, ele chama a ação.

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

###  <a name="Shortcut"></a> Atalho
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém o atalho de teclado de entrada do Windows do item de menu.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

###  <a name="Submenus"></a> Submenus
  Suportado no Windows PowerShell ISE 2.0 e posteriores. 

 A propriedade somente leitura que obtém a [lista de submenus](The-ISEMenuItemCollection-Object.md) do item de menu.

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## Exemplo de script
 Para entender melhor o uso do menu Complementos e suas propriedades programáveis, leia o exemplo de script a seguir.

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## Consulte Também
 [O objeto ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) 
 [O modelo de objeto de script do ISE do Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Referência de modelo de objeto do ISE do Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [A hierarquia de modelo de objeto do ISE](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Oct16_HO2-->


