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
ms.locfileid: "30953048"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="5b0b6-103">O objeto ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="5b0b6-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="5b0b6-104">O objeto **ISEAddOnToolCollection** é uma coleção de objetos **ISEAddOnTool**.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="5b0b6-105">Um exemplo é o objeto **$psISE.CurrentPowerShellTab.VerticalAddOnTools**.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="5b0b6-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="5b0b6-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="5b0b6-107">Add\( Name, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="5b0b6-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="5b0b6-108">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="5b0b6-109">Adiciona uma nova ferramenta complementar à coleção.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="5b0b6-110">Retorna a ferramenta complementar recém-adicionada.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="5b0b6-111">Antes de executar esse comando, você deve instalar a ferramenta complementar no computador local e carregar o assembly.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="5b0b6-112">**Name** – cadeia de caracteres, especifica o nome de exibição da ferramenta complementar que é adicionada ao ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="5b0b6-113">**ControlType** – Tipo, especifica o controle que é adicionado.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="5b0b6-114">**\[IsVisible\]** – Booliano opcional, se for definido como **$true**, a ferramenta complementar ficará imediatamente visível no painel de ferramentas associado.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="5b0b6-115">Remove\( Item \)</span><span class="sxs-lookup"><span data-stu-id="5b0b6-115">Remove\( Item \)</span></span>

<span data-ttu-id="5b0b6-116">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="5b0b6-117">Remove a ferramenta complementar especificada da coleção.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="5b0b6-118">**Item** – Microsoft.PowerShell.Host.ISE.ISEAddOnTool, especifica o objeto a ser removido do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="5b0b6-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="5b0b6-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="5b0b6-120">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="5b0b6-121">Seleciona a guia do PowerShell que o parâmetro **psTab** especifica.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="5b0b6-122">**psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab, a guia PowerShell a ser selecionada.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="5b0b6-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="5b0b6-123">Remove\( psTab \)</span></span>

<span data-ttu-id="5b0b6-124">Com suporte no Windows PowerShell ISE 3.0 e posterior, não está presente em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="5b0b6-125">Remove a guia do PowerShell que o parâmetro **psTab** especifica.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="5b0b6-126">**psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab, a guia PowerShell a ser removida.</span><span class="sxs-lookup"><span data-stu-id="5b0b6-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="5b0b6-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5b0b6-127">See Also</span></span>

- [<span data-ttu-id="5b0b6-128">O objeto PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="5b0b6-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="5b0b6-129">Objetivo do modelo de objeto de script do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b0b6-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="5b0b6-130">A hierarquia de modelo de objeto do ISE</span><span class="sxs-lookup"><span data-stu-id="5b0b6-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)