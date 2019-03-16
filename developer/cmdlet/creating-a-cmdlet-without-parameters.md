---
title: Criação de um Cmdlet sem parâmetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: c380b28570c955de6f41152fd617f5c1b0f9e4bd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054689"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="f3d49-102">Criar um cmdlet sem parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3d49-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="f3d49-103">Esta seção descreve como criar um cmdlet que recupera informações do computador local sem o uso de parâmetros e, em seguida, grava as informações para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="f3d49-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="f3d49-104">O cmdlet descrito aqui é um cmdlet Get-Proc que recupera informações sobre os processos do computador local e, em seguida, exibe essas informações na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f3d49-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

<span data-ttu-id="f3d49-105">Os tópicos nesta seção incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f3d49-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="f3d49-106">O Cmdlet de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="f3d49-106">Naming the Cmdlet</span></span>](#Naming-the-Cmdlet)

- [<span data-ttu-id="f3d49-107">Definição da classe do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f3d49-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="f3d49-108">Substituindo uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="f3d49-108">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="f3d49-109">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f3d49-109">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="f3d49-110">Definindo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="f3d49-110">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="f3d49-111">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f3d49-111">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="f3d49-112">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f3d49-112">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

> [!NOTE]
> <span data-ttu-id="f3d49-113">Lembre-se de que ao gravar cmdlets, os assemblies de referência Windows PowerShell® são baixados para o disco (por padrão em C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). Eles não estão instalados no Cache de Assembly Global (GAC).</span><span class="sxs-lookup"><span data-stu-id="f3d49-113">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="f3d49-114">O Cmdlet de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="f3d49-114">Naming the Cmdlet</span></span>

<span data-ttu-id="f3d49-115">Um nome de cmdlet consiste em um verbo que indica que a ação que o cmdlet usa e um substantivo que indica os itens que o cmdlet atua.</span><span class="sxs-lookup"><span data-stu-id="f3d49-115">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="f3d49-116">Como esse exemplo de cmdlet Get-Proc recupera objetos de processo, ele usa o verbo "Get", definido pela [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeração e o substantivo "Processo" para indicar que o cmdlet funciona em itens de processo.</span><span class="sxs-lookup"><span data-stu-id="f3d49-116">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="f3d49-117">Ao nomear os cmdlets, não use nenhum dos seguintes caracteres: #, () {} [] & - / \ $;: "' <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="f3d49-117">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="f3d49-118">@ \` .</span><span class="sxs-lookup"><span data-stu-id="f3d49-118">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="f3d49-119">Escolhendo um substantivo</span><span class="sxs-lookup"><span data-stu-id="f3d49-119">Choosing a Noun</span></span>

<span data-ttu-id="f3d49-120">Você deve escolher um substantivo específico.</span><span class="sxs-lookup"><span data-stu-id="f3d49-120">You should choose a noun that is specific.</span></span> <span data-ttu-id="f3d49-121">É melhor usar um substantivo no singular prefixado com uma versão abreviada do nome do produto.</span><span class="sxs-lookup"><span data-stu-id="f3d49-121">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="f3d49-122">Um nome de cmdlet de exemplo desse tipo é "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="f3d49-122">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="f3d49-123">Escolhendo um verbo</span><span class="sxs-lookup"><span data-stu-id="f3d49-123">Choosing a Verb</span></span>

<span data-ttu-id="f3d49-124">Você deve usar um verbo do conjunto de nomes de verbos aprovados do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3d49-124">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="f3d49-125">Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="f3d49-125">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="f3d49-126">Definição da classe do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f3d49-126">Defining the Cmdlet Class</span></span>

<span data-ttu-id="f3d49-127">Depois de escolher um nome de cmdlet, defina uma classe do .NET para implementar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3d49-127">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="f3d49-128">Aqui está a definição de classe para esse cmdlet Get-Proc de exemplo:</span><span class="sxs-lookup"><span data-stu-id="f3d49-128">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="f3d49-129">Observe que o anterior para a definição de classe, o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo, com a sintaxe `[Cmdlet(verb, noun, ...)]`, é usado para identificar essa classe como um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3d49-129">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="f3d49-130">Isso é o único atributo obrigatório para todos os cmdlets e permite que o tempo de execução do Windows PowerShell chamá-los corretamente.</span><span class="sxs-lookup"><span data-stu-id="f3d49-130">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="f3d49-131">Você pode definir palavras-chave de atributo adicional declarar a classe, se necessário.</span><span class="sxs-lookup"><span data-stu-id="f3d49-131">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="f3d49-132">Lembre-se de que a declaração de atributo para nosso exemplo de classe GetProcCommand declara apenas os nomes de verbo e um substantivo para o cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="f3d49-132">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="f3d49-133">Para todas as classes de atributo do Windows PowerShell, as palavras-chave que você pode definir correspondem às propriedades da classe de atributo.</span><span class="sxs-lookup"><span data-stu-id="f3d49-133">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="f3d49-134">Ao nomear a classe do cmdlet, é uma boa prática para refletir o nome do cmdlet no nome da classe.</span><span class="sxs-lookup"><span data-stu-id="f3d49-134">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="f3d49-135">Para fazer isso, use o formulário "VerbNounCommand" e substitua "Verbo" e "Substantivo" com o verbo e substantivo usado no nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3d49-135">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="f3d49-136">Conforme é mostrado na definição de classe anteriores, o cmdlet Get-Proc de exemplo define uma classe chamada GetProcCommand, que deriva de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe base.</span><span class="sxs-lookup"><span data-stu-id="f3d49-136">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f3d49-137">Se você quiser definir um cmdlet que acessa o tempo de execução do Windows PowerShell diretamente, sua classe do .NET deve derivar de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base.</span><span class="sxs-lookup"><span data-stu-id="f3d49-137">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="f3d49-138">Para obter mais informações sobre essa classe, consulte [criando um Cmdlet que conjuntos de parâmetros define](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="f3d49-138">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f3d49-139">A classe para um cmdlet deve ser explicitamente marcada como pública.</span><span class="sxs-lookup"><span data-stu-id="f3d49-139">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="f3d49-140">Classes que não são marcadas como públicos padrão serão interno e não serão encontradas pelo tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3d49-140">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="f3d49-141">O Windows PowerShell usa o [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace para suas classes de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3d49-141">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="f3d49-142">É recomendável colocar suas classes de cmdlet em um namespace de comandos do seu namespace de API, por exemplo, xxx.PS.Commands.</span><span class="sxs-lookup"><span data-stu-id="f3d49-142">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="f3d49-143">Substituindo uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="f3d49-143">Overriding an Input Processing Method</span></span>

<span data-ttu-id="f3d49-144">O [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe fornece três métodos de processamento de entrada principal, pelo menos um dos quais deve substituir seu cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3d49-144">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="f3d49-145">Para obter mais informações sobre como o Windows PowerShell processa registros, consulte [como o Windows PowerShell funciona](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="f3d49-145">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

<span data-ttu-id="f3d49-146">Para todos os tipos de entrada, o tempo de execução do Windows PowerShell chama [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) para habilitar o processamento.</span><span class="sxs-lookup"><span data-stu-id="f3d49-146">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="f3d49-147">Se seu cmdlet deve executar algum pré-processamento ou a instalação, ele pode fazer isso substituindo esse método.</span><span class="sxs-lookup"><span data-stu-id="f3d49-147">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="f3d49-148">Windows PowerShell usa o termo "Registro" para descrever o conjunto de valores de parâmetro fornecido quando um cmdlet é chamado.</span><span class="sxs-lookup"><span data-stu-id="f3d49-148">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="f3d49-149">Se seu cmdlet aceita entrada do pipeline, ele deve substituir a [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método e, opcionalmente, o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)método.</span><span class="sxs-lookup"><span data-stu-id="f3d49-149">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="f3d49-150">Por exemplo, um cmdlet pode substituir os dois métodos se ele reúne todas as entrada usando [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) e, em seguida, opera na entrada como um todo, em vez de um elemento por vez, como o `Sort-Object` cmdlet faz.</span><span class="sxs-lookup"><span data-stu-id="f3d49-150">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="f3d49-151">Se seu cmdlet não aceita entrada do pipeline, ele deve substituir a [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="f3d49-151">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="f3d49-152">Lembre-se de que esse método é frequentemente usado no lugar de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) quando o cmdlet não pode operar em um elemento por vez, como no caso de um cmdlet de classificação.</span><span class="sxs-lookup"><span data-stu-id="f3d49-152">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="f3d49-153">Como esse exemplo de cmdlet Get-Proc deve receber entrada do pipeline, ele substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método e usa as implementações padrão para [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) e [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="f3d49-153">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="f3d49-154">O [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) substituição recupera processos e os grava em linha de comando usando o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método.</span><span class="sxs-lookup"><span data-stu-id="f3d49-154">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="f3d49-155">Coisas a serem lembrados sobre o processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="f3d49-155">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="f3d49-156">A fonte padrão para a entrada é um objeto explícito (por exemplo, uma cadeia de caracteres) fornecido pelo usuário na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f3d49-156">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="f3d49-157">Para obter mais informações, consulte [criação de um Cmdlet para entrada de linha de comando de processo](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="f3d49-157">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="f3d49-158">Uma método de processamento de entrada também pode receber entrada de objeto de saída de um cmdlet upstream no pipeline.</span><span class="sxs-lookup"><span data-stu-id="f3d49-158">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="f3d49-159">Para obter mais informações, consulte [criação de um Cmdlet para entrada de Pipeline de processo](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="f3d49-159">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="f3d49-160">Lembre-se que seu cmdlet pode receber entrada de uma combinação de linha de comando e um pipeline de códigos-fonte.</span><span class="sxs-lookup"><span data-stu-id="f3d49-160">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="f3d49-161">O cmdlet downstream pode não retornar por um longo tempo ou não.</span><span class="sxs-lookup"><span data-stu-id="f3d49-161">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="f3d49-162">Por esse motivo, a método no seu cmdlet de processamento de entrada deve não mantenha bloqueios durante as chamadas para [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especialmente os bloqueios para a qual o escopo ultrapasse a instância do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3d49-162">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f3d49-163">Cmdlets nunca deve chamar [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) ou seu equivalente.</span><span class="sxs-lookup"><span data-stu-id="f3d49-163">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="f3d49-164">Seu cmdlet pode ter variáveis de objeto a ser limpo quando ele for concluído processamento (por exemplo, se ele é aberto em um identificador de arquivo a [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método e mantém o identificador aberto para uso pelo [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="f3d49-164">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="f3d49-165">É importante lembrar-se de que o tempo de execução do Windows PowerShell não sempre chamar o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método, que deve executar a limpeza do objeto.</span><span class="sxs-lookup"><span data-stu-id="f3d49-165">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="f3d49-166">Por exemplo, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) não poderá ser chamado se o cmdlet foi cancelado no centro ou se um encerramento ocorrerá erro em qualquer parte do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3d49-166">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="f3d49-167">Portanto, um cmdlet que requer a limpeza do objeto deve implementar completo [System. IDisposable](/dotnet/api/System.IDisposable) padrão, incluindo o finalizador, para que o tempo de execução possa chamar ambos [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) no final do processamento.</span><span class="sxs-lookup"><span data-stu-id="f3d49-167">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f3d49-168">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="f3d49-168">Code Sample</span></span>

<span data-ttu-id="f3d49-169">Para o completo C# exemplos de código, consulte [exemplo GetProcessSample01](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f3d49-169">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="f3d49-170">Definindo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="f3d49-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="f3d49-171">Windows PowerShell passa informações entre cmdlets usando objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="f3d49-171">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="f3d49-172">Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet, ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f3d49-172">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="f3d49-173">Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="f3d49-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="f3d49-174">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f3d49-174">Building the Cmdlet</span></span>

<span data-ttu-id="f3d49-175">Depois de implementar um cmdlet, você deve registrá-lo com o Windows PowerShell por meio de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3d49-175">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="f3d49-176">Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="f3d49-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="f3d49-177">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f3d49-177">Testing the Cmdlet</span></span>

<span data-ttu-id="f3d49-178">Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f3d49-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="f3d49-179">O código para nosso exemplo de cmdlet Get-Proc é pequeno, mas ainda usa o tempo de execução do Windows PowerShell e um objeto existente do .NET, que é suficiente para torná-lo útil.</span><span class="sxs-lookup"><span data-stu-id="f3d49-179">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="f3d49-180">Vamos testá-lo para entender melhor o que Get-Proc pode fazer e como sua saída pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="f3d49-180">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="f3d49-181">Para obter mais informações sobre como usar os cmdlets da linha de comando, consulte o [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="f3d49-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="f3d49-182">Inicie o Windows PowerShell e obter os processos atuais em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="f3d49-182">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="f3d49-183">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="f3d49-183">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="f3d49-184">Atribua uma variável para os resultados do cmdlet para facilitar a manipulação.</span><span class="sxs-lookup"><span data-stu-id="f3d49-184">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="f3d49-185">Obtenha o número de processos.</span><span class="sxs-lookup"><span data-stu-id="f3d49-185">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="f3d49-186">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="f3d49-186">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="f3d49-187">Recupere um processo específico.</span><span class="sxs-lookup"><span data-stu-id="f3d49-187">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="f3d49-188">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="f3d49-188">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="f3d49-189">Obter a hora de início desse processo.</span><span class="sxs-lookup"><span data-stu-id="f3d49-189">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="f3d49-190">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="f3d49-190">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="f3d49-191">Obter os processos para o qual a contagem de identificadores é maior que 500 e classificar o resultado.</span><span class="sxs-lookup"><span data-stu-id="f3d49-191">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="f3d49-192">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="f3d49-192">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="f3d49-193">Use o `Get-Member` cmdlet para listar as propriedades disponíveis para cada processo.</span><span class="sxs-lookup"><span data-stu-id="f3d49-193">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="f3d49-194">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="f3d49-194">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="f3d49-195">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f3d49-195">See Also</span></span>

[<span data-ttu-id="f3d49-196">Criação de um Cmdlet para processar a entrada de linha de comando</span><span class="sxs-lookup"><span data-stu-id="f3d49-196">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="f3d49-197">Criação de um Cmdlet para processar a entrada de Pipeline</span><span class="sxs-lookup"><span data-stu-id="f3d49-197">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="f3d49-198">Como criar um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3d49-198">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="f3d49-199">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="f3d49-199">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="f3d49-200">Como funciona o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3d49-200">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="f3d49-201">Como registrar Cmdlets, provedores e aplicativos de Host</span><span class="sxs-lookup"><span data-stu-id="f3d49-201">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="f3d49-202">Referência do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3d49-202">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="f3d49-203">Exemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="f3d49-203">Cmdlet Samples</span></span>](./cmdlet-samples.md)