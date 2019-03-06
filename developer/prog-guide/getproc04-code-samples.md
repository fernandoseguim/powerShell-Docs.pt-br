---
title: Exemplos de código GetProc04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: b9b42c818981090496f7b14a1cb8bdec14a5d5bb
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429713"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="4b48a-102">Exemplos de código GetProc04</span><span class="sxs-lookup"><span data-stu-id="4b48a-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="4b48a-103">Aqui estão exemplos de código para o cmdlet de exemplo GetProc04.</span><span class="sxs-lookup"><span data-stu-id="4b48a-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="4b48a-104">Esse é o `Get-Process` cmdlet de exemplo descrito em [adicionando sem encerramento relatório de erros para o Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="4b48a-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="4b48a-105">Isso `Get-Process` cmdlet chamadas a [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método sempre que uma exceção de operação inválida é lançada durante a recuperação de informações do processo.</span><span class="sxs-lookup"><span data-stu-id="4b48a-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="4b48a-106">Você pode baixar o C# arquivo de origem (getprov04.cs) para esse cmdlet Get-Proc usando o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="4b48a-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4b48a-107">Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="4b48a-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="4b48a-108">Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="4b48a-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="4b48a-109">Para o código de exemplo completo, consulte os tópicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="4b48a-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="4b48a-110">Language</span><span class="sxs-lookup"><span data-stu-id="4b48a-110">Language</span></span>|<span data-ttu-id="4b48a-111">Tópico</span><span class="sxs-lookup"><span data-stu-id="4b48a-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="4b48a-112">C#</span><span class="sxs-lookup"><span data-stu-id="4b48a-112">C#</span></span>|[<span data-ttu-id="4b48a-113">GetProc04 (C#) código de exemplo</span><span class="sxs-lookup"><span data-stu-id="4b48a-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="4b48a-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="4b48a-114">VB.NET</span></span>|[<span data-ttu-id="4b48a-115">GetProc04 código de exemplo (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="4b48a-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="4b48a-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="4b48a-116">See Also</span></span>

[<span data-ttu-id="4b48a-117">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b48a-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4b48a-118">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b48a-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)