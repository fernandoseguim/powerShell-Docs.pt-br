---
title: Criando um fluxo de trabalho com atividades do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853462"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="5d226-102">Criar um fluxo de trabalho com atividades do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d226-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="5d226-103">Você pode criar um fluxo de trabalho do Windows PowerShell selecionando as atividades de ferramentas do Visual Studio e arrastando-os para a janela do Designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5d226-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="5d226-104">Para obter informações sobre como adicionar atividades do Windows PowerShell para ferramentas do Visual Studio, consulte [adicionando atividades do Windows PowerShell para ferramentas do Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="5d226-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="5d226-105">Os procedimentos a seguir descrevem como criar um fluxo de trabalho que verifica o status de domínio de um grupo de computadores especificados pelo usuário, une-as em um domínio, se eles não estão associados e, em seguida, verifica o status novamente.</span><span class="sxs-lookup"><span data-stu-id="5d226-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="5d226-106">Configuração do projeto</span><span class="sxs-lookup"><span data-stu-id="5d226-106">Setting up the Project</span></span>

1. <span data-ttu-id="5d226-107">Siga o procedimento [adicionando atividades do Windows PowerShell para o Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) para criar um projeto de fluxo de trabalho e adicionar as atividades da [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) e [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies à caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="5d226-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="5d226-108">Adicione Automation, Microsoft.PowerShell.Activities, System. Management, Microsoft.PowerShell.Management.Activities e Microsoft.PowerShell.Commands.Management como para o projeto como assemblies de referência.</span><span class="sxs-lookup"><span data-stu-id="5d226-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="5d226-109">Adicionando atividades ao fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="5d226-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="5d226-110">Adicionar um **sequência** atividade ao fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5d226-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="5d226-111">Crie um argumento nomeado `ComputerName` com um tipo de argumento `String[]`.</span><span class="sxs-lookup"><span data-stu-id="5d226-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="5d226-112">Esse argumento representa os nomes dos computadores para verificar e Junte-se.</span><span class="sxs-lookup"><span data-stu-id="5d226-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="5d226-113">Crie um argumento nomeado `DomainCred` do tipo [pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="5d226-113">Create an argument named `DomainCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="5d226-114">Esse argumento representa as credenciais de domínio de uma conta de domínio que está autorizado para ingressar um computador ao domínio.</span><span class="sxs-lookup"><span data-stu-id="5d226-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="5d226-115">Crie um argumento nomeado `MachineCred` do tipo [pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="5d226-115">Create an argument named `MachineCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="5d226-116">Esse argumento representa as credenciais de administrador nos computadores para verificar e Junte-se.</span><span class="sxs-lookup"><span data-stu-id="5d226-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="5d226-117">Adicionar um **ParallelForEach** atividade dentro de **sequência** atividade.</span><span class="sxs-lookup"><span data-stu-id="5d226-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="5d226-118">Insira `comp` e `ComputerName` nas caixas de texto para que o loop itera através dos elementos da `ComputerName` matriz.</span><span class="sxs-lookup"><span data-stu-id="5d226-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="5d226-119">Adicionar um **sequência** atividade ao corpo do **ParallelForEach** atividade.</span><span class="sxs-lookup"><span data-stu-id="5d226-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="5d226-120">Defina as **DisplayName** propriedade da sequência a `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="5d226-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="5d226-121">Adicionar um **GetWmiObject** atividade para o **JoinDomain** sequência.</span><span class="sxs-lookup"><span data-stu-id="5d226-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="5d226-122">Editar as propriedades do **GetWmiObject** atividade da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="5d226-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="5d226-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5d226-123">Property</span></span>|<span data-ttu-id="5d226-124">Valor</span><span class="sxs-lookup"><span data-stu-id="5d226-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="5d226-125">**Classe**</span><span class="sxs-lookup"><span data-stu-id="5d226-125">**Class**</span></span>|<span data-ttu-id="5d226-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="5d226-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="5d226-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="5d226-127">**PSComputerName**</span></span>|<span data-ttu-id="5d226-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="5d226-128">{comp}</span></span>|
   |<span data-ttu-id="5d226-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="5d226-129">**PSCredential**</span></span>|<span data-ttu-id="5d226-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="5d226-130">MachineCred</span></span>|

9. <span data-ttu-id="5d226-131">Adicionar um **AddComputer** atividade para o **JoinDomain** sequência após a **GetWmiObject** atividade.</span><span class="sxs-lookup"><span data-stu-id="5d226-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="5d226-132">Editar as propriedades do **AddComputer** atividade da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="5d226-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="5d226-133">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5d226-133">Property</span></span>|<span data-ttu-id="5d226-134">Valor</span><span class="sxs-lookup"><span data-stu-id="5d226-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="5d226-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="5d226-135">**ComputerName**</span></span>|<span data-ttu-id="5d226-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="5d226-136">{comp}</span></span>|
    |<span data-ttu-id="5d226-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="5d226-137">**DomainCredential**</span></span>|<span data-ttu-id="5d226-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="5d226-138">DomainCred</span></span>|

11. <span data-ttu-id="5d226-139">Adicionar um **RestartComputer** atividade para o **JoinDomain** sequência após a **AddComputer** atividade.</span><span class="sxs-lookup"><span data-stu-id="5d226-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="5d226-140">Editar as propriedades do **RestartComputer** atividade da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="5d226-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="5d226-141">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5d226-141">Property</span></span>|<span data-ttu-id="5d226-142">Valor</span><span class="sxs-lookup"><span data-stu-id="5d226-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="5d226-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="5d226-143">**ComputerName**</span></span>|<span data-ttu-id="5d226-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="5d226-144">{comp}</span></span>|
    |<span data-ttu-id="5d226-145">**Credential**</span><span class="sxs-lookup"><span data-stu-id="5d226-145">**Credential**</span></span>|<span data-ttu-id="5d226-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="5d226-146">MachineCred</span></span>|
    |<span data-ttu-id="5d226-147">**para**</span><span class="sxs-lookup"><span data-stu-id="5d226-147">**For**</span></span>|<span data-ttu-id="5d226-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d226-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="5d226-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="5d226-149">**Force**</span></span>|<span data-ttu-id="5d226-150">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="5d226-150">True</span></span>|
    |<span data-ttu-id="5d226-151">Wait</span><span class="sxs-lookup"><span data-stu-id="5d226-151">Wait</span></span>|<span data-ttu-id="5d226-152">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="5d226-152">True</span></span>|
    |<span data-ttu-id="5d226-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="5d226-153">PSComputerName</span></span>|<span data-ttu-id="5d226-154">{""}</span><span class="sxs-lookup"><span data-stu-id="5d226-154">{""}</span></span>|

13. <span data-ttu-id="5d226-155">Adicionar um **GetWmiObject** atividade para o **JoinDomain** sequência após a **RestartComputer** atividade.</span><span class="sxs-lookup"><span data-stu-id="5d226-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="5d226-156">Editar suas propriedades para ser o mesmo que o anterior **GetWmiObject** atividade.</span><span class="sxs-lookup"><span data-stu-id="5d226-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="5d226-157">Quando você terminar de procedimentos, a janela de design de fluxo de trabalho deve ter esta aparência.</span><span class="sxs-lookup"><span data-stu-id="5d226-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="5d226-158">![XAML JoinDomain no designer de fluxo de trabalho](../media/joindomainworkflow.png)
    ![JoinDomain XAML no designer de fluxo de trabalho](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="5d226-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>