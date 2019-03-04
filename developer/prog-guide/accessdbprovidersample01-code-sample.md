---
title: Exemplo de código AccessDbProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859662"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="61bfb-102">Exemplo de código AccessDbProviderSample01</span><span class="sxs-lookup"><span data-stu-id="61bfb-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="61bfb-103">O código a seguir mostra a implementação do provedor do Windows PowerShell descrito em [criando um provedor básico do Windows PowerShell](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="61bfb-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="61bfb-104">Essa implementação oferece métodos para iniciar e interromper o provedor e, embora ele não fornece um meio para acessar um armazenamento de dados ou para obter ou definir os dados no armazenamento de dados, ele fornece a funcionalidade básica necessária por todos os provedores.</span><span class="sxs-lookup"><span data-stu-id="61bfb-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="61bfb-105">Você pode baixar o C# arquivo de origem (AccessDBSampleProvider01.cs) para este provedor usando o Windows Software Development Kit do Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="61bfb-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="61bfb-106">Para obter instruções de download, consulte [como instalar o Windows PowerShell e o Download do SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="61bfb-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="61bfb-107">Os arquivos de origem baixado estão disponíveis na  **\<amostras do PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="61bfb-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="61bfb-108">Para obter mais informações sobre outras implementações do provedor do Windows PowerShell, consulte [projetando seu provedor do Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="61bfb-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="61bfb-109">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="61bfb-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="61bfb-110">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="61bfb-110">See Also</span></span>

[<span data-ttu-id="61bfb-111">Guia do programador do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="61bfb-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="61bfb-112">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="61bfb-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)