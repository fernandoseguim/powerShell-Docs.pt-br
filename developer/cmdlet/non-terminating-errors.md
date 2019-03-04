---
title: Erros não fatais | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 9d5c9b16fc5daf3d2f753eeeeedb0db925551a67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853772"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="7e910-102">Erros de não encerramento</span><span class="sxs-lookup"><span data-stu-id="7e910-102">Non-Terminating Errors</span></span>

<span data-ttu-id="7e910-103">Este tópico aborda o método usado para relatar erros de não finalização.</span><span class="sxs-lookup"><span data-stu-id="7e910-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="7e910-104">Ele também aborda como chamar o método a partir do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7e910-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="7e910-105">Quando ocorre um erro de finalização, o cmdlet deve relatar este erro chamando o [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método.</span><span class="sxs-lookup"><span data-stu-id="7e910-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="7e910-106">Quando o cmdlet relata um erro de finalização, o cmdlet pode continuar a operar nesse objeto de entrada e na entrada mais objetos do pipeline.</span><span class="sxs-lookup"><span data-stu-id="7e910-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="7e910-107">Se o cmdlet chama o [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método, o cmdlet pode gravar um registro de erro que descreve a condição que causou o erro não fatal.</span><span class="sxs-lookup"><span data-stu-id="7e910-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="7e910-108">Para obter mais informações sobre os registros de erro, consulte [registros de erros do Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="7e910-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="7e910-109">Cmdlets pode chamar [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) conforme necessário de dentro de seu métodos de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="7e910-109">Cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="7e910-110">No entanto, os cmdlets pode chamar [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) somente do thread que chamou o [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), ou [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) o método de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="7e910-110">However, cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="7e910-111">Não chame [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) de outro thread.</span><span class="sxs-lookup"><span data-stu-id="7e910-111">Do not call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="7e910-112">Em vez disso, se comunicar erros de volta para o thread principal.</span><span class="sxs-lookup"><span data-stu-id="7e910-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e910-113">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="7e910-113">See Also</span></span>

[<span data-ttu-id="7e910-114">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="7e910-114">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="7e910-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="7e910-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="7e910-116">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="7e910-116">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="7e910-117">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="7e910-117">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="7e910-118">Registros de erro do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="7e910-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

<span data-ttu-id="7e910-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="7e910-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
