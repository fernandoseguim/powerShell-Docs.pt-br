---
title: Adicionar mensagens de usuário ao seu Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: ffc08d2713c4bfc0938b2e07146102af8b5467d2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855982"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Adicionar mensagens de usuário para o cmdlet

Cmdlets pode gravar vários tipos de mensagens que podem ser exibidos ao usuário no tempo de execução do Windows PowerShell. Essas mensagens incluem os seguintes tipos:

- Mensagens detalhadas que contêm informações gerais de usuário.

- Mensagens que contêm informações de solução de problemas de depuração.

- Mensagens de aviso que contêm uma notificação de que o cmdlet está prestes a realizar uma operação que pode ter resultados inesperados.

- Relatório de progresso, mensagens que contêm informações sobre a quantidade funcionar o cmdlet foi concluída ao executar uma operação que demora muito tempo.

Não há nenhum limite para o número de mensagens que seu cmdlet pode gravar ou o tipo de mensagens que grava seu cmdlet. Cada mensagem é gravada, fazendo uma chamada específica de dentro da método do seu cmdlet de processamento de entrada.

## <a name="the-stopproc-cmdlet"></a>O StopProc Cmdlet

Os tópicos nesta seção incluem o seguinte:

- [Definindo o Cmdlet](#Defining-the-Cmdlet)

- [Definir parâmetros para modificação do sistema](#Defining-Parameters-for-System-Modification)

- [Substituindo uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Gravar uma mensagem detalhada](#Writing-a-Verbose-Message)

- [Gravar uma mensagem de depuração](#Writing-a-Debug-Message)

- [Gravar uma mensagem de aviso](#Writing-a-Warning-Message)

- [Gravar uma mensagem de progresso](#Writing-a-Progress-Message)

- [Exemplo de código](#Code-Sample)

- [Definir tipos de objeto e formatação](#Define-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [Testando o Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definindo o Cmdlet

A primeira etapa na criação de cmdlet sempre é o cmdlet de nomenclatura e declarar a classe .NET que implementa o cmdlet. Qualquer tipo de cmdlet pode gravar as notificações do usuário de seu métodos; de processamento de entrada em geral, você pode nomear este cmdlet usando qualquer verbo que indica quais modificações no sistema que executa o cmdlet. Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

O cmdlet Stop-Proc foi projetado para modificar o sistema; Portanto, o [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaração para a classe do .NET deve incluir o `SupportsShouldProcess` palavra-chave de atributo e definido como `true`.

O código a seguir é a definição para essa classe do cmdlet Stop-Proc. Para obter mais informações sobre essa definição, consulte [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definir parâmetros para modificação do sistema

O cmdlet Stop-Proc define três parâmetros: `Name`, `Force`, e `PassThru`. Para obter mais informações sobre como definir esses parâmetros, consulte [criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

Aqui está a declaração de parâmetro para o cmdlet Stop-Proc.

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a>Substituindo uma método de processamento de entrada

O cmdlet deve substituir uma método de processamento de entrada, geralmente será [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Esse cmdlet Stop-Proc substitui o [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) o método de processamento de entrada. Nessa implementação do cmdlet Stop-Proc, as chamadas são feitas para gravar as mensagens detalhadas, mensagens de depuração e mensagens de aviso.

> [!NOTE]
> Para obter mais informações sobre como esse método chama o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos, consulte [Criação de um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Gravar uma mensagem detalhada

O [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método é usado para gravar informações gerais de nível de usuário que está relacionadas a condições de erro específicas. O administrador do sistema, em seguida, pode usar essas informações para continuar processando outros comandos. Além disso, qualquer informação escrita usando esse método deve ser localizada, conforme necessário.

O código a seguir desse cmdlet Stop-Proc mostra duas chamadas para o [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método de substituição do [System.Management.Automation.Cmdlet.Processrecord* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Gravar uma mensagem de depuração

O [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método é usado para gravar mensagens de depuração que podem ser usadas para solucionar problemas da operação do cmdlet. A chamada é feita de uma método de processamento de entrada.

> [!NOTE]
> Windows PowerShell também define um `Debug` parâmetro que apresenta ambos detalhado e informações de depuração. Se seu cmdlet oferece suporte a esse parâmetro, ele não precisa chamar [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) no mesmo código que chama [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).

Duas seções de código do cmdlet Stop-Proc exemplo a seguir mostram as chamadas para o [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método de substituição do [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

Essa mensagem de depuração é gravada imediatamente antes [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) é chamado.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Essa mensagem de depuração é gravada imediatamente antes [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) é chamado.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell roteia automaticamente qualquer [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) chamadas para os cmdlets e infra-estrutura de rastreamento. Isso permite que as chamadas de método a ser rastreado para o aplicativo de hospedagem, um arquivo ou um depurador sem precisar fazer qualquer trabalho adicional de desenvolvimento dentro do cmdlet. A entrada de linha de comando a seguir implementa uma operação de rastreamento.

**PS > Parar rastreamento-expression-proc-arquivo proc.log-bloco de notas do comando stop-proc**

## <a name="writing-a-warning-message"></a>Gravar uma mensagem de aviso

O [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método é usado para gravar um aviso quando o cmdlet está prestes a realizar uma operação que pode ter um resultado inesperado, por exemplo, substituição de um arquivo somente leitura.

O código do cmdlet Stop-Proc exemplo a seguir mostra a chamada para o [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método de substituição do [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Gravar uma mensagem de progresso

O [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) é usado para gravar mensagens de progresso quando operações de cmdlet levar um longo período de tempo para ser concluída. Uma chamada para [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passa um [progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) objeto que é enviado ao aplicativo de hospedagem para renderização para o usuário.

> [!NOTE]
> Esse cmdlet Stop-Proc não inclui uma chamada para o [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.

O código a seguir é um exemplo de uma mensagem de progresso, escrito por um cmdlet que está tentando copiar um item.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Exemplo de código

Para o completo C# exemplos de código, consulte [StopProcessSample02 amostra](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets usando objetos .NET. Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet, ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, ele deve ser registrado com o Windows PowerShell por meio de um snap-in do Windows PowerShell. Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testando o Cmdlet

Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando. Vamos testar o exemplo de cmdlet Stop-Proc. Para obter mais informações sobre como usar os cmdlets da linha de comando, consulte o [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- A entrada de linha de comando a seguir usa Proc Stop para interromper o processo de chamada "NOTEPAD", forneça notificações detalhadas e imprimir informações de depuração.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

A seguinte saída é exibida.

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a>Consulte Também

[Criar um Cmdlet que modifica o sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Como criar um Cmdlet do Windows PowerShell](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registrar Cmdlets, provedores e aplicativos de Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
