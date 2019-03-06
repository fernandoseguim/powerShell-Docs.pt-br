---
title: GetProc04 (C#) exemplos de código | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 1fc1ab58ae651239937e36c8bb08fda3d3272b2a
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429679"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="8750c-102">Código de exemplo GetProc04 (C#)</span><span class="sxs-lookup"><span data-stu-id="8750c-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="8750c-103">O código a seguir mostra a implementação de um `Get-Process` cmdlet que relata os erros sem encerramento.</span><span class="sxs-lookup"><span data-stu-id="8750c-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="8750c-104">Essa implementação chama o [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método para relatar erros sem encerramento.</span><span class="sxs-lookup"><span data-stu-id="8750c-104">This implementation calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="8750c-105">Você pode baixar o C# arquivo de origem (getprov04.cs) para esse cmdlet Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="8750c-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="8750c-106">Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="8750c-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="8750c-107">Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="8750c-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8750c-108">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="8750c-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="8750c-109">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8750c-109">See Also</span></span>

[<span data-ttu-id="8750c-110">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8750c-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8750c-111">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8750c-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)