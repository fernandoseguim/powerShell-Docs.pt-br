---
title: Adicionando atividades do Windows PowerShell para a caixa de ferramentas do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863562"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="ab2bc-102">Adicionar atividades do Windows PowerShell à caixa de ferramentas do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ab2bc-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="ab2bc-103">Antes de criar um fluxo de trabalho do PowerShell usando o Designer de fluxo de trabalho, você deve primeiro adicionar as atividades do PowerShell à caixa de ferramentas em um projeto de aplicativo de console do fluxo de trabalho do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="ab2bc-104">O procedimento a seguir mostra como adicionar as atividades do assembly Microsoft.PowerShell.Core.Activities a caixa de ferramentas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="ab2bc-105">Adicionando o Windows PowerShell atividades à caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="ab2bc-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="ab2bc-106">Crie um novo projeto de aplicativo de console do fluxo de trabalho no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="ab2bc-107">Sobre o **modo de exibição** menu, clique em **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="ab2bc-108">Adicionar uma nova guia na caixa de ferramentas, clicando duas vezes dentro da caixa de ferramentas e clicando em **Adicionar guia**e nomeie a nova guia, como "PowerShell atividades".</span><span class="sxs-lookup"><span data-stu-id="ab2bc-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="ab2bc-109">Adicionar uma guia permite que você agrupe as atividades de PowerShell separada de outras ferramentas na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="ab2bc-110">Na nova guia da caixa de ferramentas, clique em **escolher itens...** . O **Choose Toolbox Items** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="ab2bc-111">No **Choose Toolbox Items** caixa de diálogo, clique o **System. Activities** guia.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="ab2bc-112">Clique em **procurar**.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-112">Click **Browse**.</span></span>

7. <span data-ttu-id="ab2bc-113">Navegue até a pasta %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e e clique duas vezes em Microsoft.PowerShell.Core.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="ab2bc-114">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-114">Click **OK**.</span></span> <span data-ttu-id="ab2bc-115">As atividades definidas pelo assembly Microsoft.PowerShell.Core.Activities agora estão disponíveis na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab2bc-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ab2bc-116">See Also</span></span>

<span data-ttu-id="ab2bc-117">[Writing a Windows PowerShell Workflow](./writing-a-windows-powershell-workflow.md) (Escrevendo um Fluxo de Trabalho do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="ab2bc-117">[Writing a Windows PowerShell Workflow](./writing-a-windows-powershell-workflow.md)</span></span>

[<span data-ttu-id="ab2bc-118">Criando um fluxo de trabalho com atividades do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab2bc-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)