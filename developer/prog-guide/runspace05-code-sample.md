---
title: Exemplo de código RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 2b5ac097e8a52832b0f8cfb93b84eef56fc64858
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854592"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="9ac98-102">Exemplo de código RunSpace05</span><span class="sxs-lookup"><span data-stu-id="9ac98-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="9ac98-103">Aqui está o código-fonte para o exemplo Runspace05 descrito [Configurando um RunspaceConfiguration do Runspace usando](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="9ac98-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="9ac98-104">Este exemplo mostra como criar as informações de configuração do espaço de execução, criar um runspace, criar um pipeline com um único comando e, em seguida, executar o pipeline.</span><span class="sxs-lookup"><span data-stu-id="9ac98-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="9ac98-105">O comando é executado é o `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9ac98-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="9ac98-106">Você pode baixar o C# arquivo de origem (runspace05.cs) usando o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="9ac98-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9ac98-107">Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9ac98-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="9ac98-108">Você pode baixar o C# arquivo de origem (runspace05.cs) usando o Microsoft Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="9ac98-108">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9ac98-109">Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9ac98-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="9ac98-110">Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="9ac98-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9ac98-111">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="9ac98-111">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="9ac98-112">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="9ac98-112">See Also</span></span>

[<span data-ttu-id="9ac98-113">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ac98-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9ac98-114">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ac98-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)