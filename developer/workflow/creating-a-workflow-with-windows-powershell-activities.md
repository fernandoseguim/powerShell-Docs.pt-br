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
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055420"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="1ec46-102">Criar um fluxo de trabalho com atividades do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ec46-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="1ec46-103">Você pode criar um fluxo de trabalho do Windows PowerShell selecionando as atividades de ferramentas do Visual Studio e arrastando-os para a janela do Designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1ec46-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="1ec46-104">Para obter informações sobre como adicionar atividades do Windows PowerShell para ferramentas do Visual Studio, consulte [adicionando atividades do Windows PowerShell para ferramentas do Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="1ec46-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="1ec46-105">Os procedimentos a seguir descrevem como criar um fluxo de trabalho que verifica o status de domínio de um grupo de computadores especificados pelo usuário, une-as em um domínio, se eles não estão associados e, em seguida, verifica o status novamente.</span><span class="sxs-lookup"><span data-stu-id="1ec46-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="1ec46-106">Configuração do projeto</span><span class="sxs-lookup"><span data-stu-id="1ec46-106">Setting up the Project</span></span>

1. <span data-ttu-id="1ec46-107">Siga o procedimento [adicionando atividades do Windows PowerShell para o Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) para criar um projeto de fluxo de trabalho e adicionar as atividades da [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) e [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies à caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="1ec46-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="1ec46-108">Adicione Automation, Microsoft.PowerShell.Activities, System. Management, Microsoft.PowerShell.Management.Activities e Microsoft.PowerShell.Commands.Management como para o projeto como assemblies de referência.</span><span class="sxs-lookup"><span data-stu-id="1ec46-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="1ec46-109">Adicionando atividades ao fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="1ec46-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="1ec46-110">Adicionar um **sequência** atividade ao fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1ec46-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="1ec46-111">Crie um argumento nomeado `ComputerName` com um tipo de argumento `String[]`.</span><span class="sxs-lookup"><span data-stu-id="1ec46-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="1ec46-112">Esse argumento representa os nomes dos computadores para verificar e Junte-se.</span><span class="sxs-lookup"><span data-stu-id="1ec46-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="1ec46-113">Crie um argumento nomeado `DomainCred` do tipo [pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="1ec46-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="1ec46-114">Esse argumento representa as credenciais de domínio de uma conta de domínio que está autorizado para ingressar um computador ao domínio.</span><span class="sxs-lookup"><span data-stu-id="1ec46-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="1ec46-115">Crie um argumento nomeado `MachineCred` do tipo [pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="1ec46-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="1ec46-116">Esse argumento representa as credenciais de administrador nos computadores para verificar e Junte-se.</span><span class="sxs-lookup"><span data-stu-id="1ec46-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="1ec46-117">Adicionar um **ParallelForEach** atividade dentro de **sequência** atividade.</span><span class="sxs-lookup"><span data-stu-id="1ec46-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="1ec46-118">Insira `comp` e `ComputerName` nas caixas de texto para que o loop itera através dos elementos da `ComputerName` matriz.</span><span class="sxs-lookup"><span data-stu-id="1ec46-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="1ec46-119">Adicionar um **sequência** atividade ao corpo do **ParallelForEach** atividade.</span><span class="sxs-lookup"><span data-stu-id="1ec46-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="1ec46-120">Defina as **DisplayName** propriedade da sequência a `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="1ec46-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="1ec46-121">Adicionar um **GetWmiObject** atividade para o **JoinDomain** sequência.</span><span class="sxs-lookup"><span data-stu-id="1ec46-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="1ec46-122">Editar as propriedades do **GetWmiObject** atividade da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="1ec46-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="1ec46-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1ec46-123">Property</span></span>|<span data-ttu-id="1ec46-124">Valor</span><span class="sxs-lookup"><span data-stu-id="1ec46-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="1ec46-125">**Classe**</span><span class="sxs-lookup"><span data-stu-id="1ec46-125">**Class**</span></span>|<span data-ttu-id="1ec46-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="1ec46-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="1ec46-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="1ec46-127">**PSComputerName**</span></span>|<span data-ttu-id="1ec46-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="1ec46-128">{comp}</span></span>|
   |<span data-ttu-id="1ec46-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="1ec46-129">**PSCredential**</span></span>|<span data-ttu-id="1ec46-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="1ec46-130">MachineCred</span></span>|

9. <span data-ttu-id="1ec46-131">Adicionar um **AddComputer** atividade para o **JoinDomain** sequência após a **GetWmiObject** atividade.</span><span class="sxs-lookup"><span data-stu-id="1ec46-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="1ec46-132">Editar as propriedades do **AddComputer** atividade da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="1ec46-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="1ec46-133">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1ec46-133">Property</span></span>|<span data-ttu-id="1ec46-134">Valor</span><span class="sxs-lookup"><span data-stu-id="1ec46-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="1ec46-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="1ec46-135">**ComputerName**</span></span>|<span data-ttu-id="1ec46-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="1ec46-136">{comp}</span></span>|
    |<span data-ttu-id="1ec46-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="1ec46-137">**DomainCredential**</span></span>|<span data-ttu-id="1ec46-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="1ec46-138">DomainCred</span></span>|

11. <span data-ttu-id="1ec46-139">Adicionar um **RestartComputer** atividade para o **JoinDomain** sequência após a **AddComputer** atividade.</span><span class="sxs-lookup"><span data-stu-id="1ec46-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="1ec46-140">Editar as propriedades do **RestartComputer** atividade da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="1ec46-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="1ec46-141">Propriedade</span><span class="sxs-lookup"><span data-stu-id="1ec46-141">Property</span></span>|<span data-ttu-id="1ec46-142">Valor</span><span class="sxs-lookup"><span data-stu-id="1ec46-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="1ec46-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="1ec46-143">**ComputerName**</span></span>|<span data-ttu-id="1ec46-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="1ec46-144">{comp}</span></span>|
    |<span data-ttu-id="1ec46-145">**Credential**</span><span class="sxs-lookup"><span data-stu-id="1ec46-145">**Credential**</span></span>|<span data-ttu-id="1ec46-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="1ec46-146">MachineCred</span></span>|
    |<span data-ttu-id="1ec46-147">**para**</span><span class="sxs-lookup"><span data-stu-id="1ec46-147">**For**</span></span>|<span data-ttu-id="1ec46-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ec46-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="1ec46-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="1ec46-149">**Force**</span></span>|<span data-ttu-id="1ec46-150">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="1ec46-150">True</span></span>|
    |<span data-ttu-id="1ec46-151">Wait</span><span class="sxs-lookup"><span data-stu-id="1ec46-151">Wait</span></span>|<span data-ttu-id="1ec46-152">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="1ec46-152">True</span></span>|
    |<span data-ttu-id="1ec46-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="1ec46-153">PSComputerName</span></span>|<span data-ttu-id="1ec46-154">{""}</span><span class="sxs-lookup"><span data-stu-id="1ec46-154">{""}</span></span>|

13. <span data-ttu-id="1ec46-155">Adicionar um **GetWmiObject** atividade para o **JoinDomain** sequência após a **RestartComputer** atividade.</span><span class="sxs-lookup"><span data-stu-id="1ec46-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="1ec46-156">Editar suas propriedades para ser o mesmo que o anterior **GetWmiObject** atividade.</span><span class="sxs-lookup"><span data-stu-id="1ec46-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="1ec46-157">Quando você terminar de procedimentos, a janela de design de fluxo de trabalho deve ter esta aparência.</span><span class="sxs-lookup"><span data-stu-id="1ec46-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="1ec46-158">![XAML JoinDomain no designer de fluxo de trabalho](../media/joindomainworkflow.png)
    ![JoinDomain XAML no designer de fluxo de trabalho](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="1ec46-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>