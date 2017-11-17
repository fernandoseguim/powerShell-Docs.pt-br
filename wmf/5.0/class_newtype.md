---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,instalação"
ms.openlocfilehash: c7318552969c44f3b79f82efd71e6a72bfabef6b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2017
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="33875-102">Novos recursos de linguagem no PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="33875-102">New language features in PowerShell 5.0</span></span> 

<span data-ttu-id="33875-103">O PowerShell 5.0 introduz os seguintes novos elementos de linguagem no Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="33875-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="33875-104">Palavra-chave class</span><span class="sxs-lookup"><span data-stu-id="33875-104">Class keyword</span></span>

<span data-ttu-id="33875-105">A palavra-chave **class** define uma nova classe.</span><span class="sxs-lookup"><span data-stu-id="33875-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="33875-106">Este é um tipo real do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="33875-106">This is a true .NET Framework type.</span></span> <span data-ttu-id="33875-107">Membros de classe são públicos, mas somente públicos dentro do escopo do módulo.</span><span class="sxs-lookup"><span data-stu-id="33875-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="33875-108">Não é possível se referir ao nome de tipo como uma cadeia de caracteres (por exemplo, `New-Object` não funciona), e nesta versão, não é possível usar um literal de tipo (por exemplo, `[MyClass]`) fora do arquivo de script/módulo no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="33875-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="33875-109">Palavra-chave Enum e enumerações</span><span class="sxs-lookup"><span data-stu-id="33875-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="33875-110">O suporte à palavra-chave **enum** for adicionado, que usa uma nova linha como o delimitador.</span><span class="sxs-lookup"><span data-stu-id="33875-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="33875-111">Limitações atuais: não é possível definir um enumerador em relação a si mesmo, mas é possível inicializar um enum em relação a outro enum, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="33875-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="33875-112">Além disso, atualmente, o tipo base não pode ser especificado; ele é sempre [int].</span><span class="sxs-lookup"><span data-stu-id="33875-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="33875-113">Um valor do enumerador deve ser uma constante de tempo de análise; não é possível defini-lo como o resultado de um comando invocado.</span><span class="sxs-lookup"><span data-stu-id="33875-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="33875-114">Enums dão suporte a operações aritméticas, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="33875-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="33875-115">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="33875-115">Import-DscResource</span></span>

<span data-ttu-id="33875-116">**Import-DscResource** agora é uma palavra-chave dinâmica real.</span><span class="sxs-lookup"><span data-stu-id="33875-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="33875-117">O PowerShell analisa o módulo raiz do módulo especificado, pesquisando classes que contêm o atributo **DscResource**.</span><span class="sxs-lookup"><span data-stu-id="33875-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="33875-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="33875-118">ImplementingAssembly</span></span>

<span data-ttu-id="33875-119">Um novo campo, **ImplementingAssembly**, foi adicionado a ModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="33875-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="33875-120">Ele é definido como o assembly dinâmico criado para um módulo de script, caso o script defina classes, ou como o assembly carregado para módulos binários.</span><span class="sxs-lookup"><span data-stu-id="33875-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="33875-121">Ele não é definido quando ModuleType = Manifest.</span><span class="sxs-lookup"><span data-stu-id="33875-121">It is not set when ModuleType = Manifest.</span></span> 

<span data-ttu-id="33875-122">A reflexão sobre o campo **ImplementingAssembly** descobre recursos em um módulo.</span><span class="sxs-lookup"><span data-stu-id="33875-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="33875-123">Isso significa que é possível descobrir recursos escritos no PowerShell ou em outras linguagens gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="33875-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="33875-124">Campos com inicializadores:</span><span class="sxs-lookup"><span data-stu-id="33875-124">Fields with initializers:</span></span>      

```powershell
[int] $i = 5
```

<span data-ttu-id="33875-125">Há suporte para static; ele funciona como um atributo, assim como as restrições de tipo; portanto, pode ser especificado em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="33875-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="33875-126">Um tipo é opcional.</span><span class="sxs-lookup"><span data-stu-id="33875-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="33875-127">Todos os membros são públicos.</span><span class="sxs-lookup"><span data-stu-id="33875-127">All members are public.</span></span> 

