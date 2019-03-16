---
title: Adicionar mensagens de usuário ao seu Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 5b3a5f5d5d02c7d5a3c1d622ec1a3740739c694f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055029"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="5fb14-102">Adicionar mensagens de usuário para o cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fb14-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="5fb14-103">Cmdlets pode gravar vários tipos de mensagens que podem ser exibidos ao usuário no tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fb14-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="5fb14-104">Essas mensagens incluem os seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="5fb14-104">These messages include the following types:</span></span>

- <span data-ttu-id="5fb14-105">Mensagens detalhadas que contêm informações gerais de usuário.</span><span class="sxs-lookup"><span data-stu-id="5fb14-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="5fb14-106">Mensagens que contêm informações de solução de problemas de depuração.</span><span class="sxs-lookup"><span data-stu-id="5fb14-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="5fb14-107">Mensagens de aviso que contêm uma notificação de que o cmdlet está prestes a realizar uma operação que pode ter resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="5fb14-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="5fb14-108">Relatório de progresso, mensagens que contêm informações sobre a quantidade funcionar o cmdlet foi concluída ao executar uma operação que demora muito tempo.</span><span class="sxs-lookup"><span data-stu-id="5fb14-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="5fb14-109">Não há nenhum limite para o número de mensagens que seu cmdlet pode gravar ou o tipo de mensagens que grava seu cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fb14-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="5fb14-110">Cada mensagem é gravada, fazendo uma chamada específica de dentro da método do seu cmdlet de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="5fb14-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="5fb14-111">O StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fb14-111">The StopProc Cmdlet</span></span>

<span data-ttu-id="5fb14-112">Os tópicos nesta seção incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5fb14-112">Topics in this section include the following:</span></span>

