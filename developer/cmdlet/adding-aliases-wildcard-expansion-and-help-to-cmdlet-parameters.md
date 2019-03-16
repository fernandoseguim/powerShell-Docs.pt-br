---
title: Adicionar Aliases, expansão de curinga e ajudar a parâmetros de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: db664e589f625855b5a33a02c522d6b238ad2810
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054859"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="5d382-102">Adicionar aliases, expansão de curinga e ajuda a parâmetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d382-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="5d382-103">Esta seção descreve como adicionar aliases, expansão de curinga, e mensagens de ajuda para os parâmetros do cmdlet Stop-Proc (descrito na [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="5d382-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="5d382-104">Esse cmdlet Stop-Proc tenta interromper os processos que são recuperados usando o cmdlet Get-Proc (descrito na [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="5d382-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="5d382-105">Os tópicos nesta seção incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5d382-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="5d382-106">Definindo o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d382-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="5d382-107">Definir parâmetros para modificação do sistema</span><span class="sxs-lookup"><span data-stu-id="5d382-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="5d382-108">Definir um Alias de parâmetro</span><span class="sxs-lookup"><span data-stu-id="5d382-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="5d382-109">Ajuda para os parâmetros de criação</span><span class="sxs-lookup"><span data-stu-id="5d382-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="5d382-110">Substituindo uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="5d382-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="5d382-111">Suporte à expansão de curinga</span><span class="sxs-lookup"><span data-stu-id="5d382-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="5d382-112">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5d382-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="5d382-113">Definindo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="5d382-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="5d382-114">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d382-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="5d382-115">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d382-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="5d382-116">Definindo o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d382-116">Defining the Cmdlet</span></span>

<span data-ttu-id="5d382-117">A primeira etapa na criação de cmdlet sempre é o cmdlet de nomenclatura e declarar a classe .NET que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5d382-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="5d382-118">Porque você está escrevendo um cmdlet para alterar o sistema, ele deve ser nomeado adequadamente.</span><span class="sxs-lookup"><span data-stu-id="5d382-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="5d382-119">Como este cmdlet interrompe os processos do sistema, ele usa o verbo "Stop", definido pela [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe, com o substantivo "Processo" para indicar o processo.</span><span class="sxs-lookup"><span data-stu-id="5d382-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="5d382-120">Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="5d382-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="5d382-121">O código a seguir é a definição de classe para esse cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="5d382-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="5d382-122">Definir parâmetros para modificação do sistema</span><span class="sxs-lookup"><span data-stu-id="5d382-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="5d382-123">O cmdlet precisa definir os parâmetros que modificações no sistema de suporte e comentários do usuário.</span><span class="sxs-lookup"><span data-stu-id="5d382-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="5d382-124">O cmdlet deve definir um `Name` parâmetro ou equivalente para que o cmdlet será capaz de modificar o sistema por algum tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="5d382-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="5d382-125">Além disso, o cmdlet deve definir a `Force` e `PassThru` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5d382-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="5d382-126">Para obter mais informações sobre esses parâmetros, consulte [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="5d382-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="5d382-127">Definir um Alias de parâmetro</span><span class="sxs-lookup"><span data-stu-id="5d382-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="5d382-128">Um alias de parâmetro pode ser um nome alternativo ou bem-definidos 1 ou 2 letras nome curto para um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5d382-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="5d382-129">Em ambos os casos, o objetivo de usar aliases é simplificar a entrada do usuário na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="5d382-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="5d382-130">Windows PowerShell dá suporte a aliases de parâmetro por meio de [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, que usa a sintaxe de declaração [Alias()].</span><span class="sxs-lookup"><span data-stu-id="5d382-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="5d382-131">O código a seguir mostra como um alias é adicionado para o `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5d382-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="5d382-132">Além de usar o [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atributo, o tempo de execução do Windows PowerShell executa a correspondência de nome parcial, mesmo se nenhum alias for especificadas.</span><span class="sxs-lookup"><span data-stu-id="5d382-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="5d382-133">Por exemplo, se seu cmdlet possui um `FileName` parâmetro e que é o único parâmetro que começa com `F`, o usuário poderia digitar `Filename`, `Filenam`, `File`, `Fi`, ou `F` e ainda reconhecer a entrada, como o `FileName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5d382-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="5d382-134">Ajuda para os parâmetros de criação</span><span class="sxs-lookup"><span data-stu-id="5d382-134">Creating Help for Parameters</span></span>

<span data-ttu-id="5d382-135">Windows PowerShell permite que você crie a Ajuda para os parâmetros de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5d382-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="5d382-136">Faça isso para qualquer parâmetro usado para comentários de usuário e a modificação do sistema.</span><span class="sxs-lookup"><span data-stu-id="5d382-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="5d382-137">Para cada parâmetro dar suporte à Ajuda, você pode definir as `HelpMessage` palavra-chave de atributo o [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração do atributo.</span><span class="sxs-lookup"><span data-stu-id="5d382-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="5d382-138">Essa palavra-chave define o texto a ser exibido ao usuário para assistência usando o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5d382-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="5d382-139">Você também pode definir o `HelpMessageBaseName` palavra-chave para identificar o nome de base de um recurso a ser usado para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="5d382-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="5d382-140">Se você definir essa palavra-chave, você também deve definir o `HelpMessageResourceId` palavra-chave para especificar o identificador de recurso.</span><span class="sxs-lookup"><span data-stu-id="5d382-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="5d382-141">O código a seguir desse cmdlet Stop-Proc define o `HelpMessage` atributo a palavra-chave para o `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5d382-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="5d382-142">Substituindo uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="5d382-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="5d382-143">O cmdlet deve substituir uma método de processamento de entrada, mais frequentemente, isso será [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="5d382-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="5d382-144">Ao modificar o sistema, o cmdlet deve chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para permitir que o usuário para fornecer comentários antes que uma alteração é feita.</span><span class="sxs-lookup"><span data-stu-id="5d382-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="5d382-145">Para obter mais informações sobre esses métodos, consulte [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="5d382-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="5d382-146">Suporte à expansão de curinga</span><span class="sxs-lookup"><span data-stu-id="5d382-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="5d382-147">Para permitir que a seleção de vários objetos, o cmdlet pode usar o [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) e [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes para fornecer suporte de expansão de curinga para o parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="5d382-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="5d382-148">São exemplos de padrões de curinga de lsa \* \*. txt e [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="5d382-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="5d382-149">Use o caractere de acento (') como um caractere de escape quando o padrão contém um caractere que deve ser usado literalmente.</span><span class="sxs-lookup"><span data-stu-id="5d382-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="5d382-150">Expansões de curinga de nomes de arquivo e caminho são exemplos de cenários comuns em que o cmdlet talvez queira permitir que o suporte para entradas de caminho quando a seleção de vários objetos é necessária.</span><span class="sxs-lookup"><span data-stu-id="5d382-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="5d382-151">Um caso comum é no sistema de arquivos, em que um usuário quiser ver todos os arquivos que residem na pasta atual.</span><span class="sxs-lookup"><span data-stu-id="5d382-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="5d382-152">Você precisa apenas raramente uma implementação de correspondência de padrão de curinga personalizados.</span><span class="sxs-lookup"><span data-stu-id="5d382-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="5d382-153">Nesse caso, seu cmdlet deve dar suporte a 1003.2 POSIX completa, especificação 3.13 para expansão de curinga ou o subconjunto simplificado a seguir:</span><span class="sxs-lookup"><span data-stu-id="5d382-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="5d382-154">**Ponto de interrogação (?).**</span><span class="sxs-lookup"><span data-stu-id="5d382-154">**Question mark (?).**</span></span> <span data-ttu-id="5d382-155">Corresponde a qualquer caractere no local especificado.</span><span class="sxs-lookup"><span data-stu-id="5d382-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="5d382-156">**Asterisco (\*).**</span><span class="sxs-lookup"><span data-stu-id="5d382-156">**Asterisk (\*).**</span></span> <span data-ttu-id="5d382-157">Corresponde a zero ou mais caracteres começando no local especificado.</span><span class="sxs-lookup"><span data-stu-id="5d382-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="5d382-158">**Colchete de abertura ([]).**</span><span class="sxs-lookup"><span data-stu-id="5d382-158">**Open bracket ([).**</span></span> <span data-ttu-id="5d382-159">Apresenta uma expressão entre colchetes padrão que pode conter caracteres ou um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5d382-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="5d382-160">Se um intervalo for necessário, um hífen (-) é usado para indicar o intervalo.</span><span class="sxs-lookup"><span data-stu-id="5d382-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="5d382-161">**Colchete de fechamento (]).**</span><span class="sxs-lookup"><span data-stu-id="5d382-161">**Close bracket (]).**</span></span> <span data-ttu-id="5d382-162">Termina uma expressão entre colchetes de padrão.</span><span class="sxs-lookup"><span data-stu-id="5d382-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="5d382-163">**Acento caractere de escape (').**</span><span class="sxs-lookup"><span data-stu-id="5d382-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="5d382-164">Indica que o próximo caractere deve ser interpretado literalmente.</span><span class="sxs-lookup"><span data-stu-id="5d382-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="5d382-165">Lembre-se de que ao especificar o caractere de acento da linha de comando (em vez de especificá-lo por meio de programação), o caractere de escape de acento deve ser especificado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="5d382-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="5d382-166">Para obter mais informações sobre padrões de curinga, consulte [que dão suporte a curingas nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5d382-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="5d382-167">O código a seguir mostra como definir opções de curinga e definir o padrão de curinga usado para resolver o `Name` parâmetro desse cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5d382-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="5d382-168">O código a seguir mostra como testar se o nome do processo corresponde ao padrão de curinga definido.</span><span class="sxs-lookup"><span data-stu-id="5d382-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="5d382-169">Observe que, nesse caso, se o nome do processo não coincide com o padrão, o cmdlet continua em obter o próximo nome de processo.</span><span class="sxs-lookup"><span data-stu-id="5d382-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="5d382-170">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5d382-170">Code Sample</span></span>

<span data-ttu-id="5d382-171">Para o completo C# exemplos de código, consulte [StopProcessSample03 amostra](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5d382-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="5d382-172">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="5d382-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="5d382-173">Windows PowerShell passa informações entre cmdlets usando objetos .net.</span><span class="sxs-lookup"><span data-stu-id="5d382-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="5d382-174">Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5d382-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="5d382-175">Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="5d382-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="5d382-176">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d382-176">Building the Cmdlet</span></span>

<span data-ttu-id="5d382-177">Depois de implementar um cmdlet, ele deve ser registrado com o Windows PowerShell por meio de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d382-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="5d382-178">Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="5d382-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="5d382-179">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d382-179">Testing the Cmdlet</span></span>

<span data-ttu-id="5d382-180">Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="5d382-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="5d382-181">Vamos testar o exemplo de cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="5d382-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="5d382-182">Para obter mais informações sobre como usar os cmdlets da linha de comando, consulte o [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="5d382-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="5d382-183">Inicie o Windows PowerShell e use Proc Stop para interromper um processo usando o alias ProcessName para o `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5d382-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="5d382-184">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="5d382-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="5d382-185">Verifique a entrada a seguir na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="5d382-185">Make the following entry on the command line.</span></span> <span data-ttu-id="5d382-186">Como o parâmetro de nome é obrigatório, você será solicitado para ele.</span><span class="sxs-lookup"><span data-stu-id="5d382-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="5d382-187">Inserir "!?"</span><span class="sxs-lookup"><span data-stu-id="5d382-187">Entering "!?"</span></span> <span data-ttu-id="5d382-188">Exibe o texto de ajuda associado ao parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5d382-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="5d382-189">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="5d382-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="5d382-190">Agora, verifique a seguinte entrada para interromper todos os processos que correspondem ao padrão de curinga "\* Observação\*".</span><span class="sxs-lookup"><span data-stu-id="5d382-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="5d382-191">Você será solicitado antes de parar a cada processo que corresponde ao padrão.</span><span class="sxs-lookup"><span data-stu-id="5d382-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="5d382-192">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="5d382-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="5d382-193">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="5d382-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="5d382-194">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="5d382-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="5d382-195">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5d382-195">See Also</span></span>

[<span data-ttu-id="5d382-196">Criar um Cmdlet que modifica o sistema</span><span class="sxs-lookup"><span data-stu-id="5d382-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="5d382-197">Como criar um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d382-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="5d382-198">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="5d382-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="5d382-199">Como registrar Cmdlets, provedores e aplicativos de Host</span><span class="sxs-lookup"><span data-stu-id="5d382-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="5d382-200">Suporte a curingas nos parâmetros do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d382-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="5d382-201">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5d382-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
