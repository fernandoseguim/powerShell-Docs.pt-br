# Declarar a classe base
É possível declarar uma classe do Windows PowerShell como um tipo base para outra classe do Windows PowerShell.

```PowerShell
class bar
{
   [int]foo() 
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

Também é possível usar os tipos existentes do .NET Framework como classes base:

```PowerShell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```<!--HONumber=Mar16_HO2-->
