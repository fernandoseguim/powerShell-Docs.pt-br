---
title: GetProc01 código de exemplo (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 1f11c89f60aef44905cbce3fe669def26119d12e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856062"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="a0f47-102">Código de exemplo GetProc01 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="a0f47-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="a0f47-103">O código a seguir mostra a implementação do cmdlet de exemplo GetProc01.</span><span class="sxs-lookup"><span data-stu-id="a0f47-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="a0f47-104">Observe que o cmdlet é simplificado, deixando o trabalho real de recuperação do processo para o [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) método.</span><span class="sxs-lookup"><span data-stu-id="a0f47-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="a0f47-105">Você pode baixar o C# arquivo de origem (getproc01.cs) para esse cmdlet Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="a0f47-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="a0f47-106">Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="a0f47-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="a0f47-107">Você pode baixar o C# arquivo de origem (getproc01.cs) para esse cmdlet Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="a0f47-107">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="a0f47-108">Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="a0f47-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="a0f47-109">Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="a0f47-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a0f47-110">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="a0f47-110">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="a0f47-111">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a0f47-111">See Also</span></span>

[<span data-ttu-id="a0f47-112">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0f47-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="a0f47-113">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0f47-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)