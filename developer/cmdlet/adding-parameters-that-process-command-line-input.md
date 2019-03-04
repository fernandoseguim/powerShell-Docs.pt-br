---
title: Adicionar parâmetros que processam a entrada de linha de comando | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: e010e28ec705932063bb418b260a1087fc3eef9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856002"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="2f255-102">Adicionar parâmetros que processam a entrada de linha de comando</span><span class="sxs-lookup"><span data-stu-id="2f255-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="2f255-103">Uma fonte de entrada para um cmdlet é a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="2f255-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="2f255-104">Este tópico descreve como adicionar um parâmetro para o **Get-Proc** cmdlet (que é descrito na [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)) para que o cmdlet pode processar a entrada do computador local com base em explícita os objetos passados para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f255-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="2f255-105">O **Get-Proc** cmdlet descrito aqui recupera processos com base em seus nomes e, em seguida, exibe informações sobre os processos em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2f255-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

<span data-ttu-id="2f255-106">As seções a seguir são neste tópico:</span><span class="sxs-lookup"><span data-stu-id="2f255-106">The following sections are in this topic:</span></span>

- [<span data-ttu-id="2f255-107">Definição da classe do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f255-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="2f255-108">Declarando parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f255-108">Declaring Parameters</span></span>](#Declaring-Parameters)

- [<span data-ttu-id="2f255-109">Suporte a validação de parâmetro</span><span class="sxs-lookup"><span data-stu-id="2f255-109">Supporting Parameter Validation</span></span>](#Supporting-Parameter-Validation)

- [<span data-ttu-id="2f255-110">Substituindo uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="2f255-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="2f255-111">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="2f255-111">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="2f255-112">Definindo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="2f255-112">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="2f255-113">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f255-113">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="2f255-114">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f255-114">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="2f255-115">Definição da classe do Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f255-115">Defining the Cmdlet Class</span></span>

<span data-ttu-id="2f255-116">A primeira etapa na criação de cmdlet é a nomeação do cmdlet e a declaração de classe do .NET Framework que implementa o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f255-116">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="2f255-117">Este cmdlet recupera informações de processo, portanto, o nome do verbo escolhido aqui é "Get".</span><span class="sxs-lookup"><span data-stu-id="2f255-117">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="2f255-118">(Quase qualquer tipo de cmdlet que é capaz de recuperar informações pode processar a entrada de linha de comando.) Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="2f255-118">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="2f255-119">Aqui está a declaração de classe para o **Get-Proc** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f255-119">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="2f255-120">Detalhes sobre essa definição são fornecidos [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="2f255-120">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="2f255-121">Declarando parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f255-121">Declaring Parameters</span></span>

<span data-ttu-id="2f255-122">Um parâmetro de cmdlet habilita o usuário fornecer entrada para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f255-122">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="2f255-123">No exemplo a seguir **Get-Proc** e `Get-Member` são os nomes dos cmdlets do pipeline, e `MemberType` é um parâmetro para o `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f255-123">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="2f255-124">O parâmetro tem o argumento "property".</span><span class="sxs-lookup"><span data-stu-id="2f255-124">The parameter has the argument "property."</span></span>

<span data-ttu-id="2f255-125">**PS > get-proc; `get-member` - membertype propriedade**</span><span class="sxs-lookup"><span data-stu-id="2f255-125">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="2f255-126">Para declarar parâmetros para um cmdlet, você deve primeiro definir as propriedades que representam os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2f255-126">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="2f255-127">No **Get-Proc** cmdlet, o único parâmetro é `Name`, nesse caso, que representa o nome do objeto de processo do .NET Framework para recuperar.</span><span class="sxs-lookup"><span data-stu-id="2f255-127">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="2f255-128">Portanto, a classe do cmdlet define uma propriedade do tipo cadeia de caracteres para aceitar uma matriz de nomes.</span><span class="sxs-lookup"><span data-stu-id="2f255-128">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="2f255-129">Aqui está a declaração de parâmetro para o `Name` parâmetro do **Get-Proc** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f255-129">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="2f255-130">Para informar o tempo de execução do Windows PowerShell que essa propriedade é o `Name` parâmetro, uma [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo é adicionado à definição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="2f255-130">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="2f255-131">A sintaxe básica para declarar esse atributo é `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="2f255-131">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="2f255-132">Um parâmetro deve ser explicitamente marcado como público.</span><span class="sxs-lookup"><span data-stu-id="2f255-132">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="2f255-133">Parâmetros que não são marcados como padrão público para interno e não são encontrados pelo runtime do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f255-133">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="2f255-134">Esse cmdlet usa uma matriz de cadeias de caracteres para o `Name` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2f255-134">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="2f255-135">Se possível, o cmdlet deve também definir um parâmetro como uma matriz, pois isso permite que o cmdlet a aceitar mais de um item.</span><span class="sxs-lookup"><span data-stu-id="2f255-135">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="2f255-136">Coisas a serem lembrados sobre definições de parâmetro</span><span class="sxs-lookup"><span data-stu-id="2f255-136">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="2f255-137">Predefinido do Windows PowerShell parâmetro nomes e tipos de dados devem ser reutilizados tanto quanto possível para garantir que seu cmdlet seja compatível com os cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f255-137">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="2f255-138">Por exemplo, se todos os cmdlets usam predefinido `Id` nome de parâmetro para identificar um recurso, o usuário não precisará facilmente entender o significado do parâmetro, independentemente de qual cmdlet que estão usando.</span><span class="sxs-lookup"><span data-stu-id="2f255-138">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="2f255-139">Basicamente, os nomes de parâmetro seguem as mesmas regras usadas para nomes de variáveis no common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2f255-139">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="2f255-140">Para obter mais informações sobre nomenclatura de parâmetro, consulte [nomes de parâmetro de Cmdlet](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="2f255-140">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="2f255-141">Windows PowerShell reserva alguns nomes de parâmetro para fornecer uma experiência de usuário consistente.</span><span class="sxs-lookup"><span data-stu-id="2f255-141">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="2f255-142">Não use esses nomes de parâmetro: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, e `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="2f255-142">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="2f255-143">Além disso, os seguintes aliases para esses nomes de parâmetro são reservados: `vb`, `db`, `ea`, `ev`, `ov`, e `ob`.</span><span class="sxs-lookup"><span data-stu-id="2f255-143">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="2f255-144">`Name` é um nome de parâmetro simples e comum, recomendado para uso em seus cmdlets.</span><span class="sxs-lookup"><span data-stu-id="2f255-144">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="2f255-145">É melhor escolher um nome de parâmetro assim que um nome complexo que é difícil lembrar e exclusivo para um cmdlet específico.</span><span class="sxs-lookup"><span data-stu-id="2f255-145">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="2f255-146">Parâmetros diferenciam maiusculas de minúsculas no Windows PowerShell, embora por padrão o shell preserva o caso.</span><span class="sxs-lookup"><span data-stu-id="2f255-146">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="2f255-147">Diferenciação de maiusculas e minúsculas dos argumentos depende da operação do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f255-147">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="2f255-148">Argumentos são passados para um parâmetro, conforme especificado na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="2f255-148">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="2f255-149">Para obter exemplos de outras declarações de parâmetro, consulte [parâmetros de Cmdlet](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="2f255-149">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="2f255-150">Declarando parâmetros como posicional ou nomeado</span><span class="sxs-lookup"><span data-stu-id="2f255-150">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="2f255-151">Um cmdlet deve definir cada parâmetro como um parâmetro posicional ou nomeado.</span><span class="sxs-lookup"><span data-stu-id="2f255-151">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="2f255-152">Os dois tipos de parâmetros aceitam argumentos únicos, vários argumentos separados por vírgulas e as configurações de Boolianas.</span><span class="sxs-lookup"><span data-stu-id="2f255-152">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="2f255-153">Um parâmetro booliano, também chamado de um *alternar*, manipula somente as configurações de Boolianas.</span><span class="sxs-lookup"><span data-stu-id="2f255-153">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="2f255-154">A opção é usada para determinar a presença do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2f255-154">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="2f255-155">O padrão recomendado é `false`.</span><span class="sxs-lookup"><span data-stu-id="2f255-155">The recommended default is `false`.</span></span>

<span data-ttu-id="2f255-156">O exemplo **Get-Proc** cmdlet define o `Name` parâmetro como um parâmetro posicional com posição 0.</span><span class="sxs-lookup"><span data-stu-id="2f255-156">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="2f255-157">Isso significa que o primeiro argumento que o usuário entra na linha de comando é inserido automaticamente para esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2f255-157">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="2f255-158">Se você quiser definir um parâmetro nomeado, o usuário deve especificar o nome do parâmetro de linha de comando, deixe o `Position` palavra-chave fora a declaração de atributo.</span><span class="sxs-lookup"><span data-stu-id="2f255-158">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="2f255-159">A menos que os parâmetros devem ser nomeados, recomendamos que você verifique os parâmetros usados com mais posicionais para que os usuários não precisarão digitar o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2f255-159">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="2f255-160">Declarando parâmetros como obrigatórios ou opcionais</span><span class="sxs-lookup"><span data-stu-id="2f255-160">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="2f255-161">Um cmdlet deve definir cada parâmetro como um parâmetro obrigatório ou opcional.</span><span class="sxs-lookup"><span data-stu-id="2f255-161">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="2f255-162">No exemplo **Get-Proc** cmdlet, o `Name` parâmetro é definido como opcional, porque o `Mandatory` palavra-chave não está definido na declaração de atributo.</span><span class="sxs-lookup"><span data-stu-id="2f255-162">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="2f255-163">Suporte a validação de parâmetro</span><span class="sxs-lookup"><span data-stu-id="2f255-163">Supporting Parameter Validation</span></span>

<span data-ttu-id="2f255-164">O exemplo **Get-Proc** cmdlet adiciona um atributo de validação de entrada, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), para o `Name` parâmetro para habilitar a validação que o entrada não é nem `null` nem vazio.</span><span class="sxs-lookup"><span data-stu-id="2f255-164">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="2f255-165">Esse atributo é um dos vários atributos de validação fornecidos pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f255-165">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="2f255-166">Para obter exemplos de outros atributos de validação, consulte [Validando a entrada do parâmetro](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="2f255-166">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="2f255-167">Substituindo uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="2f255-167">Overriding an Input Processing Method</span></span>

<span data-ttu-id="2f255-168">Se seu cmdlet é manipular a entrada de linha de comando, ele deve substituir os métodos de processamento de entrada apropriada.</span><span class="sxs-lookup"><span data-stu-id="2f255-168">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="2f255-169">Os métodos de processamento de entrada básico são introduzidos no [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="2f255-169">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="2f255-170">O **Get-Proc** cmdlet substitui o [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para manipular o `Name` entrada de parâmetro fornecida pelo usuário ou um script.</span><span class="sxs-lookup"><span data-stu-id="2f255-170">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="2f255-171">Esse método obtém os processos para cada nome de processo solicitado, ou todos os processos se nenhum nome for fornecido.</span><span class="sxs-lookup"><span data-stu-id="2f255-171">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="2f255-172">Observe que, na [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), a chamada para [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) é a saída objetos do mecanismo de envio de saída para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="2f255-172">Notice that in [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="2f255-173">O segundo parâmetro dessa chamada `enumerateCollection`, é definido como `true` para informar o tempo de execução do Windows PowerShell para enumerar a matriz de saída de objetos de processo e gravar um processo por vez à linha de comando.</span><span class="sxs-lookup"><span data-stu-id="2f255-173">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="2f255-174">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="2f255-174">Code Sample</span></span>

<span data-ttu-id="2f255-175">Para o completo C# exemplos de código, consulte [GetProcessSample02 exemplo](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2f255-175">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="2f255-176">Definindo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="2f255-176">Defining Object Types and Formatting</span></span>

<span data-ttu-id="2f255-177">Windows PowerShell passa informações entre cmdlets usando objetos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2f255-177">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="2f255-178">Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet ou um cmdlet, talvez seja necessário estender um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2f255-178">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="2f255-179">Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="2f255-179">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="2f255-180">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f255-180">Building the Cmdlet</span></span>

<span data-ttu-id="2f255-181">Depois de implementar um cmdlet, você deve registrá-lo com o Windows PowerShell usando um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f255-181">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="2f255-182">Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="2f255-182">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="2f255-183">Testando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f255-183">Testing the Cmdlet</span></span>

<span data-ttu-id="2f255-184">Quando seu cmdlet é registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="2f255-184">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="2f255-185">Aqui estão duas maneiras de testar o código para o cmdlet de exemplo.</span><span class="sxs-lookup"><span data-stu-id="2f255-185">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="2f255-186">Para obter mais informações sobre como usar os cmdlets da linha de comando, consulte [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="2f255-186">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="2f255-187">No prompt do Windows PowerShell, use o seguinte comando para listar o processo do Internet Explorer, que é chamado de "IEXPLORE."</span><span class="sxs-lookup"><span data-stu-id="2f255-187">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="2f255-188">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="2f255-188">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="2f255-189">Para listar os processos do Internet Explorer, Outlook e o bloco de notas, chamados "IEXPLORE", "OUTLOOK" e "NOTEPAD", usam o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="2f255-189">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="2f255-190">Se houver vários processos, todos eles são exibidos.</span><span class="sxs-lookup"><span data-stu-id="2f255-190">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="2f255-191">A seguinte saída é exibida.</span><span class="sxs-lookup"><span data-stu-id="2f255-191">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="2f255-192">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="2f255-192">See Also</span></span>

[<span data-ttu-id="2f255-193">Adicionar parâmetros de entrada do Pipeline de processo</span><span class="sxs-lookup"><span data-stu-id="2f255-193">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="2f255-194">Criando seu primeiro Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f255-194">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="2f255-195">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="2f255-195">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="2f255-196">Como registrar Cmdlets, provedores e aplicativos de Host</span><span class="sxs-lookup"><span data-stu-id="2f255-196">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="2f255-197">Referência do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f255-197">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="2f255-198">Exemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f255-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)