- [<span data-ttu-id="5fb14-113">Definindo o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fb14-113">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="5fb14-114">Definir parâmetros para modificação do sistema</span><span class="sxs-lookup"><span data-stu-id="5fb14-114">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="5fb14-115">Substituindo uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="5fb14-115">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="5fb14-116">Gravar uma mensagem detalhada</span><span class="sxs-lookup"><span data-stu-id="5fb14-116">Writing a Verbose Message</span></span>](#Writing-a-Verbose-Message)

- [<span data-ttu-id="5fb14-117">Gravar uma mensagem de depuração</span><span class="sxs-lookup"><span data-stu-id="5fb14-117">Writing a Debug Message</span></span>](#Writing-a-Debug-Message)

- [<span data-ttu-id="5fb14-118">Gravar uma mensagem de aviso</span><span class="sxs-lookup"><span data-stu-id="5fb14-118">Writing a Warning Message</span></span>](#Writing-a-Warning-Message)

- [<span data-ttu-id="5fb14-119">Gravar uma mensagem de progresso</span><span class="sxs-lookup"><span data-stu-id="5fb14-119">Writing a Progress Message</span></span>](#Writing-a-Progress-Message)

- [<span data-ttu-id="5fb14-120">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5fb14-120">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="5fb14-121">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="5fb14-121">Define Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="5fb14-122">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fb14-122">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="5fb14-123">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fb14-123">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="5fb14-124">Definindo o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fb14-124">Defining the Cmdlet</span></span>

<span data-ttu-id="5fb14-125">A primeira etapa na criação de cmdlet sempre é o cmdlet de nomenclatura e declarar a classe .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fb14-125">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="5fb14-126">Qualquer tipo de cmdlet pode gravar as notificações do usuário de seu métodos; de processamento de entrada em geral, você pode nomear este cmdlet usando qualquer verbo que indica quais modificações no sistema que executa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fb14-126">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="5fb14-127">Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="5fb14-127">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="5fb14-128">O cmdlet Stop-Proc foi projetado para modificar o sistema; Portanto, o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaração para a classe do .NET deve incluir o `SupportsShouldProcess` palavra-chave de atributo e definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="5fb14-128">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="5fb14-129">O código a seguir é a definição para essa classe do cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="5fb14-129">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="5fb14-130">Para obter mais informações sobre essa definição, consulte [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="5fb14-130">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="5fb14-131">Definir parâmetros para modificação do sistema</span><span class="sxs-lookup"><span data-stu-id="5fb14-131">Defining Parameters for System Modification</span></span>

<span data-ttu-id="5fb14-132">O cmdlet Stop-Proc define três parâmetros: `Name`, `Force`, e `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="5fb14-132">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="5fb14-133">Para obter mais informações sobre como definir esses parâmetros, consulte [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="5fb14-133">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="5fb14-134">Aqui está a declaração de parâmetro para o cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="5fb14-134">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="5fb14-135">Substituindo uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="5fb14-135">Overriding an Input Processing Method</span></span>

<span data-ttu-id="5fb14-136">O cmdlet deve substituir uma método de processamento de entrada, geralmente será [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="5fb14-136">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="5fb14-137">Esse cmdlet Stop-Proc substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) o método de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="5fb14-137">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="5fb14-138">Nessa implementação do cmdlet Stop-Proc, as chamadas são feitas para gravar as mensagens detalhadas, mensagens de depuração e mensagens de aviso.</span><span class="sxs-lookup"><span data-stu-id="5fb14-138">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="5fb14-139">Para obter mais informações sobre como esse método chama o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos, consulte [Criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="5fb14-139">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="5fb14-140">Gravar uma mensagem detalhada</span><span class="sxs-lookup"><span data-stu-id="5fb14-140">Writing a Verbose Message</span></span>

<span data-ttu-id="5fb14-141">O [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método é usado para gravar informações gerais de nível de usuário que está relacionadas a condições de erro específicas.</span><span class="sxs-lookup"><span data-stu-id="5fb14-141">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="5fb14-142">O administrador do sistema, em seguida, pode usar essas informações para continuar processando outros comandos.</span><span class="sxs-lookup"><span data-stu-id="5fb14-142">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="5fb14-143">Além disso, qualquer informação escrita usando esse método deve ser localizada, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="5fb14-143">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="5fb14-144">O código a seguir desse cmdlet Stop-Proc mostra duas chamadas para o [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método de substituição do [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="5fb14-144">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="5fb14-145">Gravar uma mensagem de depuração</span><span class="sxs-lookup"><span data-stu-id="5fb14-145">Writing a Debug Message</span></span>

<span data-ttu-id="5fb14-146">O [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método é usado para gravar mensagens de depuração que podem ser usadas para solucionar problemas da operação do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fb14-146">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="5fb14-147">A chamada é feita de uma método de processamento de entrada.</span><span class="sxs-lookup"><span data-stu-id="5fb14-147">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="5fb14-148">Windows PowerShell também define um `Debug` parâmetro que apresenta ambos detalhado e informações de depuração.</span><span class="sxs-lookup"><span data-stu-id="5fb14-148">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="5fb14-149">Se seu cmdlet oferece suporte a esse parâmetro, ele não precisa chamar [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) no mesmo código que chama [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .</span><span class="sxs-lookup"><span data-stu-id="5fb14-149">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="5fb14-150">Duas seções de código do cmdlet Stop-Proc exemplo a seguir mostram as chamadas para o [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método de substituição do [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="5fb14-150">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="5fb14-151">Essa mensagem de depuração é gravada imediatamente antes [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) é chamado.</span><span class="sxs-lookup"><span data-stu-id="5fb14-151">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="5fb14-152">Essa mensagem de depuração é gravada imediatamente antes [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) é chamado.</span><span class="sxs-lookup"><span data-stu-id="5fb14-152">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="5fb14-153">Windows PowerShell roteia automaticamente qualquer [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) chamadas para os cmdlets e infra-estrutura de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5fb14-153">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="5fb14-154">Isso permite que as chamadas de método a ser rastreado para o aplicativo de hospedagem, um arquivo ou um depurador sem precisar fazer qualquer trabalho adicional de desenvolvimento dentro do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fb14-154">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="5fb14-155">A entrada de linha de comando a seguir implementa uma operação de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="5fb14-155">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="5fb14-156">**PS > Parar rastreamento-expression-proc-arquivo proc.log-bloco de notas do comando stop-proc**</span><span class="sxs-lookup"><span data-stu-id="5fb14-156">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="5fb14-157">Gravar uma mensagem de aviso</span><span class="sxs-lookup"><span data-stu-id="5fb14-157">Writing a Warning Message</span></span>

<span data-ttu-id="5fb14-158">O [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método é usado para gravar um aviso quando o cmdlet está prestes a realizar uma operação que pode ter um resultado inesperado, por exemplo, substituição de um arquivo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="5fb14-158">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="5fb14-159">O código do cmdlet Stop-Proc exemplo a seguir mostra a chamada para o [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método de substituição do [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="5fb14-159">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="5fb14-160">Gravar uma mensagem de progresso</span><span class="sxs-lookup"><span data-stu-id="5fb14-160">Writing a Progress Message</span></span>

<span data-ttu-id="5fb14-161">O [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) é usado para gravar mensagens de progresso quando operações de cmdlet levar um longo período de tempo para ser concluída.</span><span class="sxs-lookup"><span data-stu-id="5fb14-161">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="5fb14-162">Uma chamada para [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passa um [progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) objeto que é enviado ao aplicativo de hospedagem para renderização para o usuário.</span><span class="sxs-lookup"><span data-stu-id="5fb14-162">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="5fb14-163">Esse cmdlet Stop-Proc não inclui uma chamada para o [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.</span><span class="sxs-lookup"><span data-stu-id="5fb14-163">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="5fb14-164">O código a seguir é um exemplo de uma mensagem de progresso, escrito por um cmdlet que está tentando copiar um item.</span><span class="sxs-lookup"><span data-stu-id="5fb14-164">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="5fb14-165">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5fb14-165">Code Sample</span></span>

<span data-ttu-id="5fb14-166">Para o completo C# exemplos de código, consulte [StopProcessSample02 amostra](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5fb14-166">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="5fb14-167">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="5fb14-167">Define Object Types and Formatting</span></span>

<span data-ttu-id="5fb14-168">Windows PowerShell passa informações entre cmdlets usando objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="5fb14-168">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="5fb14-169">Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet, ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fb14-169">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="5fb14-170">Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="5fb14-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="5fb14-171">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fb14-171">Building the Cmdlet</span></span>

<span data-ttu-id="5fb14-172">Depois de implementar um cmdlet, ele deve ser registrado com o Windows PowerShell por meio de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fb14-172">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="5fb14-173">Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="5fb14-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="5fb14-174">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fb14-174">Testing the Cmdlet</span></span>

<span data-ttu-id="5fb14-175">Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="5fb14-175">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="5fb14-176">Vamos testar o exemplo de cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="5fb14-176">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="5fb14-177">Para obter mais informações sobre como usar os cmdlets da linha de comando, consulte o [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="5fb14-177">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="5fb14-178">A entrada de linha de comando a seguir usa Proc Stop para interromper o processo de chamada "NOTEPAD", forneça notificações detalhadas e imprimir informações de depuração.</span><span class="sxs-lookup"><span data-stu-id="5fb14-178">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="5fb14-179">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="5fb14-179">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="5fb14-180">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5fb14-180">See Also</span></span>

[<span data-ttu-id="5fb14-181">Criar um Cmdlet que modifica o sistema</span><span class="sxs-lookup"><span data-stu-id="5fb14-181">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="5fb14-182">Como criar um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fb14-182">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="5fb14-183">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="5fb14-183">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="5fb14-184">Como registrar Cmdlets, provedores e aplicativos de Host</span><span class="sxs-lookup"><span data-stu-id="5fb14-184">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="5fb14-185">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fb14-185">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