## <a name="constructors-and-instantiation"></a><span data-ttu-id="33875-128">Construtores e instanciação</span><span class="sxs-lookup"><span data-stu-id="33875-128">Constructors and instantiation</span></span>

<span data-ttu-id="33875-129">As classes do Windows PowerShell podem ter construtores; eles têm o mesmo nome que a classe.</span><span class="sxs-lookup"><span data-stu-id="33875-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="33875-130">Os construtores podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="33875-130">Constructors can be overloaded.</span></span> <span data-ttu-id="33875-131">Há suporte para construtores estáticos.</span><span class="sxs-lookup"><span data-stu-id="33875-131">Static constructors are supported.</span></span> <span data-ttu-id="33875-132">As propriedades com expressões de inicialização são inicializadas antes da execução de qualquer código em um construtor.</span><span class="sxs-lookup"><span data-stu-id="33875-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="33875-133">As propriedades estáticas são inicializadas antes do corpo de um construtor estático, e as propriedades de instância são inicializadas antes do corpo do construtor não estático.</span><span class="sxs-lookup"><span data-stu-id="33875-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="33875-134">Atualmente, não há nenhuma sintaxe para chamar um construtor de outro construtor [como a sintaxe do C\# ": this()"].</span><span class="sxs-lookup"><span data-stu-id="33875-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="33875-135">A solução alternativa é definir um método comum de Init.</span><span class="sxs-lookup"><span data-stu-id="33875-135">The workaround is to define a common Init method.</span></span> 

<span data-ttu-id="33875-136">Veja a seguir as maneiras de criar uma instância de classes nesta versão.</span><span class="sxs-lookup"><span data-stu-id="33875-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="33875-137">Criando uma instância usando o construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="33875-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="33875-138">Observe que não há suporte para New-Object nesta versão.</span><span class="sxs-lookup"><span data-stu-id="33875-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="33875-139">Chamando um construtor com um parâmetro</span><span class="sxs-lookup"><span data-stu-id="33875-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="33875-140">Passando uma matriz para um construtor com vários parâmetros</span><span class="sxs-lookup"><span data-stu-id="33875-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="33875-141">Nesta versão, New-Object não funciona com classes definidas no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33875-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="33875-142">Além disso, nesta versão, o nome de tipo é visível apenas lexicalmente, o que significa que ele não é visível fora do módulo ou do script que define a classe.</span><span class="sxs-lookup"><span data-stu-id="33875-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="33875-143">As funções podem retornar instâncias de uma classe definida no Windows PowerShell, e as instâncias funcionam bem fora do módulo ou do script.</span><span class="sxs-lookup"><span data-stu-id="33875-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="33875-144">`Get-Member -Static` lista os construtores, para que seja possível exibir sobrecargas como qualquer outro método.</span><span class="sxs-lookup"><span data-stu-id="33875-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="33875-145">O desempenho dessa sintaxe também é consideravelmente mais rápido do que o de New-Object.</span><span class="sxs-lookup"><span data-stu-id="33875-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="33875-146">O método pseudoestático chamado **new** funciona com tipos do .NET, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="33875-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="33875-147">Agora você pode ver as sobrecargas do construtor com Get-Member, ou conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="33875-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="33875-148">Métodos</span><span class="sxs-lookup"><span data-stu-id="33875-148">Methods</span></span>

<span data-ttu-id="33875-149">Um método de classe do Windows PowerShell é implementado como um ScriptBlock que tem apenas um end block.</span><span class="sxs-lookup"><span data-stu-id="33875-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="33875-150">Todos os métodos são públicos.</span><span class="sxs-lookup"><span data-stu-id="33875-150">All methods are public.</span></span> <span data-ttu-id="33875-151">Veja a seguir um exemplo de definição de um método chamado **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="33875-151">The following shows an example of defining a method named **DoSomething**.</span></span>

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

