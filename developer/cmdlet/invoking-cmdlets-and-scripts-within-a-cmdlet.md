---
title: Invocar Cmdlets e Scripts dentro de um Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855182"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="aeccf-102">Invocar cmdlets e scripts dentro de um cmdlet</span><span class="sxs-lookup"><span data-stu-id="aeccf-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="aeccf-103">Um cmdlet pode invocar outros cmdlets e scripts de dentro da método do cmdlet de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="aeccf-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="aeccf-104">Isso permite que você adicionar a funcionalidade de scripts e cmdlets existentes para o cmdlet sem reescrever o código.</span><span class="sxs-lookup"><span data-stu-id="aeccf-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="aeccf-105">A invocação de método</span><span class="sxs-lookup"><span data-stu-id="aeccf-105">The Invoke Method</span></span>

<span data-ttu-id="aeccf-106">Todos os cmdlets podem invocar um cmdlet existente chamando o [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método de dentro de uma entrada de processamento, como o método, [ System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), que é substituído pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aeccf-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="aeccf-107">No entanto, você pode chamar apenas esses cmdlets que derivam diretamente de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="aeccf-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="aeccf-108">Você não pode chamar um cmdlet que deriva de [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="aeccf-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="aeccf-109">O [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método tem as seguintes variantes.</span><span class="sxs-lookup"><span data-stu-id="aeccf-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="aeccf-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) essa variante invoca o objeto de cmdlet e retorna uma coleção de objetos do tipo "T".</span><span class="sxs-lookup"><span data-stu-id="aeccf-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="aeccf-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) essa variante invoca o objeto de cmdlet e retorna um emumerator com rigidez de tipos.</span><span class="sxs-lookup"><span data-stu-id="aeccf-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="aeccf-112">Essa variante permite ao usuário usar os objetos na coleção para executar operações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="aeccf-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="aeccf-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="aeccf-113">Examples</span></span>

|<span data-ttu-id="aeccf-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aeccf-114">Example</span></span>|<span data-ttu-id="aeccf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="aeccf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aeccf-116">Invocar Cmdlets dentro de um Cmdlet</span><span class="sxs-lookup"><span data-stu-id="aeccf-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="aeccf-117">Este exemplo mostra como chamar um cmdlet de dentro de outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aeccf-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="aeccf-118">Invocando Scripts dentro de um Cmdlet</span><span class="sxs-lookup"><span data-stu-id="aeccf-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="aeccf-119">Este exemplo mostra como chamar um script que é fornecido para o cmdlet de dentro de outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aeccf-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="aeccf-120">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="aeccf-120">See Also</span></span>

<span data-ttu-id="aeccf-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="aeccf-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
