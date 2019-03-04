---
title: Adicionando o parâmetro define como um Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: b02a2e0d4b0a27c261b0bc05febda7826ad5276e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859262"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Adicionar conjuntos de parâmetros como um cmdlet

Esta seção descreve como adicionar conjuntos de parâmetro para o cmdlet Stop-Proc (descrito na [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)). Semelhante a outros cmdlets Stop-Proc descritos no guia do programador deste, esse cmdlet tenta interromper os processos que são recuperados usando o cmdlet Get-Proc (descrito na [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Os tópicos nesta seção incluem o seguinte:

- [É importante saber sobre conjuntos de parâmetros](#Adding-Parameter-Sets-to-a-Cmdlet)

- [Declarar a classe do Cmdlet](#Declaring-the-Cmdlet-Class)

- [Declarar os parâmetros do Cmdlet](#Declaring-the-Parameters-of-the-Cmdlet)

- [Substituindo uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Exemplo de código](#Declaring-the-Parameters-of-the-Cmdlet)

- [Definindo tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [Testando o Cmdlet](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a>É importante saber sobre conjuntos de parâmetros

Windows PowerShell define um parâmetro definido como um grupo de parâmetros que funcionam em conjunto. Agrupando os parâmetros de um cmdlet, você pode criar um único cmdlet que pode alterar sua funcionalidade com base em qual grupo de parâmetros que o usuário especifica.

Um exemplo de um cmdlet que usa dois conjuntos de parâmetros para definir diferentes funcionalidades é a `Get-EventLog` cmdlet que é fornecida pelo Windows PowerShell. Esse cmdlet retorna informações distintas quando o usuário Especifica o `List` ou `LogName` parâmetro. Se o `LogName` parâmetro for especificado, o cmdlet retorna informações sobre os eventos em determinado log de eventos. Se o `List` parâmetro for especificado, o cmdlet retorna informações sobre o log de arquivos em si (não as informações de evento contêm). Nesse caso, o `List` e `LogName` parâmetros identificam dois conjuntos de parâmetros separado.

Dois aspectos importantes a serem lembrados sobre conjuntos de parâmetros é que o tempo de execução do Windows PowerShell usa apenas um conjunto de parâmetros para uma entrada específica e que cada conjunto de parâmetros deve ter pelo menos um parâmetro que é exclusivo para esse conjunto de parâmetros.

Para ilustrar esse último ponto, esse cmdlet Stop-Proc usa três conjuntos de parâmetros: `ProcessName`, `ProcessId`, e `InputObject`. Cada um desses conjuntos de parâmetro tem um parâmetro que não está nos conjuntos de parâmetro. Os conjuntos de parâmetros podem compartilhar outros parâmetros, mas o cmdlet usa os parâmetros exclusivos `ProcessName`, `ProcessId`, e `InputObject` para identificar qual conjunto de parâmetros que o tempo de execução do Windows PowerShell deve usar.

## <a name="declaring-the-cmdlet-class"></a>Declarar a classe do Cmdlet

A primeira etapa na criação de cmdlet sempre é o cmdlet de nomenclatura e declarar a classe .NET que implementa o cmdlet. Para esse cmdlet, o verbo de ciclo de vida "Stop" é usado porque o cmdlet interrompe os processos do sistema. O nome de substantivo "Proc" é usado como o cmdlet funciona em processos. Na declaração a seguir, observe que o nome do verbo e substantivo do cmdlet são refletidas no nome de classe do cmdlet.

> [!NOTE]
> Para obter mais informações sobre nomes de verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

O código a seguir é a definição de classe para esse cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Declarar os parâmetros do Cmdlet

Esse cmdlet define três parâmetros necessários como entrada para o cmdlet (esses parâmetros também definem os conjuntos de parâmetros), bem como uma `Force` parâmetro que gerencia o cmdlet faz e um `PassThru` parâmetro que determina se o cmdlet envia um objeto de saída por meio do pipeline. Por padrão, esse cmdlet não passar um objeto por meio do pipeline. Para obter mais informações sobre esses dois últimos parâmetros, consulte [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Declarar o parâmetro de nome

Esse parâmetro de entrada permite que o usuário especificar os nomes dos processos a serem interrompidos. Observe que o `ParameterSetName` atributo a palavra-chave do [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica a `ProcessName` parâmetro definido para esse parâmetro.

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

Observe também que o alias "ProcessName" é fornecido para esse parâmetro.

### <a name="declaring-the-id-parameter"></a>Declarar o parâmetro de Id

Esse parâmetro de entrada permite que o usuário especificar os identificadores dos processos a serem interrompidos. Observe que o `ParameterSetName` atributo a palavra-chave do [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica a `ProcessId` conjunto de parâmetros.

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

Observe também que o alias "ProcessId" é fornecido para esse parâmetro.

### <a name="declaring-the-inputobject-parameter"></a>Declarar o parâmetro InputObject

Esse parâmetro de entrada permite que o usuário especifique um objeto de entrada que contém informações sobre os processos sejam interrompidos. Observe que o `ParameterSetName` atributo a palavra-chave do [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) atributo especifica a `InputObject` parâmetro definido para esse parâmetro.

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

Observe também que esse parâmetro não tem alias.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Declarando parâmetros em vários conjuntos de parâmetros

Embora deva haver um parâmetro exclusivo para cada conjunto de parâmetros, os parâmetros podem pertencer a mais de um conjunto de parâmetros. Nesses casos, o parâmetro compartilhado dar a um [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração de atributo para cada conjunto ao qual o parâmetro pertence. Se for um parâmetro em todos os conjuntos de parâmetro, você só precisa declarar o atributo de parâmetro de uma vez e não é necessário especificar que o parâmetro de nome de conjunto.

## <a name="overriding-an-input-processing-method"></a>Substituindo uma método de processamento de entrada

Cada cmdlet deve substituir uma método de processamento de entrada, geralmente essa será a [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método. Esse cmdlet, o [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método é substituído para que o cmdlet pode processar qualquer número de processos. Ele contém uma instrução Select que chama um método diferente com base em qual conjunto de parâmetros, o usuário especificado.

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

Os métodos auxiliares chamados pela instrução Select não são descritos aqui, mas você pode ver sua implementação no exemplo de código completo na próxima seção.

## <a name="code-sample"></a>Exemplo de código

Para o completo C# exemplos de código, consulte [StopProcessSample04 amostra](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definindo tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets usando objetos .NET. Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet, ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, você deve registrá-lo com o Windows PowerShell por meio de um snap-in do Windows PowerShell. Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testando o Cmdlet

Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você deve testá-lo executando-o na linha de comando. Aqui estão alguns testes que mostram como o `ProcessId` e `InputObject` parâmetros podem ser usados para testar seus conjuntos de parâmetros para interromper um processo.

- Com o Windows PowerShell de iniciado, execute o cmdlet Stop-Proc com o `ProcessId` parâmetro definido para interromper um processo com base em seu identificador. Nesse caso, o cmdlet está usando o `ProcessId` parâmetro definido para interromper o processo.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Com o Windows PowerShell de iniciado, execute o cmdlet Stop-Proc com o `InputObject` parâmetro definido como para parar os processos no objeto de bloco de notas recuperado pelo `Get-Process` comando.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Consulte Também

[Criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Como criar um Cmdlet do Windows PowerShell](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
