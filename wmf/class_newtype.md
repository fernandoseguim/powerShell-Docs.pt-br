# Novos recursos de linguagem no PowerShell 5.0 

O PowerShell 5.0 introduz os seguintes novos elementos de linguagem no Windows PowerShell:

## Palavra-chave class

A palavra-chave **class** define uma nova classe. Este é um tipo real do .NET Framework. Membros de classe são públicos, mas somente públicos dentro do escopo do módulo.
Não é possível se referir ao nome de tipo como uma cadeia de caracteres (por exemplo, `New-Object` não funciona), e nesta versão, não é possível usar um literal de tipo (por exemplo, `[MyClass]`) fora do arquivo de script/módulo no qual a classe é definida.

```powershell
class MyClass
{
    ...
}
```

## Palavra-chave Enum e enumerações

O suporte à palavra-chave **enum** for adicionado, que usa uma nova linha como o delimitador.
Limitações atuais: não é possível definir um enumerador em relação a si mesmo, mas é possível inicializar um enum em relação a outro enum, conforme mostrado no exemplo a seguir.
Além disso, atualmente, o tipo base não pode ser especificado; ele é sempre [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Um valor do enumerador deve ser uma constante de tempo de análise; não é possível defini-lo como o resultado de um comando invocado.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Enums dão suporte a operações aritméticas, conforme mostrado no exemplo a seguir.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## Import-DscResource

**Import-DscResource** agora é uma palavra-chave dinâmica real.
O PowerShell analisa o módulo raiz do módulo especificado, pesquisando classes que contêm o atributo **DscResource**.

## ImplementingAssembly

Um novo campo, **ImplementingAssembly**, foi adicionado a ModuleInfo. Ele é definido como o assembly dinâmico criado para um módulo de script, caso o script defina classes, ou como o assembly carregado para módulos binários. Ele não é definido quando ModuleType = Manifest. 

A reflexão sobre o campo **ImplementingAssembly** descobre recursos em um módulo. Isso significa que é possível descobrir recursos escritos no PowerShell ou em outras linguagens gerenciadas.

Campos com inicializadores:      

```powershell
[int] $i = 5
```

Há suporte para static; ele funciona como um atributo, assim como as restrições de tipo; portanto, pode ser especificado em qualquer ordem.

```powershell
static [int] $count = 0
```

Um tipo é opcional.

```powershell
$s = "hello"
```

Todos os membros são públicos. 

## Construtores e instanciação

As classes do Windows PowerShell podem ter construtores; eles têm o mesmo nome que a classe. Os construtores podem ser sobrecarregados. Há suporte para construtores estáticos. As propriedades com expressões de inicialização são inicializadas antes da execução de qualquer código em um construtor. As propriedades estáticas são inicializadas antes do corpo de um construtor estático, e as propriedades de instância são inicializadas antes do corpo do construtor não estático. Atualmente, não há nenhuma sintaxe para chamar um construtor de outro construtor [como a sintaxe do C\# ": this()"]. A solução alternativa é definir um método comum de Init. 

Veja a seguir as maneiras de criar uma instância de classes nesta versão.

Criando uma instância usando o construtor padrão. Observe que não há suporte para New-Object nesta versão.

```powershell
$a = [MyClass]::new()
```

Chamando um construtor com um parâmetro

```powershell
$b = [MyClass]::new(42)
```

Passando uma matriz para um construtor com vários parâmetros
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

Nesta versão, New-Object não funciona com classes definidas no Windows PowerShell. Além disso, nesta versão, o nome de tipo é visível apenas lexicalmente, o que significa que ele não é visível fora do módulo ou do script que define a classe. As funções podem retornar instâncias de uma classe definida no Windows PowerShell, e as instâncias funcionam bem fora do módulo ou do script.

`Get-Member -Static` lista os construtores, para que você possa exibir sobrecargas como qualquer outro método. O desempenho dessa sintaxe também é consideravelmente mais rápido do que o de New-Object.

O método pseudoestático chamado **new** funciona com tipos do .NET, conforme mostrado no exemplo a seguir.

```powershell
[hashtable]::new()
```

Agora você pode ver as sobrecargas do construtor com Get-Member, ou conforme mostrado neste exemplo:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## Métodos

Um método de classe do Windows PowerShell é implementado como um ScriptBlock que tem apenas um end block. Todos os métodos são públicos. Veja a seguir um exemplo de definição de um método chamado **DoSomething**.

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

Invocação de método:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42) 
```

Também há suporte para métodos sobrecarregados – ou seja, aqueles que têm o mesmo nome que um método existente, mas que são diferenciados por seus valores especificados.

## Propriedades 

Todas as propriedades são públicas. As propriedades exigem uma nova linha ou um ponto-e-vírgula. Se nenhum tipo de objeto for especificado, o tipo de propriedade será o objeto.

As propriedades que usam atributos de validação ou atributos de transformação de argumento (por exemplo, `[ValidateSet("aaa")]`) funcionam como esperado.

## Hidden

Uma nova palavra-chave, **Hidden**, foi adicionada. **Hidden** pode ser aplicado a propriedades e métodos (incluindo construtores).

Membros ocultos são públicos, mas não aparecem na saída de Get-Member, a menos que o parâmetro -Force seja adicionado.

Membros ocultos não são incluídos durante o preenchimento de tabulação ou uso do IntelliSense, a menos que o preenchimento ocorra na classe que define o membro oculto.

Um novo atributo, **System.Management.Automation.HiddenAttribute**, foi adicionado, para que o código do C# possa ter a mesma semântica dentro do Windows PowerShell.

## Tipos de retorno

O tipo de retorno é um contrato; o valor retornado é convertido para o tipo esperado. Se nenhum tipo de retorno for especificado, o tipo de retorno será nulo. Não há nenhum streaming de objetos; os objetos não podem ser gravados no pipeline, seja intencionalmente ou por engano.

## Atributos

Dois novos atributos, **DscResource** e **DscProperty** foram adicionados.

## Escopo léxico de variáveis

Apresentamos a seguir um exemplo de como o escopo léxico funciona nesta versão.

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

## Exemplo de ponta a ponta

O exemplo a seguir cria várias classes novas e personalizadas para implementar uma DSL (linguagem de folha de estilos dinâmica) em HTML. Em seguida, o exemplo adiciona funções auxiliares para criar tipos específicos de elementos como parte da classe de elemento, como estilos de título e tabelas, já que os tipos não podem ser usados fora do escopo de um módulo.

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

<!--HONumber=Jun16_HO4-->


