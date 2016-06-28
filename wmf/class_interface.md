# Declarar a interface implementada

Será possível declarar interfaces implementadas após tipos base, ou imediatamente após dois-pontos (:), se não houver nenhum tipo base especificado. Separe todos os nomes de tipo usando vírgulas. Isso é muito semelhante à sintaxe do C#.

```PowerShell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

<!--HONumber=Jun16_HO4-->


