---
ms.date: 2017-06-05
keywords: PowerShell, cmdlet
title: "Usando classes e métodos estáticos"
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: fe41c7d6b45564e7b5bc2b922a18587c9745e26d
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2017
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="7e179-103">Usando classes e métodos estáticos</span><span class="sxs-lookup"><span data-stu-id="7e179-103">Using Static Classes and Methods</span></span>
<span data-ttu-id="7e179-104">Nem todas as classes do .NET Framework podem ser criadas usando **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="7e179-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="7e179-105">Por exemplo, se você tentar criar um objeto **System.Environment** ou **System.Math** com **New-Object**, as mensagens de erro a seguir poderão ser exibidas:</span><span class="sxs-lookup"><span data-stu-id="7e179-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment
PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

<span data-ttu-id="7e179-106">Esses erros ocorrem porque não há nenhuma maneira de criar um novo objeto dessas classes.</span><span class="sxs-lookup"><span data-stu-id="7e179-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="7e179-107">Essas classes são bibliotecas de referência de métodos e propriedades que não mudam de estado.</span><span class="sxs-lookup"><span data-stu-id="7e179-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="7e179-108">Não é necessário criá-las, você simplesmente as usa.</span><span class="sxs-lookup"><span data-stu-id="7e179-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="7e179-109">Classes e métodos como esses são chamados de *classes estáticas* porque não são criados, destruídos ou alterados.</span><span class="sxs-lookup"><span data-stu-id="7e179-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="7e179-110">Para esclarecer esse ponto, forneceremos exemplos que usam classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="7e179-110">To make this clear we will provide examples that use static classes.</span></span>

### <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="7e179-111">Obtendo dados de ambiente com o System.Environment</span><span class="sxs-lookup"><span data-stu-id="7e179-111">Getting Environment Data with System.Environment</span></span>
<span data-ttu-id="7e179-112">Normalmente, a primeira etapa ao trabalhar com um objeto no Windows PowerShell é usar Get-Member para descobrir quais membros ele contém.</span><span class="sxs-lookup"><span data-stu-id="7e179-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="7e179-113">Com classes estáticas, o processo é um pouco diferente porque a classe real não é um objeto.</span><span class="sxs-lookup"><span data-stu-id="7e179-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

#### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="7e179-114">Fazendo referência à classe estática System.Environment</span><span class="sxs-lookup"><span data-stu-id="7e179-114">Referring to the Static System.Environment Class</span></span>
<span data-ttu-id="7e179-115">Você pode fazer referência a uma classe estática envolvendo o nome de classe entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="7e179-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="7e179-116">Por exemplo, você pode fazer referência a **System.Environment** digitando o nome entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="7e179-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="7e179-117">Isso exibe algumas informações de tipo genérico:</span><span class="sxs-lookup"><span data-stu-id="7e179-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="7e179-118">Conforme mencionado anteriormente, o Windows PowerShell adiciona “**System.**” automaticamente no início</span><span class="sxs-lookup"><span data-stu-id="7e179-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="7e179-119">de nomes de tipo quando você usa **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="7e179-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="7e179-120">A mesma coisa acontece ao usar um nome de tipo entre colchetes, por isso você pode especificar **\[System.Environment]** como **\[Environment]**.</span><span class="sxs-lookup"><span data-stu-id="7e179-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="7e179-121">A classe **System. Environment** classe contém informações gerais sobre o ambiente de trabalho para o processo atual, que é powershell.exe ao trabalhar no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e179-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="7e179-122">Se você tentar exibir detalhes dessa classe digitando **\[System.Environment] | Get-Member**, o tipo de objeto será relatado como **System.RuntimeType**, não **System.Environment**:</span><span class="sxs-lookup"><span data-stu-id="7e179-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="7e179-123">Para exibir membros estáticos com Get-Member, especifique o parâmetro **Static**:</span><span class="sxs-lookup"><span data-stu-id="7e179-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

<span data-ttu-id="7e179-124">Agora podemos selecionar propriedades a serem exibidas de System.Environment.</span><span class="sxs-lookup"><span data-stu-id="7e179-124">We can now select properties to view from System.Environment.</span></span>

#### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="7e179-125">Exibindo propriedades estáticas do System.Environment</span><span class="sxs-lookup"><span data-stu-id="7e179-125">Displaying Static Properties of System.Environment</span></span>
<span data-ttu-id="7e179-126">As propriedades do System.Environment também são estáticas e devem ser especificadas de forma diferente que as propriedades normais.</span><span class="sxs-lookup"><span data-stu-id="7e179-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="7e179-127">Usamos **::** para indicar ao Windows PowerShell que queremos trabalhar com uma propriedade ou método estático.</span><span class="sxs-lookup"><span data-stu-id="7e179-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="7e179-128">Para ver o comando que foi usado para iniciar o Windows PowerShell, verificamos a propriedade **CommandLine** digitando:</span><span class="sxs-lookup"><span data-stu-id="7e179-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="7e179-129">Para verificar a versão do sistema operacional, exiba a propriedade OSVersion digitando:</span><span class="sxs-lookup"><span data-stu-id="7e179-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="7e179-130">Podemos verificar se o computador está no processo de desligamento exibindo a propriedade **HasShutdownStarted**:</span><span class="sxs-lookup"><span data-stu-id="7e179-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a><span data-ttu-id="7e179-131">Fazendo cálculos com o System.Math</span><span class="sxs-lookup"><span data-stu-id="7e179-131">Doing Math with System.Math</span></span>
<span data-ttu-id="7e179-132">A classe estática System.Math é útil para executar algumas operações matemáticas.</span><span class="sxs-lookup"><span data-stu-id="7e179-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="7e179-133">Os membros importantes do **System.Math** são em sua maioria métodos, que podemos exibir usando **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="7e179-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="7e179-134">O System.Math tem vários métodos com o mesmo nome, mas eles são diferenciados pelo tipo dos seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7e179-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="7e179-135">Digite o comando a seguir para listar os métodos da classe **System.Math**.</span><span class="sxs-lookup"><span data-stu-id="7e179-135">Type the following command to list the methods of the **System.Math** class.</span></span>

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

<span data-ttu-id="7e179-136">Isso exibe vários métodos matemáticos.</span><span class="sxs-lookup"><span data-stu-id="7e179-136">This displays several mathematical methods.</span></span> <span data-ttu-id="7e179-137">Aqui está uma lista de comandos que demonstram como alguns dos métodos comuns funcionam:</span><span class="sxs-lookup"><span data-stu-id="7e179-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```

