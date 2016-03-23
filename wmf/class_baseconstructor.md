# Chamar o construtor de classe base

Para chamar um construtor de classe base desde uma subclasse, use a palavra-chave **base**:

```PowerShell
class A 
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

Se uma classe base tiver um construtor padrão (sem parâmetros), será possível omitir uma chamada explícita de construtor:

```PowerShell
class C : B
{
    C([int]$c) {}
}
```<!--HONumber=Mar16_HO2-->
