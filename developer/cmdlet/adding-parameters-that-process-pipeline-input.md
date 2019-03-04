---
title: Adicionar parâmetros que processam a entrada do Pipeline | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: c790d20a792bcdb4a34485e53375560e129433a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854532"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="d99e5-102">Adicionar parâmetros que processam a entrada de pipeline</span><span class="sxs-lookup"><span data-stu-id="d99e5-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="d99e5-103">Uma fonte de entrada para um cmdlet é um objeto no pipeline do que se origina de um cmdlet de upstream.</span><span class="sxs-lookup"><span data-stu-id="d99e5-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="d99e5-104">Esta seção descreve como adicionar um parâmetro para o cmdlet Get-Proc (descrito na [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)) para que o cmdlet pode processar objetos do pipeline.</span><span class="sxs-lookup"><span data-stu-id="d99e5-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="d99e5-105">Esse cmdlet Get-Proc usa um `Name` parâmetro que aceita entrada de um objeto de pipeline, recupera informações de processo do computador local com base em nomes fornecidos e, em seguida, exibe informações sobre os processos na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d99e5-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

<span data-ttu-id="d99e5-106">Os tópicos nesta seção incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d99e5-106">Topics in this section include the following:</span></span>

- [<span data-ttu-id="d99e5-107">Definição da classe do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d99e5-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="d99e5-108">Definindo a entrada do Pipeline</span><span class="sxs-lookup"><span data-stu-id="d99e5-108">Defining Input from the Pipeline</span></span>](#Defining-Input-from-the-Pipeline)

- [<span data-ttu-id="d99e5-109">Substituindo uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="d99e5-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="d99e5-110">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="d99e5-110">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="d99e5-111">Definindo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="d99e5-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="d99e5-112">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d99e5-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="d99e5-113">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d99e5-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="d99e5-114">Definição da classe do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d99e5-114">Defining the Cmdlet Class</span></span>

<span data-ttu-id="d99e5-115">A primeira etapa na criação de cmdlet sempre é o cmdlet de nomenclatura e declarar a classe .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d99e5-115">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="d99e5-116">Este cmdlet recupera informações de processo, portanto, o nome do verbo escolhido aqui é "Get".</span><span class="sxs-lookup"><span data-stu-id="d99e5-116">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="d99e5-117">(Quase qualquer tipo de cmdlet que é capaz de recuperar informações pode processar a entrada de linha de comando.) Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="d99e5-117">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="d99e5-118">A seguir está a definição para esse cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="d99e5-118">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="d99e5-119">Detalhes desta definição são fornecidos nas [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="d99e5-119">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="d99e5-120">Definindo a entrada do Pipeline</span><span class="sxs-lookup"><span data-stu-id="d99e5-120">Defining Input from the Pipeline</span></span>

<span data-ttu-id="d99e5-121">Esta seção descreve como definir a entrada do pipeline para um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d99e5-121">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="d99e5-122">Esse cmdlet Get-Proc define uma propriedade que representa o `Name` parâmetro, conforme descrito em [adicionando parâmetros essa entrada de linha de comando de processo](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="d99e5-122">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="d99e5-123">(Consulte o tópico para obter informações gerais sobre como declarar parâmetros).</span><span class="sxs-lookup"><span data-stu-id="d99e5-123">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="d99e5-124">No entanto, quando um cmdlet precisa processar a entrada do pipeline, ele deve ter seus parâmetros associados a valores de entrada no tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d99e5-124">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="d99e5-125">Para fazer isso, você deve adicionar o `ValueFromPipeline` palavra-chave ou adicionar a `ValueFromPipelineByProperty` palavra-chave para o [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração do atributo.</span><span class="sxs-lookup"><span data-stu-id="d99e5-125">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="d99e5-126">Especifique o `ValueFromPipeline` palavra-chave se o cmdlet acessa o objeto de entrada completo.</span><span class="sxs-lookup"><span data-stu-id="d99e5-126">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="d99e5-127">Especifique o `ValueFromPipelineByProperty` se o cmdlet acessa apenas uma propriedade do objeto.</span><span class="sxs-lookup"><span data-stu-id="d99e5-127">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="d99e5-128">Aqui está a declaração de parâmetro para o `Name` parâmetro desse cmdlet Get-Proc que aceita entrada do pipeline.</span><span class="sxs-lookup"><span data-stu-id="d99e5-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="d99e5-129">Os conjuntos de declaração anterior a `ValueFromPipeline` palavra-chave para `true` para que o tempo de execução do Windows PowerShell irá associar o parâmetro para o objeto de entrada se o objeto é o mesmo tipo que o parâmetro ou se ele pode ser forçado para o mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="d99e5-129">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="d99e5-130">O `ValueFromPipelineByPropertyName` palavra-chave também é definido como `true` para que o tempo de execução do Windows PowerShell verificará o objeto de entrada para um `Name` propriedade.</span><span class="sxs-lookup"><span data-stu-id="d99e5-130">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="d99e5-131">Se o objeto de entrada tem essa propriedade, o tempo de execução será associado a `Name` parâmetro para o `Name` propriedade do objeto de entrada.</span><span class="sxs-lookup"><span data-stu-id="d99e5-131">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="d99e5-132">A configuração do `ValueFromPipeline` palavra-chave de atributo de um parâmetro tem precedência sobre a configuração para o `ValueFromPipelineByPropertyName` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="d99e5-132">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="d99e5-133">Substituindo uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="d99e5-133">Overriding an Input Processing Method</span></span>

<span data-ttu-id="d99e5-134">Se seu cmdlet é manipular a entrada do pipeline, ele precisa substituir os métodos de processamento de entrada apropriada.</span><span class="sxs-lookup"><span data-stu-id="d99e5-134">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="d99e5-135">Os métodos de processamento de entrada básico são introduzidos no [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="d99e5-135">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="d99e5-136">Esse cmdlet Get-Proc substitui o [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para manipular o `Name` entrada de parâmetro fornecida pelo usuário ou um script.</span><span class="sxs-lookup"><span data-stu-id="d99e5-136">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="d99e5-137">Esse método obtém os processos para cada nome de processo solicitado ou todos os processos se nenhum nome for fornecido.</span><span class="sxs-lookup"><span data-stu-id="d99e5-137">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="d99e5-138">Observe que dentro [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), a chamada para [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) é o mecanismo de saída para enviar objetos de saída para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="d99e5-138">Notice that within [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="d99e5-139">O segundo parâmetro dessa chamada `enumerateCollection`, é definido como `true` para informar o tempo de execução do Windows PowerShell enumere a matriz de objetos de processo e gravar um processo por vez à linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d99e5-139">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="d99e5-140">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="d99e5-140">Code Sample</span></span>

<span data-ttu-id="d99e5-141">Para o completo C# exemplos de código, consulte [GetProcessSample03 amostra](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d99e5-141">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="d99e5-142">Definindo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="d99e5-142">Defining Object Types and Formatting</span></span>

<span data-ttu-id="d99e5-143">Windows PowerShell passa informações entre cmdlets usando objetos .net.</span><span class="sxs-lookup"><span data-stu-id="d99e5-143">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="d99e5-144">Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d99e5-144">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="d99e5-145">Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="d99e5-145">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="d99e5-146">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d99e5-146">Building the Cmdlet</span></span>

<span data-ttu-id="d99e5-147">Depois de implementar um cmdlet ele deve ser registrado com o Windows PowerShell por meio de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d99e5-147">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="d99e5-148">Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="d99e5-148">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="d99e5-149">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d99e5-149">Testing the Cmdlet</span></span>

<span data-ttu-id="d99e5-150">Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você deve testá-lo executando-o na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d99e5-150">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="d99e5-151">Por exemplo, teste o código para o cmdlet de exemplo.</span><span class="sxs-lookup"><span data-stu-id="d99e5-151">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="d99e5-152">Para obter mais informações sobre como usar os cmdlets da linha de comando, consulte o [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d99e5-152">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="d99e5-153">No prompt do Windows PowerShell, digite os seguintes comandos para recuperar os nomes de processo por meio do pipeline.</span><span class="sxs-lookup"><span data-stu-id="d99e5-153">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="d99e5-154">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="d99e5-154">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="d99e5-155">Insira as seguintes linhas para obter os objetos de processo que têm um `Name` propriedade dos processos chamado "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="d99e5-155">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="d99e5-156">Este exemplo usa o `Get-Process` cmdlet (fornecido pelo Windows PowerShell) como um comando upstream para recuperar os processos "IEXPLORE".</span><span class="sxs-lookup"><span data-stu-id="d99e5-156">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="d99e5-157">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="d99e5-157">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="d99e5-158">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d99e5-158">See Also</span></span>

[<span data-ttu-id="d99e5-159">Adicionar parâmetros que processam a entrada de linha de comando</span><span class="sxs-lookup"><span data-stu-id="d99e5-159">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="d99e5-160">Criando seu primeiro Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d99e5-160">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="d99e5-161">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="d99e5-161">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="d99e5-162">Como registrar Cmdlets, provedores e aplicativos de Host</span><span class="sxs-lookup"><span data-stu-id="d99e5-162">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="d99e5-163">Referência do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d99e5-163">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="d99e5-164">Exemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="d99e5-164">Cmdlet Samples</span></span>](./cmdlet-samples.md)
