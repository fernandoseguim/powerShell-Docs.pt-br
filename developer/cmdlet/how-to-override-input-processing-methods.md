---
title: Como substituir os métodos de processamento de entrada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056389"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="ff82a-102">Como substituir os métodos de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="ff82a-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="ff82a-103">Estes exemplos mostram como substituir os métodos dentro de um cmdlet de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="ff82a-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="ff82a-104">Esses métodos são usados para executar as seguintes operações:</span><span class="sxs-lookup"><span data-stu-id="ff82a-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="ff82a-105">O [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método é usado para executar operações de inicialização única que são válidas para todos os objetos processados pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ff82a-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="ff82a-106">O tempo de execução do Windows PowerShell chama esse método apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="ff82a-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="ff82a-107">O [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método é usado para processar os objetos passados para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ff82a-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="ff82a-108">O tempo de execução do Windows PowerShell chama esse método para cada objeto passado para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ff82a-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="ff82a-109">O [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método é usado para executar operações de processamento de postagem única.</span><span class="sxs-lookup"><span data-stu-id="ff82a-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="ff82a-110">O tempo de execução do Windows PowerShell chama esse método apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="ff82a-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="ff82a-111">Para substituir o método BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="ff82a-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="ff82a-112">Declarar uma substituição protegida do [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="ff82a-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="ff82a-113">A classe a seguir imprime uma mensagem de exemplo.</span><span class="sxs-lookup"><span data-stu-id="ff82a-113">The following class prints a sample message.</span></span> <span data-ttu-id="ff82a-114">Para usar essa classe, altere o verbo e substantivo no atributo de Cmdlet, altere o nome da classe para refletir o novo verbo e substantivo e, em seguida, adicionar a funcionalidade necessária para a substituição do [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="ff82a-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="ff82a-115">Substituir o método ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="ff82a-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="ff82a-116">Declarar uma substituição protegida do [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="ff82a-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="ff82a-117">A classe a seguir imprime uma mensagem de exemplo.</span><span class="sxs-lookup"><span data-stu-id="ff82a-117">The following class prints a sample message.</span></span> <span data-ttu-id="ff82a-118">Para usar essa classe, altere o verbo e substantivo no atributo de Cmdlet, altere o nome da classe para refletir o novo verbo e substantivo e, em seguida, adicionar a funcionalidade necessária para a substituição do [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="ff82a-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="ff82a-119">Para substituir o método EndProcessing</span><span class="sxs-lookup"><span data-stu-id="ff82a-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="ff82a-120">Declarar uma substituição protegida do [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="ff82a-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="ff82a-121">A classe a seguir imprime uma amostra.</span><span class="sxs-lookup"><span data-stu-id="ff82a-121">The following class prints a sample.</span></span> <span data-ttu-id="ff82a-122">Para usar essa classe, altere o verbo e substantivo no atributo de Cmdlet, altere o nome da classe para refletir o novo verbo e substantivo e, em seguida, adicionar a funcionalidade necessária para a substituição do [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="ff82a-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a><span data-ttu-id="ff82a-123">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ff82a-123">See Also</span></span>

[<span data-ttu-id="ff82a-124">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="ff82a-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="ff82a-125">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="ff82a-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="ff82a-126">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="ff82a-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

<span data-ttu-id="ff82a-127">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="ff82a-127">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
