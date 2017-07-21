---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: O objeto ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="ff0df-103">O objeto ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="ff0df-103">The ISEMenuItemCollection Object</span></span>
  <span data-ttu-id="ff0df-104">Um objeto **ISEMenuItemCollection** é uma coleção de objetos **ISEMenuItem**.</span><span class="sxs-lookup"><span data-stu-id="ff0df-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="ff0df-105">É uma instância da classe Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="ff0df-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="ff0df-106">Um exemplo é o objeto **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** que é usado para personalizar o menu **Complemento** no ISE (Ambiente de Script Integrado) do Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="ff0df-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="ff0df-107">Método</span><span class="sxs-lookup"><span data-stu-id="ff0df-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="ff0df-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="ff0df-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>
  <span data-ttu-id="ff0df-109">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="ff0df-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff0df-110">Adiciona um item de menu à coleção.</span><span class="sxs-lookup"><span data-stu-id="ff0df-110">Adds a menu item to the collection.</span></span>

 <span data-ttu-id="ff0df-111">**DisplayName**
 O nome de exibição do menu a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="ff0df-111">**DisplayName**
 The display name of the menu to be added.</span></span>

 <span data-ttu-id="ff0df-112">**Action**
 O objeto **System.Management.Automation.ScriptBlock** que especifica a ação associada a este item de menu.</span><span class="sxs-lookup"><span data-stu-id="ff0df-112">**Action**
 The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

 <span data-ttu-id="ff0df-113">**Shortcut**
 O atalho de teclado desta ação.</span><span class="sxs-lookup"><span data-stu-id="ff0df-113">**Shortcut**
 The keyboard shortcut for the action.</span></span>

 <span data-ttu-id="ff0df-114">**Returns**
 O objeto ISEMenuItem que acabou de ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="ff0df-114">**Returns**
 The ISEMenuItem object that was just added.</span></span>

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a><span data-ttu-id="ff0df-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="ff0df-115">Clear\(\)</span></span>
  <span data-ttu-id="ff0df-116">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="ff0df-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff0df-117">Remove todos os submenus do item de menu.</span><span class="sxs-lookup"><span data-stu-id="ff0df-117">Removes all submenus from the menu item.</span></span>

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a><span data-ttu-id="ff0df-118">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ff0df-118">See Also</span></span>
- [<span data-ttu-id="ff0df-119">O objeto ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="ff0df-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md) 
- [<span data-ttu-id="ff0df-120">O modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff0df-120">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="ff0df-121">Referência de modelo de objeto do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff0df-121">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="ff0df-122">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="ff0df-122">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
