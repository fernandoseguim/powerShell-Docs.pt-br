---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: O objeto PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="dca4f-103">O objeto PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="dca4f-103">The PowerShellTabCollection Object</span></span>
  <span data-ttu-id="dca4f-104">O objeto da coleção **PowerShellTab** é uma coleção de objetos **PowerShellTab**.</span><span class="sxs-lookup"><span data-stu-id="dca4f-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="dca4f-105">Cada objeto **PowerShellTab** funciona como um ambiente de tempo de execução separado.</span><span class="sxs-lookup"><span data-stu-id="dca4f-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="dca4f-106">Ele é uma instância da classe Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="dca4f-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="dca4f-107">Um exemplo é o objeto **$psISE.PowerShellTabs**.</span><span class="sxs-lookup"><span data-stu-id="dca4f-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="dca4f-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="dca4f-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="dca4f-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="dca4f-109">Add\(\)</span></span>
  <span data-ttu-id="dca4f-110">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="dca4f-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="dca4f-111">Adiciona uma nova guia do PowerShell à coleção.</span><span class="sxs-lookup"><span data-stu-id="dca4f-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="dca4f-112">Retorna a guia recém-adicionada.</span><span class="sxs-lookup"><span data-stu-id="dca4f-112">It returns the newly added tab.</span></span>

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="dca4f-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="dca4f-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="dca4f-114">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="dca4f-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="dca4f-115">Remove a guia especificada pelo parâmetro **psTab**.</span><span class="sxs-lookup"><span data-stu-id="dca4f-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

 <span data-ttu-id="dca4f-116">**psTab**
 A guia do PowerShell a ser removida.</span><span class="sxs-lookup"><span data-stu-id="dca4f-116">**psTab**
 The PowerShell tab to remove.</span></span>

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="dca4f-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="dca4f-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="dca4f-118">Suportado no Windows PowerShell ISE 2.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="dca4f-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="dca4f-119">Seleciona a guia do PowerShell que é especificada pelo parâmetro **psTab** para torná-la a guia ativa do PowerShell no momento.</span><span class="sxs-lookup"><span data-stu-id="dca4f-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

 <span data-ttu-id="dca4f-120">**psTab**
 A guia do PowerShell a ser selecionada.</span><span class="sxs-lookup"><span data-stu-id="dca4f-120">**psTab**
 The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dca4f-121">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="dca4f-121">See Also</span></span>
- [<span data-ttu-id="dca4f-122">O objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="dca4f-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="dca4f-123">O modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dca4f-123">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="dca4f-124">Referência de modelo de objeto do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dca4f-124">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="dca4f-125">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="dca4f-125">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
