---
title: Adicionando relatórios de erros ao seu Cmdlet não fatal | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 2f3bb481722363557c93ebbc5e6df62baeff2555
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862002"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Adicionar relatórios de erros de não encerramento ao seu cmdlet

Cmdlets podem relatar erros sem encerramento chamando o [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método e ainda continuar a operar no objeto de entrada atual ou em entrada mais objetos do pipeline. Esta seção explica como criar um cmdlet que relata erros sem encerramento de seus métodos de processamento de entrada.

Para erros de não encerramento (bem como erros de encerramento), o cmdlet deve passar uma [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto identifica o erro. Cada registro de erro é identificado por uma cadeia de caracteres exclusiva, chamada "identificador de erro". Além do identificador, a categoria de cada erro é especificada pelo constantes definidas por um [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeração. O usuário pode exibir os erros com base em sua categoria, definindo o `$ErrorView` variável para "CategoryView".

Para obter mais informações sobre os registros de erro, consulte [registros de erros do Windows PowerShell](./windows-powershell-error-records.md).

Os tópicos nesta seção incluem o seguinte:

- [Definindo o Cmdlet](#Defining-the-Cmdlet)

- [Definindo parâmetros](#Defining-Parameters)

- [Substituindo métodos de processamento de entrada](#Overriding-Input-Processing-Methods)

- [Relatando erros sem encerramento](#Reporting-Nonterminating-Errors)

- [Exemplo de código](#Code-Sample)

- [Definindo tipos de objeto e formatação](#Define-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [Testando o Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definindo o Cmdlet

A primeira etapa na criação de cmdlet sempre é o cmdlet de nomenclatura e declarar a classe .NET que implementa o cmdlet. Este cmdlet recupera informações de processo, portanto, o nome do verbo escolhido aqui é "Get". (Quase qualquer tipo de cmdlet que é capaz de recuperar informações pode processar a entrada de linha de comando.) Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

A seguir está a definição para esse cmdlet Get-Proc. Detalhes desta definição são fornecidos nas [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Definindo parâmetros

Se necessário, o cmdlet deve definir parâmetros para o processamento de entrada. Esse cmdlet Get-Proc define uma `Name` parâmetro, conforme descrito em [adicionando parâmetros essa entrada de linha de comando de processo](./adding-parameters-that-process-command-line-input.md).

Aqui está a declaração de parâmetro para o `Name` parâmetro desse cmdlet Get-Proc.

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

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

## <a name="overriding-input-processing-methods"></a>Substituindo métodos de processamento de entrada

Todos os cmdlets devem substituir pelo menos uma entrada de processamento métodos fornecidos pelo [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Esses métodos são discutidos [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> O cmdlet deve tratar cada registro independentemente do quanto possível.

Esse cmdlet Get-Proc substitui o [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para lidar com o `Name` parâmetro de entrada fornecida pelo usuário ou um script. Esse método obtém os processos para cada nome de processo solicitado ou todos os processos se nenhum nome for fornecido. Detalhes dessa substituição são fornecidos nas [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md).

#### <a name="things-to-remember-when-reporting-errors"></a>Itens a lembrar ao relatar erros

O [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) do objeto que o cmdlet transmite ao escrever um erro requer uma exceção em seu núcleo. Siga as diretrizes do .NET ao determinar a exceção a usar. Basicamente, se o erro semanticamente é o mesmo que uma exceção existente, o cmdlet deve usar ou derivar dessa exceção. Caso contrário, ele deve derivar uma nova exceção ou hierarquia de exceções diretamente a partir de [System. Exception](/dotnet/api/System.Exception) classe.

Durante a criação de identificadores de erro (acessados por meio da propriedade da classe ErrorRecord FullyQualifiedErrorId) tenha em mente o seguinte.

- Usar cadeias de caracteres que são direcionadas para fins de diagnóstico para que, ao inspecionar o identificador totalmente qualificado, você pode determinar que o erro é e onde o erro veio de.

- Um identificador de erro bem formado de totalmente qualificado pode ser da seguinte maneira.

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

Observe que no exemplo anterior, o identificador de erro (o primeiro token) que designa qual é o erro e a parte restante indica de onde veio o erro.

- Para cenários mais complexos, o identificador de erro pode ser um token de ponto separado que pode ser analisado na inspeção. Isso permite que você ramificar muito nas partes do identificador de erro, bem como a categoria de erro e o identificador de erro.

O cmdlet deve atribuir os identificadores de erro específicas para diferentes caminhos de código. Lembre-se as informações a seguir para a atribuição de identificadores de erro:

- Um identificador de erro deve permanecer constante ao longo do ciclo de vida do cmdlet. Não altere a semântica de um identificador de erro entre as versões do cmdlet.

- Use o texto de um identificador de erro tersely corresponde ao erro que está sendo relatado. Não use espaço em branco ou pontuação.

- Ter seu cmdlet gerar somente os identificadores de erro que podem ser reproduzidos. Por exemplo, ele não deve gerar um identificador que inclui um identificador de processo. Identificadores de erro são úteis para um usuário somente quando eles correspondem aos identificadores que são vistos por outros usuários tiver o mesmo problema.

Exceções não tratadas não são detectadas pelo Windows PowerShell nas seguintes condições:

- Se um cmdlet cria um novo thread e o código que executa o thread gerará uma exceção sem tratamento, o Windows PowerShell não irá capturar o erro e encerrará o processo.

- Se um objeto tiver um código em seu destruidor ou métodos Dispose que faz com que uma exceção sem tratamento, o Windows PowerShell não irá capturar o erro e encerrará o processo.

## <a name="reporting-nonterminating-errors"></a>Relatando erros sem encerramento

Qualquer um dos métodos de processamento de entrada pode relatar um erro sem encerramento no fluxo de saída usando o [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método. Aqui está um exemplo de código desse cmdlet Get-Proc que ilustra a chamada para [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) de dentro a substituição do [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método. Nesse caso, a chamada será feita se o cmdlet não é possível localizar um processo para um identificador de processo especificado.

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Itens a lembrar sobre a escrita de erros sem encerramento

Para um erro sem encerramento, o cmdlet deve gerar um identificador de erro específico para cada objeto de entrada específico.

Um cmdlet com frequência precisa modificar a ação do Windows PowerShell produzida por um erro sem encerramento. Ele pode fazer isso definindo a `ErrorAction` e `ErrorVariable` parâmetros. Se definir a `ErrorAction` parâmetro, o cmdlet apresenta as opções de usuário [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), você também posso influenciar diretamente a ação, definindo o `$ErrorActionPreference` variável.

O cmdlet pode salvar erros sem encerramento em uma variável usando o `ErrorVariable` parâmetro, que não é afetado pela configuração da `ErrorAction`. Falhas podem ser anexadas a uma variável de erro existente adicionando um sinal de adição (+) na frente do nome da variável.

## <a name="code-sample"></a>Exemplo de código

Para o completo C# exemplos de código, consulte [GetProcessSample04 amostra](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets usando objetos .NET. Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet, ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, você deve registrá-lo com o Windows PowerShell por meio de um snap-in do Windows PowerShell. Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testando o Cmdlet

Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando. Vamos testar o cmdlet Get-Proc de exemplo para ver se ele relata um erro:

- Inicie o Windows PowerShell e use o cmdlet Get-Proc para recuperar os processos denominados "Teste".

    ```powershell
    PS> get-proc -name test
    ```

A seguinte saída é exibida.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>Consulte Também

[Adicionar parâmetros de entrada do Pipeline de processo](./adding-parameters-that-process-pipeline-input.md)

[Adicionar parâmetros que processam a entrada de linha de comando](./adding-parameters-that-process-command-line-input.md)

[Criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Referência do Windows PowerShell](../windows-powershell-reference.md)

[Exemplos de cmdlet](./cmdlet-samples.md)
