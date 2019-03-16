---
title: Adicionando relatórios de erros ao seu Cmdlet não fatal | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: e0550dacc33f45f45ba105ca5cb4d2e5b5d675fb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056049"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="df985-102">Adicionar relatórios de erros de não encerramento ao seu cmdlet</span><span class="sxs-lookup"><span data-stu-id="df985-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="df985-103">Cmdlets podem relatar erros sem encerramento chamando o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método e ainda continuar a operar no objeto de entrada atual ou em entrada mais objetos do pipeline.</span><span class="sxs-lookup"><span data-stu-id="df985-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span> <span data-ttu-id="df985-104">Esta seção explica como criar um cmdlet que relata erros sem encerramento de seus métodos de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="df985-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="df985-105">Para erros de não encerramento (bem como erros de encerramento), o cmdlet deve passar uma [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto identifica o erro.</span><span class="sxs-lookup"><span data-stu-id="df985-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object identifying the error.</span></span> <span data-ttu-id="df985-106">Cada registro de erro é identificado por uma cadeia de caracteres exclusiva, chamada "identificador de erro".</span><span class="sxs-lookup"><span data-stu-id="df985-106">Each error record is identified by a unique string called the "error identifier."</span></span> <span data-ttu-id="df985-107">Além do identificador, a categoria de cada erro é especificada pelo constantes definidas por um [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeração.</span><span class="sxs-lookup"><span data-stu-id="df985-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="df985-108">O usuário pode exibir os erros com base em sua categoria, definindo o `$ErrorView` variável para "CategoryView".</span><span class="sxs-lookup"><span data-stu-id="df985-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="df985-109">Para obter mais informações sobre os registros de erro, consulte [registros de erros do Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="df985-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="df985-110">Os tópicos nesta seção incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="df985-110">Topics in this section include the following:</span></span>

- [<span data-ttu-id="df985-111">Definindo o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df985-111">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="df985-112">Definindo parâmetros</span><span class="sxs-lookup"><span data-stu-id="df985-112">Defining Parameters</span></span>](#Defining-Parameters)

- [<span data-ttu-id="df985-113">Substituindo métodos de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="df985-113">Overriding Input Processing Methods</span></span>](#Overriding-Input-Processing-Methods)

- [<span data-ttu-id="df985-114">Relatando erros sem encerramento</span><span class="sxs-lookup"><span data-stu-id="df985-114">Reporting Nonterminating Errors</span></span>](#Reporting-Nonterminating-Errors)

- [<span data-ttu-id="df985-115">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="df985-115">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="df985-116">Definindo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="df985-116">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="df985-117">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df985-117">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="df985-118">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df985-118">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="df985-119">Definindo o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df985-119">Defining the Cmdlet</span></span>

<span data-ttu-id="df985-120">A primeira etapa na criação de cmdlet sempre é o cmdlet de nomenclatura e declarar a classe .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df985-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="df985-121">Este cmdlet recupera informações de processo, portanto, o nome do verbo escolhido aqui é "Get".</span><span class="sxs-lookup"><span data-stu-id="df985-121">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="df985-122">(Quase qualquer tipo de cmdlet que é capaz de recuperar informações pode processar a entrada de linha de comando.) Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="df985-122">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="df985-123">A seguir está a definição para esse cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="df985-123">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="df985-124">Detalhes desta definição são fornecidos nas [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="df985-124">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="df985-125">Definindo parâmetros</span><span class="sxs-lookup"><span data-stu-id="df985-125">Defining Parameters</span></span>

<span data-ttu-id="df985-126">Se necessário, o cmdlet deve definir parâmetros para o processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="df985-126">If necessary, your cmdlet must define parameters for processing input.</span></span> <span data-ttu-id="df985-127">Esse cmdlet Get-Proc define uma `Name` parâmetro, conforme descrito em [adicionando parâmetros essa entrada de linha de comando de processo](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="df985-127">This Get-Proc cmdlet defines a `Name` parameter as described in [Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="df985-128">Aqui está a declaração de parâmetro para o `Name` parâmetro desse cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="df985-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="df985-129">Substituindo métodos de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="df985-129">Overriding Input Processing Methods</span></span>

<span data-ttu-id="df985-130">Todos os cmdlets devem substituir pelo menos uma entrada de processamento métodos fornecidos pelo [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="df985-130">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="df985-131">Esses métodos são discutidos [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="df985-131">These methods are discussed in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="df985-132">O cmdlet deve tratar cada registro independentemente do quanto possível.</span><span class="sxs-lookup"><span data-stu-id="df985-132">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="df985-133">Esse cmdlet Get-Proc substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para lidar com o `Name` parâmetro de entrada fornecida pelo usuário ou um script.</span><span class="sxs-lookup"><span data-stu-id="df985-133">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter for input provided by the user or a script.</span></span> <span data-ttu-id="df985-134">Esse método obtém os processos para cada nome de processo solicitado ou todos os processos se nenhum nome for fornecido.</span><span class="sxs-lookup"><span data-stu-id="df985-134">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="df985-135">Detalhes dessa substituição são fornecidos nas [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="df985-135">Details of this override are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

#### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="df985-136">Itens a lembrar ao relatar erros</span><span class="sxs-lookup"><span data-stu-id="df985-136">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="df985-137">O [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) do objeto que o cmdlet transmite ao escrever um erro requer uma exceção em seu núcleo.</span><span class="sxs-lookup"><span data-stu-id="df985-137">The [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object that the cmdlet passes when writing an error requires an exception at its core.</span></span> <span data-ttu-id="df985-138">Siga as diretrizes do .NET ao determinar a exceção a usar.</span><span class="sxs-lookup"><span data-stu-id="df985-138">Follow the .NET guidelines when determining the exception to use.</span></span> <span data-ttu-id="df985-139">Basicamente, se o erro semanticamente é o mesmo que uma exceção existente, o cmdlet deve usar ou derivar dessa exceção.</span><span class="sxs-lookup"><span data-stu-id="df985-139">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span> <span data-ttu-id="df985-140">Caso contrário, ele deve derivar uma nova exceção ou hierarquia de exceções diretamente a partir de [System. Exception](/dotnet/api/System.Exception) classe.</span><span class="sxs-lookup"><span data-stu-id="df985-140">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception](/dotnet/api/System.Exception) class.</span></span>

<span data-ttu-id="df985-141">Durante a criação de identificadores de erro (acessados por meio da propriedade da classe ErrorRecord FullyQualifiedErrorId) tenha em mente o seguinte.</span><span class="sxs-lookup"><span data-stu-id="df985-141">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="df985-142">Usar cadeias de caracteres que são direcionadas para fins de diagnóstico para que, ao inspecionar o identificador totalmente qualificado, você pode determinar que o erro é e onde o erro veio de.</span><span class="sxs-lookup"><span data-stu-id="df985-142">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="df985-143">Um identificador de erro bem formado de totalmente qualificado pode ser da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="df985-143">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

<span data-ttu-id="df985-144">Observe que no exemplo anterior, o identificador de erro (o primeiro token) que designa qual é o erro e a parte restante indica de onde veio o erro.</span><span class="sxs-lookup"><span data-stu-id="df985-144">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="df985-145">Para cenários mais complexos, o identificador de erro pode ser um token de ponto separado que pode ser analisado na inspeção.</span><span class="sxs-lookup"><span data-stu-id="df985-145">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span> <span data-ttu-id="df985-146">Isso permite que você ramificar muito nas partes do identificador de erro, bem como a categoria de erro e o identificador de erro.</span><span class="sxs-lookup"><span data-stu-id="df985-146">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="df985-147">O cmdlet deve atribuir os identificadores de erro específicas para diferentes caminhos de código.</span><span class="sxs-lookup"><span data-stu-id="df985-147">The cmdlet should assign specific error identifiers to different code paths.</span></span> <span data-ttu-id="df985-148">Lembre-se as informações a seguir para a atribuição de identificadores de erro:</span><span class="sxs-lookup"><span data-stu-id="df985-148">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="df985-149">Um identificador de erro deve permanecer constante ao longo do ciclo de vida do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df985-149">An error identifier should remain constant throughout the cmdlet life cycle.</span></span> <span data-ttu-id="df985-150">Não altere a semântica de um identificador de erro entre as versões do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df985-150">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="df985-151">Use o texto de um identificador de erro tersely corresponde ao erro que está sendo relatado.</span><span class="sxs-lookup"><span data-stu-id="df985-151">Use text for an error identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="df985-152">Não use espaço em branco ou pontuação.</span><span class="sxs-lookup"><span data-stu-id="df985-152">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="df985-153">Ter seu cmdlet gerar somente os identificadores de erro que podem ser reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="df985-153">Have your cmdlet generate only error identifiers that are reproducible.</span></span> <span data-ttu-id="df985-154">Por exemplo, ele não deve gerar um identificador que inclui um identificador de processo.</span><span class="sxs-lookup"><span data-stu-id="df985-154">For example, it should not generate an identifier that includes a process identifier.</span></span> <span data-ttu-id="df985-155">Identificadores de erro são úteis para um usuário somente quando eles correspondem aos identificadores que são vistos por outros usuários tiver o mesmo problema.</span><span class="sxs-lookup"><span data-stu-id="df985-155">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="df985-156">Exceções não tratadas não são detectadas pelo Windows PowerShell nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="df985-156">Unhandled exceptions are not caught by Windows PowerShell in the following conditions:</span></span>

- <span data-ttu-id="df985-157">Se um cmdlet cria um novo thread e o código que executa o thread gerará uma exceção sem tratamento, o Windows PowerShell não irá capturar o erro e encerrará o processo.</span><span class="sxs-lookup"><span data-stu-id="df985-157">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="df985-158">Se um objeto tiver um código em seu destruidor ou métodos Dispose que faz com que uma exceção sem tratamento, o Windows PowerShell não irá capturar o erro e encerrará o processo.</span><span class="sxs-lookup"><span data-stu-id="df985-158">If an object has code in its destructor or Dispose methods that causes an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="df985-159">Relatando erros sem encerramento</span><span class="sxs-lookup"><span data-stu-id="df985-159">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="df985-160">Qualquer um dos métodos de processamento de entrada pode relatar um erro sem encerramento no fluxo de saída usando o [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método.</span><span class="sxs-lookup"><span data-stu-id="df985-160">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="df985-161">Aqui está um exemplo de código desse cmdlet Get-Proc que ilustra a chamada para [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) de dentro a substituição do [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="df985-161">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="df985-162">Nesse caso, a chamada será feita se o cmdlet não é possível localizar um processo para um identificador de processo especificado.</span><span class="sxs-lookup"><span data-stu-id="df985-162">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="df985-163">Itens a lembrar sobre a escrita de erros sem encerramento</span><span class="sxs-lookup"><span data-stu-id="df985-163">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="df985-164">Para um erro sem encerramento, o cmdlet deve gerar um identificador de erro específico para cada objeto de entrada específico.</span><span class="sxs-lookup"><span data-stu-id="df985-164">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="df985-165">Um cmdlet com frequência precisa modificar a ação do Windows PowerShell produzida por um erro sem encerramento.</span><span class="sxs-lookup"><span data-stu-id="df985-165">A cmdlet frequently needs to modify the Windows PowerShell action produced by a nonterminating error.</span></span> <span data-ttu-id="df985-166">Ele pode fazer isso definindo a `ErrorAction` e `ErrorVariable` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="df985-166">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span> <span data-ttu-id="df985-167">Se definir a `ErrorAction` parâmetro, o cmdlet apresenta as opções de usuário [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), você também posso influenciar diretamente a ação, definindo o `$ErrorActionPreference` variável.</span><span class="sxs-lookup"><span data-stu-id="df985-167">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="df985-168">O cmdlet pode salvar erros sem encerramento em uma variável usando o `ErrorVariable` parâmetro, que não é afetado pela configuração da `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="df985-168">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span> <span data-ttu-id="df985-169">Falhas podem ser anexadas a uma variável de erro existente adicionando um sinal de adição (+) na frente do nome da variável.</span><span class="sxs-lookup"><span data-stu-id="df985-169">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="df985-170">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="df985-170">Code Sample</span></span>

<span data-ttu-id="df985-171">Para o completo C# exemplos de código, consulte [GetProcessSample04 amostra](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="df985-171">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="df985-172">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="df985-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="df985-173">Windows PowerShell passa informações entre cmdlets usando objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="df985-173">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="df985-174">Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet, ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df985-174">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="df985-175">Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="df985-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="df985-176">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df985-176">Building the Cmdlet</span></span>

<span data-ttu-id="df985-177">Depois de implementar um cmdlet, você deve registrá-lo com o Windows PowerShell por meio de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df985-177">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="df985-178">Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="df985-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="df985-179">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df985-179">Testing the Cmdlet</span></span>

<span data-ttu-id="df985-180">Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="df985-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="df985-181">Vamos testar o cmdlet Get-Proc de exemplo para ver se ele relata um erro:</span><span class="sxs-lookup"><span data-stu-id="df985-181">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="df985-182">Inicie o Windows PowerShell e use o cmdlet Get-Proc para recuperar os processos denominados "Teste".</span><span class="sxs-lookup"><span data-stu-id="df985-182">Start Windows PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="df985-183">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="df985-183">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="df985-184">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="df985-184">See Also</span></span>

[<span data-ttu-id="df985-185">Adicionar parâmetros de entrada do Pipeline de processo</span><span class="sxs-lookup"><span data-stu-id="df985-185">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="df985-186">Adicionar parâmetros que processam a entrada de linha de comando</span><span class="sxs-lookup"><span data-stu-id="df985-186">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="df985-187">Criando seu primeiro Cmdlet</span><span class="sxs-lookup"><span data-stu-id="df985-187">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="df985-188">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="df985-188">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="df985-189">Como registrar Cmdlets, provedores e aplicativos de Host</span><span class="sxs-lookup"><span data-stu-id="df985-189">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="df985-190">Referência do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="df985-190">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="df985-191">Exemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="df985-191">Cmdlet Samples</span></span>](./cmdlet-samples.md)
