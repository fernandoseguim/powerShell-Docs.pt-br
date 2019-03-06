---
title: Exemplo de código RunSpace10 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 77c0675b45bf4ff6f8c6a85ff9a090c13c199c6d
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429577"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="f4a4c-102">Exemplo de código RunSpace10</span><span class="sxs-lookup"><span data-stu-id="f4a4c-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="f4a4c-103">Aqui está o código-fonte para o exemplo Runspace10.</span><span class="sxs-lookup"><span data-stu-id="f4a4c-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="f4a4c-104">Este aplicativo de exemplo adiciona um cmdlet para [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) e, em seguida, usa as informações de configuração modificado para criar o espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="f4a4c-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="f4a4c-105">Você pode baixar o C# arquivo de origem (runspace10.cs) usando o Windows Software Development Kit do Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="f4a4c-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f4a4c-106">Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="f4a4c-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f4a4c-107">Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="f4a4c-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f4a4c-108">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f4a4c-108">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="f4a4c-109">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f4a4c-109">See Also</span></span>

[<span data-ttu-id="f4a4c-110">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4a4c-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f4a4c-111">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4a4c-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)