---
title: Adicionar parâmetros que processam a entrada do Pipeline | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: c790d20a792bcdb4a34485e53375560e129433a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854532"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Adicionar parâmetros que processam a entrada de pipeline

Uma fonte de entrada para um cmdlet é um objeto no pipeline do que se origina de um cmdlet de upstream. Esta seção descreve como adicionar um parâmetro para o cmdlet Get-Proc (descrito na [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)) para que o cmdlet pode processar objetos do pipeline.

Esse cmdlet Get-Proc usa um `Name` parâmetro que aceita entrada de um objeto de pipeline, recupera informações de processo do computador local com base em nomes fornecidos e, em seguida, exibe informações sobre os processos na linha de comando.

Os tópicos nesta seção incluem o seguinte:

- [Definição da classe do Cmdlet](#Defining-the-Cmdlet-Class)

- [Definindo a entrada do Pipeline](#Defining-Input-from-the-Pipeline)

- [Substituindo uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Exemplo de código](#Code-Sample)

- [Definindo tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [Testando o Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Definição da classe do Cmdlet

A primeira etapa na criação de cmdlet sempre é o cmdlet de nomenclatura e declarar a classe .NET que implementa o cmdlet. Este cmdlet recupera informações de processo, portanto, o nome do verbo escolhido aqui é "Get". (Quase qualquer tipo de cmdlet que é capaz de recuperar informações pode processar a entrada de linha de comando.) Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

A seguir está a definição para esse cmdlet Get-Proc. Detalhes desta definição são fornecidos nas [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Definindo a entrada do Pipeline

Esta seção descreve como definir a entrada do pipeline para um cmdlet. Esse cmdlet Get-Proc define uma propriedade que representa o `Name` parâmetro, conforme descrito em [adicionando parâmetros essa entrada de linha de comando de processo](./adding-parameters-that-process-command-line-input.md). (Consulte o tópico para obter informações gerais sobre como declarar parâmetros).

No entanto, quando um cmdlet precisa processar a entrada do pipeline, ele deve ter seus parâmetros associados a valores de entrada no tempo de execução do Windows PowerShell. Para fazer isso, você deve adicionar o `ValueFromPipeline` palavra-chave ou adicionar a `ValueFromPipelineByProperty` palavra-chave para o [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaração do atributo. Especifique o `ValueFromPipeline` palavra-chave se o cmdlet acessa o objeto de entrada completo. Especifique o `ValueFromPipelineByProperty` se o cmdlet acessa apenas uma propriedade do objeto.

Aqui está a declaração de parâmetro para o `Name` parâmetro desse cmdlet Get-Proc que aceita entrada do pipeline.

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

Os conjuntos de declaração anterior a `ValueFromPipeline` palavra-chave para `true` para que o tempo de execução do Windows PowerShell irá associar o parâmetro para o objeto de entrada se o objeto é o mesmo tipo que o parâmetro ou se ele pode ser forçado para o mesmo tipo. O `ValueFromPipelineByPropertyName` palavra-chave também é definido como `true` para que o tempo de execução do Windows PowerShell verificará o objeto de entrada para um `Name` propriedade. Se o objeto de entrada tem essa propriedade, o tempo de execução será associado a `Name` parâmetro para o `Name` propriedade do objeto de entrada.

> [!NOTE]
> A configuração do `ValueFromPipeline` palavra-chave de atributo de um parâmetro tem precedência sobre a configuração para o `ValueFromPipelineByPropertyName` palavra-chave.

## <a name="overriding-an-input-processing-method"></a>Substituindo uma método de processamento de entrada

Se seu cmdlet é manipular a entrada do pipeline, ele precisa substituir os métodos de processamento de entrada apropriada. Os métodos de processamento de entrada básico são introduzidos no [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

Esse cmdlet Get-Proc substitui o [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para manipular o `Name` entrada de parâmetro fornecida pelo usuário ou um script. Esse método obtém os processos para cada nome de processo solicitado ou todos os processos se nenhum nome for fornecido. Observe que dentro [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), a chamada para [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) é o mecanismo de saída para enviar objetos de saída para o pipeline. O segundo parâmetro dessa chamada `enumerateCollection`, é definido como `true` para informar o tempo de execução do Windows PowerShell enumere a matriz de objetos de processo e gravar um processo por vez à linha de comando.

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
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Exemplo de código

Para o completo C# exemplos de código, consulte [GetProcessSample03 amostra](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definindo tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets usando objetos .net. Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet ele deve ser registrado com o Windows PowerShell por meio de um snap-in do Windows PowerShell. Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testando o Cmdlet

Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você deve testá-lo executando-o na linha de comando. Por exemplo, teste o código para o cmdlet de exemplo. Para obter mais informações sobre como usar os cmdlets da linha de comando, consulte o [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- No prompt do Windows PowerShell, digite os seguintes comandos para recuperar os nomes de processo por meio do pipeline.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

A seguinte saída é exibida.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- Insira as seguintes linhas para obter os objetos de processo que têm um `Name` propriedade dos processos chamado "IEXPLORE". Este exemplo usa o `Get-Process` cmdlet (fornecido pelo Windows PowerShell) como um comando upstream para recuperar os processos "IEXPLORE".

    ```powershell
    PS> get-process iexplore | get-proc
    ```

A seguinte saída é exibida.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>Consulte Também

[Adicionar parâmetros que processam a entrada de linha de comando](./adding-parameters-that-process-command-line-input.md)

[Criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referência do Windows PowerShell](../windows-powershell-reference.md)

[Exemplos de cmdlet](./cmdlet-samples.md)
