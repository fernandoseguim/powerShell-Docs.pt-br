---
title: Criando um InitialSessionState | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 3a7c47487b632d00643fce0aa082e0dc9a9bb626
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057987"
---
# <a name="creating-an-initialsessionstate"></a>Criar um InitialSessionState

Execute comandos do Windows PowerShell em um runspace. Para hospedar o Windows PowerShell em seu aplicativo, você deve criar uma [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objeto. Cada espaço de execução tem um [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto associado a ele. O [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Especifica as características do espaço de execução, como qual módulos, variáveis e comandos estão disponíveis para esse espaço de execução.

## <a name="create-a-default-initialsessionstate"></a>Criar um padrão InitialSessionState

 O [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)e [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) métodos podem ser usados para criar [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objetos. [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) cria um InitialSessionState com todos os comandos internos carregado, enquanto [ System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) carrega apenas os comandos necessários para hospedar o Windows PowerShell (os comandos do módulo Microsoft.PowerShell.Core.

 Se você quiser limitar ainda mais os comandos disponíveis no aplicativo host, você precisa criar um runspace com restrição. Para obter informações, consulte Criando um runspace com restrição.

 O código a seguir mostra como criar um InitialSessionState, atribuí-lo a um runspace, adicionar comandos a esse espaço de execução, o pipeline e invocar os comandos. Para obter mais informações sobre como adicionar e invocar comandos, consulte Adicionando e invocar comandos.

```csharp

namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell
      // object,and then specify the runspace and commands to the pipeline.
      // and  create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
        foreach (PSObject result in ps.Invoke())
        {
          Console.WriteLine("{0,-20}{1}",
                  result.Members["Name"].Value,
                  result.Members["Value"].Value);
        } // End foreach.

        // Close the runspace to free resources.
        rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a>Consulte Também

 [Criando um runspace com restrição](./creating-a-constrained-runspace.md)
