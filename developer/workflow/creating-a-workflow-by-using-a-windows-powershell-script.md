---
title: Criando um fluxo de trabalho usando um Script do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853042"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="30fce-102">Criar um fluxo de trabalho pelo uso de um script do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="30fce-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="30fce-103">Você pode criar um fluxo de trabalho, escrevendo um script do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30fce-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="30fce-104">Para criar um fluxo de trabalho, use a palavra-chave de fluxo de trabalho seguida por um nome para o fluxo de trabalho antes do corpo do script.</span><span class="sxs-lookup"><span data-stu-id="30fce-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="30fce-105">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="30fce-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="30fce-106">Você pode encontrar o fluxo de trabalho da mesma maneira que faria com qualquer outro comando do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30fce-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="30fce-107">Implementando Parallel e Sequence</span><span class="sxs-lookup"><span data-stu-id="30fce-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="30fce-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) dá suporte à execução de atividades em paralelo.</span><span class="sxs-lookup"><span data-stu-id="30fce-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="30fce-109">Para implementar essa funcionalidade em um script do Windows PowerShell, use o `parallel` palavra-chave na frente de um bloco de script.</span><span class="sxs-lookup"><span data-stu-id="30fce-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="30fce-110">Você também pode usar o `foreach -parallel` construção para iterar por meio de uma coleção de objetos em paralelo.</span><span class="sxs-lookup"><span data-stu-id="30fce-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="30fce-111">Para executar um grupo de atividades em ordem sequencial dentro de um bloco paralelo, coloque o grupo de atividades em um bloco de script e preceder o bloco com a palavra-chave de sequência.</span><span class="sxs-lookup"><span data-stu-id="30fce-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="30fce-112">Ingressando computadores em um domínio</span><span class="sxs-lookup"><span data-stu-id="30fce-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="30fce-113">O script a seguir cria um fluxo de trabalho que verifica o status de domínio de um grupo de computadores especificados pelo usuário, une-as em um domínio, se eles não estão associados e, em seguida, verifica o status novamente.</span><span class="sxs-lookup"><span data-stu-id="30fce-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="30fce-114">Esta é uma versão de script do fluxo de trabalho XAML explicado [criando um fluxo de trabalho com atividades do Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="30fce-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```