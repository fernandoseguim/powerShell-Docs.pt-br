---
title: "Usando classes e métodos estáticos"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 50ebc8a737b50aba5a5af49716b59905da74669a

---

# Usando classes e métodos estáticos
Nem todas as classes do .NET Framework podem ser criadas usando **New\-Object**. Por exemplo, se você tentar criar um objeto **System.Environment** ou um **System.Math** com **New\-Object**, você receberá as seguintes mensagens de erro:

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

Esses erros ocorrem porque não há nenhuma maneira de criar um novo objeto dessas classes. Essas classes são bibliotecas de referência de métodos e propriedades que não mudam de estado. Não é necessário criá-las, você simplesmente as usa. Classes e métodos como esses são chamados de *classes estáticas* porque não são criados, destruídos ou alterados. Para esclarecer esse ponto, forneceremos exemplos que usam classes estáticas.

### Obtendo dados de ambiente com o System.Environment
Normalmente, a primeira etapa ao trabalhar com um objeto no Windows PowerShell é usar Get\-Member para descobrir quais membros ele contém. Com classes estáticas, o processo é um pouco diferente porque a classe real não é um objeto.

#### Fazendo referência à classe estática System.Environment
Você pode fazer referência a uma classe estática envolvendo o nome de classe entre colchetes. Por exemplo, você pode fazer referência a **System.Environment** digitando o nome entre colchetes. Isso exibe algumas informações de tipo genérico:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Conforme mencionado anteriormente, o Windows PowerShell adiciona “**System.**” automaticamente no início de nomes de tipo quando você usa **New\-Object**. A mesma coisa acontece ao usar um nome de tipo entre colchetes, por isso você pode especificar **\[System.Environment]** como **\[Environment]**.

A classe **System. Environment** classe contém informações gerais sobre o ambiente de trabalho para o processo atual, que é powershell.exe ao trabalhar no Windows PowerShell.

Se você tentar exibir detalhes dessa classe digitando **\[System.Environment] | Get\-Member**, o tipo de objeto será relatado como **System.RuntimeType**, não **System.Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Para exibir membros estáticos com Get\-Member, especifique o parâmetro **Static**:

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

Agora podemos selecionar propriedades a serem exibidas de System.Environment.

#### Exibindo propriedades estáticas do System.Environment
As propriedades do System.Environment também são estáticas e devem ser especificadas de forma diferente que as propriedades normais. Usamos **::** para indicar ao Windows PowerShell que queremos trabalhar com uma propriedade ou método estático. Para ver o comando que foi usado para iniciar o Windows PowerShell, verificamos a propriedade **CommandLine** digitando:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Para verificar a versão do sistema operacional, exiba a propriedade OSVersion digitando:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Podemos verificar se o computador está no processo de desligamento exibindo a propriedade **HasShutdownStarted**:

```
PS> [System.Environment]::HasShutdownStarted
False
```

### Fazendo cálculos com o System.Math
A classe estática System.Math é útil para executar algumas operações matemáticas. Os membros importantes de **System.Math** são, em sua maioria, métodos, que podemos exibir usando **Get\-Member**.

> [!NOTE]
> O System.Math tem vários métodos com o mesmo nome, mas eles são diferenciados pelo tipo dos seus parâmetros.

Digite o comando a seguir para listar os métodos da classe **System.Math**.

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

Isso exibe vários métodos matemáticos. Aqui está uma lista de comandos que demonstram como alguns dos métodos comuns funcionam:

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




<!--HONumber=Jun16_HO4-->