<span data-ttu-id="33875-152">Invocação de método:</span><span class="sxs-lookup"><span data-stu-id="33875-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42) 
```

<span data-ttu-id="33875-153">Também há suporte para métodos sobrecarregados – ou seja, aqueles que têm o mesmo nome que um método existente, mas que são diferenciados por seus valores especificados.</span><span class="sxs-lookup"><span data-stu-id="33875-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="33875-154">Propriedades</span><span class="sxs-lookup"><span data-stu-id="33875-154">Properties</span></span> 

<span data-ttu-id="33875-155">Todas as propriedades são públicas.</span><span class="sxs-lookup"><span data-stu-id="33875-155">All properties are public.</span></span> <span data-ttu-id="33875-156">As propriedades exigem uma nova linha ou um ponto-e-vírgula.</span><span class="sxs-lookup"><span data-stu-id="33875-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="33875-157">Se nenhum tipo de objeto for especificado, o tipo de propriedade será o objeto.</span><span class="sxs-lookup"><span data-stu-id="33875-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="33875-158">As propriedades que usam atributos de validação ou atributos de transformação de argumento (por exemplo, `[ValidateSet("aaa")]`) funcionam como esperado.</span><span class="sxs-lookup"><span data-stu-id="33875-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="33875-159">Hidden</span><span class="sxs-lookup"><span data-stu-id="33875-159">Hidden</span></span>

<span data-ttu-id="33875-160">Uma nova palavra-chave, **Hidden**, foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="33875-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="33875-161">**Hidden** pode ser aplicado a propriedades e métodos (incluindo construtores).</span><span class="sxs-lookup"><span data-stu-id="33875-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="33875-162">Membros ocultos são públicos, mas não aparecem na saída de Get-Member, a menos que o parâmetro -Force seja adicionado.</span><span class="sxs-lookup"><span data-stu-id="33875-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="33875-163">Membros ocultos não são incluídos durante o preenchimento de tabulação ou uso do IntelliSense, a menos que o preenchimento ocorra na classe que define o membro oculto.</span><span class="sxs-lookup"><span data-stu-id="33875-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="33875-164">Um novo atributo, **System.Management.Automation.HiddenAttribute**, foi adicionado, para que o código do C# possa ter a mesma semântica dentro do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33875-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="33875-165">Tipos de retorno</span><span class="sxs-lookup"><span data-stu-id="33875-165">Return types</span></span>

<span data-ttu-id="33875-166">O tipo de retorno é um contrato; o valor retornado é convertido para o tipo esperado.</span><span class="sxs-lookup"><span data-stu-id="33875-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="33875-167">Se nenhum tipo de retorno for especificado, o tipo de retorno será nulo.</span><span class="sxs-lookup"><span data-stu-id="33875-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="33875-168">Não há nenhum streaming de objetos; os objetos não podem ser gravados no pipeline, seja intencionalmente ou por engano.</span><span class="sxs-lookup"><span data-stu-id="33875-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="33875-169">Atributos</span><span class="sxs-lookup"><span data-stu-id="33875-169">Attributes</span></span>

<span data-ttu-id="33875-170">Dois novos atributos, **DscResource** e **DscProperty** foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="33875-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="33875-171">Escopo léxico de variáveis</span><span class="sxs-lookup"><span data-stu-id="33875-171">Lexical scoping of variables</span></span>

<span data-ttu-id="33875-172">Apresentamos a seguir um exemplo de como o escopo léxico funciona nesta versão.</span><span class="sxs-lookup"><span data-stu-id="33875-172">The following shows an example of how lexical scoping works in this release.</span></span>

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a><span data-ttu-id="33875-173">Exemplo de ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="33875-173">End-to-End Example</span></span>

<span data-ttu-id="33875-174">O exemplo a seguir cria várias classes novas e personalizadas para implementar uma DSL (linguagem de folha de estilos dinâmica) em HTML.</span><span class="sxs-lookup"><span data-stu-id="33875-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="33875-175">Em seguida, o exemplo adiciona funções auxiliares para criar tipos específicos de elementos como parte da classe de elemento, como estilos de título e tabelas, já que os tipos não podem ser usados fora do escopo de um módulo.</span><span class="sxs-lookup"><span data-stu-id="33875-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body
    
    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren’t visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$\_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```

