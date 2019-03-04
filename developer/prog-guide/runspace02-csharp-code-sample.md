---
title: Runspace02 (C#) exemplo de código | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: 0a8fc05db74529e2bfb88820b9cfd988245e0aeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854612"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="c39bb-102">Exemplo de código Runspace02 (C#)</span><span class="sxs-lookup"><span data-stu-id="c39bb-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="c39bb-103">Aqui está o C# código-fonte do exemplo Runspace02.</span><span class="sxs-lookup"><span data-stu-id="c39bb-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="c39bb-104">Este exemplo usa o [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe para executar o `Get-Process` cmdlet sincronicamente.</span><span class="sxs-lookup"><span data-stu-id="c39bb-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="c39bb-105">Windows Forms e vinculação de dados, em seguida, são usados para exibir os resultados em um controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="c39bb-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="c39bb-106">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="c39bb-106">Code Sample</span></span>

[!code-csharp[Runspace02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a><span data-ttu-id="c39bb-107">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c39bb-107">See Also</span></span>

[<span data-ttu-id="c39bb-108">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c39bb-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)