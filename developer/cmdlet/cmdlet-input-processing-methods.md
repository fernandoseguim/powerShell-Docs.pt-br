---
title: Métodos de processamento de entrada do cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: 065214647dfa6d376b727930fe75140911095faf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059364"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="f9580-102">Métodos de processamento de entrada de cmdlet</span><span class="sxs-lookup"><span data-stu-id="f9580-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="f9580-103">Cmdlets deve substituir um ou mais dos métodos descritos neste tópico para realizar seu trabalho de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="f9580-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="f9580-104">Esses métodos permitem que o cmdlet executar pré-processando operações de entrada operações de processamento e pós-processamento de operações.</span><span class="sxs-lookup"><span data-stu-id="f9580-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="f9580-105">Esses métodos também permitem que você parar o processamento de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9580-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="f9580-106">Tarefas de pré-processamento</span><span class="sxs-lookup"><span data-stu-id="f9580-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="f9580-107">Cmdlets deve substituir o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método para adicionar quaisquer operações de pré-processamento são válidas para todos os registros que serão processados posteriormente pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9580-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="f9580-108">Quando o Windows PowerShell processa um pipeline de comando, o Windows PowerShell chama esse método uma vez para cada instância do cmdlet no pipeline.</span><span class="sxs-lookup"><span data-stu-id="f9580-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="f9580-109">Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento do Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="f9580-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="f9580-110">O código a seguir mostra uma implementação do [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="f9580-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

<span data-ttu-id="f9580-111">Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f9580-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="f9580-112">Neste tutorial, o **Str Select** cmdlet usa o [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método para gerar a expressão regular que é usada para pesquisar os registros de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="f9580-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="f9580-113">Tarefas de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="f9580-113">Input Processing Tasks</span></span>

<span data-ttu-id="f9580-114">Cmdlets pode substituir o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método para processar a entrada que é enviada para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9580-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="f9580-115">Quando o Windows PowerShell processa um pipeline de comando, o Windows PowerShell chama esse método para cada registro de entrada é processado pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9580-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="f9580-116">Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento do Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="f9580-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="f9580-117">O código a seguir mostra uma implementação do [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="f9580-117">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

<span data-ttu-id="f9580-118">Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f9580-118">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="f9580-119">Tarefas de pós-processamento</span><span class="sxs-lookup"><span data-stu-id="f9580-119">Post-Processing Tasks</span></span>

<span data-ttu-id="f9580-120">Cmdlets deve substituir o [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método para adicionar qualquer pós-processamento operações que são válidas para todos os registros que foram processados pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9580-120">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="f9580-121">Por exemplo, o cmdlet pode ter que limpar as variáveis de objeto depois que ele é concluído de processamento.</span><span class="sxs-lookup"><span data-stu-id="f9580-121">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="f9580-122">Quando o Windows PowerShell processa um pipeline de comando, o Windows PowerShell chama esse método uma vez para cada instância do cmdlet no pipeline.</span><span class="sxs-lookup"><span data-stu-id="f9580-122">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="f9580-123">No entanto, é importante lembrar-se de que o tempo de execução do Windows PowerShell não chamará o [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método se o cmdlet foi cancelado no Centro por meio de seu processamento de entrada ou se um encerramento ocorrerá erro em qualquer parte do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9580-123">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="f9580-124">Por esse motivo, um cmdlet que requer a limpeza do objeto deve implementar completo [System. IDisposable](/dotnet/api/System.IDisposable) padrão, incluindo um finalizador, para que o tempo de execução possa chamar ambos o [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) e [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) métodos no final do processamento.</span><span class="sxs-lookup"><span data-stu-id="f9580-124">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="f9580-125">Para obter mais informações sobre como o Windows PowerShell invoca o pipeline de comando, consulte [ciclo de vida de processamento do Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="f9580-125">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="f9580-126">O código a seguir mostra uma implementação do [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="f9580-126">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

<span data-ttu-id="f9580-127">Para obter um exemplo mais detalhado de como usar o [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f9580-127">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9580-128">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f9580-128">See Also</span></span>

[<span data-ttu-id="f9580-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="f9580-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="f9580-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="f9580-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="f9580-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="f9580-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="f9580-132">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="f9580-132">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="f9580-133">Shell do Windows PowerShell do SDK</span><span class="sxs-lookup"><span data-stu-id="f9580-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
