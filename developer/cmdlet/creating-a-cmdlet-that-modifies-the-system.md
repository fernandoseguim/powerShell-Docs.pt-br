---
title: Criação de um Cmdlet que modifica o sistema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055131"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Criar um cmdlet que modifica o sistema

Às vezes, um cmdlet deve modificar o estado de execução do sistema, não apenas o estado do tempo de execução do Windows PowerShell. Nesses casos, o cmdlet deve permitir ao usuário uma oportunidade para confirmar se deseja ou não fazer a alteração.

Para dar suporte à confirmação de um cmdlet deve fazer duas coisas.

- Declarar que o cmdlet oferece suporte a confirmação quando você especifica o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo definindo a palavra-chave SupportsShouldProcess como `true`.

- Chame [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) durante a execução do cmdlet (conforme mostrado no exemplo a seguir).

Com o suporte à confirmação, um cmdlet expõe o `Confirm` e `WhatIf` parâmetros que são fornecidos pelo Windows PowerShell e também atende as diretrizes de desenvolvimento para cmdlets (para obter mais informações sobre as diretrizes de desenvolvimento do cmdlet, consulte [ Diretrizes de desenvolvimento do cmdlet](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>Alterando o sistema

O ato de "alterando o sistema" se refere a qualquer cmdlet que potencialmente altera o estado do sistema fora do Windows PowerShell. Por exemplo, interromper um processo, habilitar ou desabilitar uma conta de usuário ou adicionando uma linha em uma tabela de banco de dados são todas as alterações no sistema que devem ser confirmados. Por outro lado, as operações que leia dados ou estabeleçam conexões transitórias não alteram o sistema e geralmente não exigem a confirmação. Confirmação também não é necessária para ações cujo efeito é limitado para dentro do runtime do Windows PowerShell, como `set-variable`. Os cmdlets que podem ou não pode fazer uma alteração persistente deve declarar `SupportsShouldProcess` e chame [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) somente se eles estiverem prestes a fazer uma alteração persistente.

> [!NOTE]
> Confirmação de ShouldProcess se aplica somente aos cmdlets. Se um comando ou script modifica o estado de execução de um sistema chamando diretamente as propriedades ou métodos do .NET, ou por aplicativos de chamada fora do Windows PowerShell, essa forma de confirmação não estará disponível.

## <a name="the-stopproc-cmdlet"></a>O StopProc Cmdlet

Este tópico descreve um cmdlet Stop-Proc que tenta interromper os processos que são recuperados usando o cmdlet Get-Proc (descrito na [criando seu primeiro Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Os tópicos nesta seção incluem o seguinte:

- [Definindo o Cmdlet](#Defining-the-Cmdlet)

- [Definir parâmetros para modificação do sistema](#Defining-Parameters-for-System-Modification)

- [Substituindo uma método de processamento de entrada](#Overriding-an-Input-Processing-Method)

- [Chamar o método ShouldProcess](#Calling-the-ShouldProcess-Method)

- [Chamar o método ShouldContinue](#Calling-the-ShouldContinue-Method)

- [Parar processamento de entrada](#Stopping-Input-Processing)

- [Exemplo de código](#Code-Sample)

- [Definindo tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o Cmdlet](#Building-the-Cmdlet)

- [Testando o Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definindo o Cmdlet

A primeira etapa na criação de cmdlet sempre é o cmdlet de nomenclatura e declarar a classe .NET que implementa o cmdlet. Porque você está escrevendo um cmdlet para alterar o sistema, ele deve ser nomeado adequadamente. Este processos de sistema do cmdlet é interrompido, portanto, o nome do verbo escolhido aqui é "Parar", definido pela [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe, com o substantivo "Processo" para indicar que o cmdlet interrompe processos. Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

A seguir está a definição de classe para esse cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Lembre-se que no [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaração, o `SupportsShouldProcess` palavra-chave do atributo é definido como `true` para habilitar o cmdlet fazer chamadas para [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Sem este conjunto de palavra-chave, o `Confirm` e `WhatIf` parâmetros não estarão disponíveis para o usuário.

### <a name="extremely-destructive-actions"></a>Ações destrutivas extremamente

Algumas operações são extremamente nocivo como reformatar uma partição de disco de rígido de Active Directory. Nesses casos, o cmdlet deve ser definido `ConfirmImpact`  =  `ConfirmImpact.High` ao declarar o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo. Essa configuração força o cmdlet para solicitar a confirmação de usuário, mesmo quando o usuário não especificou o `Confirm` parâmetro. No entanto, os desenvolvedores de cmdlet devem evitar o uso excessivo `ConfirmImpact` para operações que são apenas potencialmente destrutivas, como excluir uma conta de usuário. Lembre-se de que, se `ConfirmImpact` é definido como [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).

Da mesma forma, algumas operações são improvável de ser destrutivo, embora eles teoricamente modificam o estado de execução de um sistema fora do Windows PowerShell. Esses cmdlets pode definir `ConfirmImpact` à [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Isso irá ignorar as solicitações de confirmação em que o usuário pediu para confirmar as operações somente impacto médio e alto impacto.

## <a name="defining-parameters-for-system-modification"></a>Definir parâmetros para modificação do sistema

Esta seção descreve como definir os parâmetros do cmdlet, incluindo aqueles que são necessários para o sistema de suporte à modificação. Ver [adicionando parâmetros essa entrada de linha de comando de processo](./adding-parameters-that-process-command-line-input.md) se você precisar de informações gerais sobre como definir parâmetros.

O cmdlet Stop-Proc define três parâmetros: `Name`, `Force`, e `PassThru`.

O `Name` parâmetro corresponde à `Name` propriedade do objeto de entrada do processo. Lembre-se que o `Name` parâmetro neste exemplo é obrigatório, pois o cmdlet falhará se não tiver um processo nomeado para parar.

O `Force` parâmetro permite que o usuário substituir chamadas para [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Na verdade, qualquer cmdlet que chama [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) deve ter uma `Force` parâmetro, de modo que quando `Force` for especificado, o cmdlet ignora a chamada para [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) e prossegue com a operação. Lembre-se de que isso não afeta chamadas para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

O `PassThru` parâmetro permite que o usuário indicar se o cmdlet passa um objeto de saída por meio do pipeline, nesse caso, depois que um processo é interrompido. Lembre-se de que esse parâmetro é vinculado ao cmdlet em si em vez de para uma propriedade do objeto de entrada.

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

O cmdlet deve substituir uma método de processamento de entrada. O código a seguir ilustra a [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) usada no cmdlet Stop-Proc exemplo de substituição. Para cada solicitado o nome do processo, esse método garante que o processo não é um processo especial, tenta interromper o processo e, em seguida, envia um objeto de saída se o `PassThru` parâmetro for especificado.

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a>Chamar o método ShouldProcess

A método do seu cmdlet de processamento de entrada deve chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para confirmar a execução de uma operação antes que uma alteração (por exemplo, exclusão de arquivos) é feita para o estado de execução do sistema. Isso permite que o tempo de execução do Windows PowerShell fornecer o comportamento correto de "WhatIf" e "Confirmar" dentro do shell.

> [!NOTE]
> Se um cmdlet informa que ele oferece suporte deve processar e não fizer a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamar, o usuário pode modificar o sistema inesperadamente.

A chamada para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) envia o nome do recurso a ser alterado para o usuário, com o tempo de execução do Windows PowerShell levando em consideração quaisquer configurações de linha de comando ou variáveis de preferências determinar o que deve ser exibido ao usuário.

O exemplo a seguir mostra a chamada para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) de substituição do [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método no exemplo Cmdlet Stop-Proc.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Chamar o método ShouldContinue

A chamada para o [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método envia uma mensagem de secundária para o usuário. Essa chamada é feita após a chamada para [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) retorna `true` e, se o `Force` parâmetro não foi definido como `true`. O usuário pode, em seguida, fornecer comentários para dizer se a operação deve continuar. Suas chamadas de cmdlet [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) como uma verificação adicional para modificações no sistema potencialmente perigoso ou quando você deseja fornecer opções Sim para todos e não para todos para o usuário.

O exemplo a seguir mostra a chamada para [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) de substituição do [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método no exemplo Cmdlet Stop-Proc.

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a>Parar processamento de entrada

A método de um cmdlet que faz modificações no sistema de processamento de entrada deve fornecer uma maneira de parar o processamento de entrada. No caso desse cmdlet Stop-Proc, é feita uma chamada do [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para o [System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill) método. Porque o `PassThru` parâmetro é definido como `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) também chama [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) para enviar o objeto de processo para o pipeline.

## <a name="code-sample"></a>Exemplo de código

Para o completo C# exemplos de código, consulte [StopProcessSample01 amostra](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definindo tipos de objeto e formatação

Windows PowerShell passa informações entre cmdlets usando objetos .net. Consequentemente, talvez seja necessário definir seu próprio tipo de um cmdlet ou o cmdlet talvez precise estender um tipo existente fornecido pelo outro cmdlet. Para obter mais informações sobre como definir novos tipos ou estender os tipos existentes, consulte [estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Criando o Cmdlet

Depois de implementar um cmdlet, ele deve ser registrado com o Windows PowerShell por meio de um snap-in do Windows PowerShell. Para obter mais informações sobre como registrar cmdlets, consulte [como registrar Cmdlets, provedores e aplicativos Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testando o Cmdlet

Quando seu cmdlet tiver sido registrado com o Windows PowerShell, você pode testá-lo executando-o na linha de comando. Aqui estão vários testes que testam o cmdlet Stop-Proc. Para obter mais informações sobre como usar os cmdlets da linha de comando, consulte o [Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Inicie o Windows PowerShell e use o cmdlet Stop-Proc para parar o processamento, conforme mostrado abaixo. Como o cmdlet especifica a `Name` parâmetro como obrigatórias, as consultas de cmdlet para o parâmetro.

    ```powershell
    PS> stop-proc
    ```

A seguinte saída é exibida.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- Agora vamos usar o cmdlet para interromper o processo de chamada "NOTEPAD". O cmdlet solicitará que você confirme a ação.

    ```powershell
    PS> stop-proc -Name notepad
    ```

A seguinte saída é exibida.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Use Stop-Proc conforme mostrado para interromper o processo crítico denominado "WINLOGON". Você é solicitado e avisado sobre como executar esta ação porque causará o reinicialização do sistema operacional.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

A seguinte saída é exibida.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- Agora, vamos tentar interromper o processo do WINLOGON sem receber um aviso. Lembre-se de que essa entrada de comando usa o `Force` parâmetro para ignorar o aviso.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

A seguinte saída é exibida.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Consulte Também

[Adicionar parâmetros que processam a entrada de linha de comando](./adding-parameters-that-process-command-line-input.md)

[Estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registrar Cmdlets, provedores e aplicativos de Host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK do Windows PowerShell](../windows-powershell-reference.md)

[Exemplos de cmdlet](./cmdlet-samples.md)