---
title: Criando um runspace com restrição | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59125e65-7030-40bb-9926-756120b2d952
caps.latest.revision: 5
ms.openlocfilehash: 3c70296cb22c325ace10dc04c8b1fd941742857b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862992"
---
# <a name="creating-a-constrained-runspace"></a>Criar um runspace com restrição

Por motivos de segurança ou de desempenho, você talvez queira restringir os comandos do Windows PowerShell disponíveis para seu aplicativo host. Para fazer isso, você cria uma vazia [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) chamando o [System.Management.Automation.Runspaces.Initialsessionstate.Create*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) método, e, em seguida, adicione somente os comandos que você deseja disponibilizar.

 Usar um espaço de execução que carrega somente os comandos que você especificar fornece um desempenho significativamente melhor.

 Use os métodos das [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) classe para definir os cmdlets para o estado de sessão inicial.

 Você também pode fazer comandos privada. Comandos privados podem ser usados pelo aplicativo host, mas não por usuários do aplicativo.

## <a name="adding-commands-to-an-empty-runspace"></a>Adicionando comandos a um runspace vazio

 O exemplo a seguir demonstra como criar um InitialSessionState vazio e adicionar comandos a ele.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using Microsoft.PowerShell.Commands;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class Runspace10b
  {
    /// <summary>
    /// This sample shows how to create an empty initial session state,
    /// how to add commands to the session state, and then how to create a
    /// runspace that has only those two commands. A PowerShell object
    /// is used to run the Get-Command cmdlet to show that only two commands
    /// are available.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create an empty InitialSessionState and then add two commands.
      InitialSessionState iss = InitialSessionState.Create();

      // Add the Get-Process and Get-Command cmdlets to the session state.
      SessionStateCmdletEntry ssce1 = new SessionStateCmdletEntry(
                                                            "get-process",
                                                            typeof(GetProcessCommand),
                                                            null);
      iss.Commands.Add(ssce1);

      SessionStateCmdletEntry ssce2 = new SessionStateCmdletEntry(
                                                            "get-command",
                                                            typeof(GetCommandCommand),
                                                            null);
      iss.Commands.Add(ssce2);

      // Create a runspace.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Create a pipeline with the Get-Command command.
          powershell.AddCommand("get-command");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Verb                 Noun");
          Console.WriteLine("----------------------------");

          // Display each result object.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                             "{0,-20} {1}",
                             result.Members["verb"].Value,
                             result.Members["Noun"].Value);
          }
        }

        // Close the runspace and release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="making-commands-private"></a>Comandos de tornar privados

 Você também pode fazer um comando em particular, definindo-o do [System.Management.Automation.Commandinfo.Visibility*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) propriedade [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private) . O aplicativo host e outros comandos podem chamar esse comando, mas não de usuário do aplicativo. No exemplo a seguir, o [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) comando é privado.
Você também pode fazer um comando em particular, definindo-o do [System.Management.Automation.Commandinfo.Visibility*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) propriedade [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private) . O aplicativo host e outros comandos podem chamar esse comando, mas não de usuário do aplicativo. No exemplo a seguir, o [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) comando é privado.

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a>Consulte Também

 [Criando um InitialSessionState](./creating-an-initialsessionstate.md)
