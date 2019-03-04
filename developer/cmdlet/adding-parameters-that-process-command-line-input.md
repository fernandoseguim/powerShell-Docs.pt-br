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
# <a name="adding-parameters-that-process-command-line-input"></a>Adicionar parâmetros que processam a entrada de linha de comando

Uma fonte de entrada para um cmdlet é a linha de comando. Este tópico descreve como adicionar um parâmetro para o **Get-Proc** cmdlet (que é descrito na [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)) para que o cmdlet pode processar a entrada do computador local com base em explícita os objetos passados para o cmdlet. O **Get-Proc** cmdlet descrito aqui recupera processos com base em seus nomes e, em seguida, exibe informações sobre os processos em um prompt de comando.

As seções a seguir são neste tópico:

- [Definição da classe do Cmdlet](#Defining-the-Cmdlet-Class)

- [Declarando parâmetros](#Declaring-Parameters)

- [Suporte a validação de parâmetro](#Supporting-Parameter-Validation)

- [Substituindo uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Exemplo de código](#Code-Sample)

- [Definindo tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [Testando o Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Definição da classe do Cmdlet

A primeira etapa na criação de cmdlet é a nomeação do cmdlet e a declaração de classe do .NET Framework que implementa o cmdlet. Este cmdlet recupera informações de processo, portanto, o nome do verbo escolhido aqui é "Get". (Quase qualquer tipo de cmdlet que é capaz de recuperar informações pode processar a entrada de linha de comando.) Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Aqui está a declaração de classe para o **Get-Proc** cmdlet. Detalhes sobre essa definição são fornecidos [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Declarando parâmetros

Um parâmetro de cmdlet habilita o usuário fornecer entrada para o cmdlet. No exemplo a seguir **Get-Proc** e `Get-Member` são os nomes dos cmdlets do pipeline, e `MemberType` é um parâmetro para o `Get-Member` cmdlet. O parâmetro tem o argumento "property".

**PS > get-proc; `get-member` - membertype propriedade**

Para declarar parâmetros para um cmdlet, você deve primeiro definir as propriedades que representam os parâmetros. No **Get-Proc** cmdlet, o único parâmetro é `Name`, nesse caso, que representa o nome do objeto de processo do .NET Framework para recuperar. Portanto, a classe do cmdlet define uma propriedade do tipo cadeia de caracteres para aceitar uma matriz de nomes.

Aqui está a declaração de parâmetro para o `Name` parâmetro do **Get-Proc** cmdlet.

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

Para informar o tempo de execução do Windows PowerShell que essa propriedade é o `Name` parâmetro, uma [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo é adicionado à definição da propriedade. A sintaxe básica para declarar esse atributo é `[Parameter()]`.

> [!NOTE]
> Um parâmetro deve ser explicitamente marcado como público. Parâmetros que não são marcados como padrão público para interno e não são encontrados pelo runtime do Windows PowerShell.

Esse cmdlet usa uma matriz de cadeias de caracteres para o `Name` parâmetro. Se possível, o cmdlet deve também definir um parâmetro como uma matriz, pois isso permite que o cmdlet a aceitar mais de um item.

#### <a name="things-to-remember-about-parameter-definitions"></a>Coisas a serem lembrados sobre definições de parâmetro

- Predefinido do Windows PowerShell parâmetro nomes e tipos de dados devem ser reutilizados tanto quanto possível para garantir que seu cmdlet seja compatível com os cmdlets do Windows PowerShell. Por exemplo, se todos os cmdlets usam predefinido `Id` nome de parâmetro para identificar um recurso, o usuário não precisará facilmente entender o significado do parâmetro, independentemente de qual cmdlet que estão usando. Basicamente, os nomes de parâmetro seguem as mesmas regras usadas para nomes de variáveis no common language runtime (CLR). Para obter mais informações sobre nomenclatura de parâmetro, consulte [nomes de parâmetro de Cmdlet](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell reserva alguns nomes de parâmetro para fornecer uma experiência de usuário consistente. Não use esses nomes de parâmetro: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, e `OutBuffer`. Além disso, os seguintes aliases para esses nomes de parâmetro são reservados: `vb`, `db`, `ea`, `ev`, `ov`, e `ob`.

- `Name` é um nome de parâmetro simples e comum, recomendado para uso em seus cmdlets. É melhor escolher um nome de parâmetro assim que um nome complexo que é difícil lembrar e exclusivo para um cmdlet específico.

- Parâmetros diferenciam maiusculas de minúsculas no Windows PowerShell, embora por padrão o shell preserva o caso. Diferenciação de maiusculas e minúsculas dos argumentos depende da operação do cmdlet. Argumentos são passados para um parâmetro, conforme especificado na linha de comando.

- Para obter exemplos de outras declarações de parâmetro, consulte [parâmetros de Cmdlet](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Declarando parâmetros como posicional ou nomeado

Um cmdlet deve definir cada parâmetro como um parâmetro posicional ou nomeado. Os dois tipos de parâmetros aceitam argumentos únicos, vários argumentos separados por vírgulas e as configurações de Boolianas. Um parâmetro booliano, também chamado de um *alternar*, manipula somente as configurações de Boolianas. A opção é usada para determinar a presença do parâmetro. O padrão recomendado é `false`.

O exemplo **Get-Proc** cmdlet define o `Name` parâmetro como um parâmetro posicional com posição 0. Isso significa que o primeiro argumento que o usuário entra na linha de comando é inserido automaticamente para esse parâmetro. Se você quiser definir um parâmetro nomeado, o usuário deve especificar o nome do parâmetro de linha de comando, deixe o `Position` palavra-chave fora a declaração de atributo.

> [!NOTE]
> A menos que os parâmetros devem ser nomeados, recomendamos que você verifique os parâmetros usados com mais posicionais para que os usuários não precisarão digitar o nome do parâmetro.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Declarando parâmetros como obrigatórios ou opcionais

Um cmdlet deve definir cada parâmetro como um parâmetro obrigatório ou opcional. No exemplo **Get-Proc** cmdlet, o `Name` parâmetro é definido como opcional, porque o `Mandatory` palavra-chave não está definido na declaração de atributo.

## <a name="supporting-parameter-validation"></a>Suporte a validação de parâmetro

O exemplo **Get-Proc** cmdlet adiciona um atributo de validação de entrada, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), para o `Name` parâmetro para habilitar a validação que o entrada não é nem `null` nem vazio. Esse atributo é um dos vários atributos de validação fornecidos pelo Windows PowerShell. Para obter exemplos de outros atributos de validação, consulte [Validando a entrada do parâmetro](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Substituindo uma método de processamento de entrada

Se seu cmdlet é manipular a entrada de linha de comando, ele deve substituir os métodos de processamento de entrada apropriada. Os métodos de processamento de entrada básico são introduzidos no [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

O **Get-Proc** cmdlet substitui o [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para manipular o `Name` entrada de parâmetro fornecida pelo usuário ou um script. Esse método obtém os processos para cada nome de processo solicitado, ou todos os processos se nenhum nome for fornecido. Observe que, na [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), a chamada para [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) é a saída objetos do mecanismo de envio de saída para o pipeline. O segundo parâmetro dessa chamada `enumerateCollection`, é definido como `true` para informar o tempo de execução do Windows PowerShell para enumerar a matriz de saída de objetos de processo e gravar um processo por vez à linha de comando.

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

## <a name="code-sample"></a>Exemplo de código

Para o completo C# exemplos de código, consulte [GetProcessSample02 exemplo](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definindo tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets usando objetos do .NET Framework. Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet ou um cmdlet, talvez seja necessário estender um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, você deve registrá-lo com o Windows PowerShell usando um snap-in do Windows PowerShell. Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testando o Cmdlet

Quando seu cmdlet é registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando. Aqui estão duas maneiras de testar o código para o cmdlet de exemplo. Para obter mais informações sobre como usar os cmdlets da linha de comando, consulte [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- No prompt do Windows PowerShell, use o seguinte comando para listar o processo do Internet Explorer, que é chamado de "IEXPLORE."

    ```powershell
    PS> get-proc -name iexplore
    ```

A seguinte saída é exibida.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Para listar os processos do Internet Explorer, Outlook e o bloco de notas, chamados "IEXPLORE", "OUTLOOK" e "NOTEPAD", usam o comando a seguir. Se houver vários processos, todos eles são exibidos.

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

A seguinte saída é exibida.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>Consulte Também

[Adicionar parâmetros de entrada do Pipeline de processo](./adding-parameters-that-process-pipeline-input.md)

[Criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referência do Windows PowerShell](../windows-powershell-reference.md)

[Exemplos de cmdlet](./cmdlet-samples.md)
