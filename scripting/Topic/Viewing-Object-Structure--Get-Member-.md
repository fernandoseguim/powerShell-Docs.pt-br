---
title: Exibindo a estrutura do objeto (Get-Member)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
---
# Exibindo a estrutura do objeto (Get-Member)
Como objetos representam um papel central no Windows PowerShell, há vários comandos nativos projetados para trabalhar com tipos de objetos arbitrários. O mais importante é o comando **Get-Member**.

A técnica mais simples para analisar os objetos que retornam um comando é direcionar a saída desse comando para o cmdlet **Get-Member**. O cmdlet **Get-Member** mostra o nome formal do tipo de objeto e uma lista completa de seus membros. O número de elementos que são retornados, às vezes, pode ser imenso. Por exemplo, um objeto de processo pode ter mais de 100 membros.

Para ver todos os membros de um objeto e Process e paginar a saída para que você possa exibir tudo, digite:

```
PS> Get-Process | Get-Member | Out-Host -Paging
```

A saída deste comando será parecida com isto:

```
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

Podemos tornar essa longa lista de informações mais utilizável com filtragem dos elementos que você deseja ver. O comando **Get-Member** permite listar somente os membros que são propriedades de lista. Há várias formas de propriedades. O cmdlet exibirá as propriedades de qualquer tipo se definirmos o parâmetro **Get-MemberMemberType** para o valor **Properties**. A lista resultante ainda é muito longa, mas um pouco mais fácil de gerenciar:

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> Os valores permitidos para MemberType são AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet e All.

Há mais de 60 propriedades para um processo. O motivo que faz o Windows PowerShell geralmente mostrar apenas algumas propriedades para qualquer objeto conhecido é que mostrar todas elas produziria uma quantidade incontrolável de informações.

> [!NOTE]
> O Windows PowerShell determina como exibir um tipo de objeto usando informações armazenadas em arquivos XML que têm nomes que terminam com .format.ps1xml. Os dados de formatação para objetos de processo, que são objetos .NET System.Diagnostics.Process, são armazenados em PowerShellCore.format.ps1xml.

Se você precisar examinar propriedades diferentes que o Windows PowerShell exibe por padrão, deverá formatar os dados de saída por conta própria. Isso pode ser feito usando os cmdlets de formato.



<!--HONumber=Apr16_HO1-->


