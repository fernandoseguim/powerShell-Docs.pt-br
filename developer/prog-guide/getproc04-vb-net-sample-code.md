---
title: GetProc04 código de exemplo (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 0d0d1a3f82bc2cee025139d69fee02eb601fa563
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055454"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="0e04f-102">Código de exemplo GetProc04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="0e04f-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="0e04f-103">O código a seguir mostra a implementação de um `Get-Process` cmdlet que relata os erros sem encerramento.</span><span class="sxs-lookup"><span data-stu-id="0e04f-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="0e04f-104">Essa implementação chama o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método para relatar erros sem encerramento.</span><span class="sxs-lookup"><span data-stu-id="0e04f-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="0e04f-105">Você pode baixar o C# arquivo de origem (getprov04.cs) para esse cmdlet Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="0e04f-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0e04f-106">Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0e04f-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0e04f-107">Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="0e04f-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0e04f-108">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="0e04f-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="0e04f-109">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0e04f-109">See Also</span></span>

[<span data-ttu-id="0e04f-110">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e04f-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0e04f-111">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e04f-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)