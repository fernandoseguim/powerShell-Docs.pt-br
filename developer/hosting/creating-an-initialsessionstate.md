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
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="8d6d3-102">Criar um InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="8d6d3-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="8d6d3-103">Execute comandos do Windows PowerShell em um runspace.</span><span class="sxs-lookup"><span data-stu-id="8d6d3-103">Windows PowerShell commands run in a runspace.</span></span> <span data-ttu-id="8d6d3-104">Para hospedar o Windows PowerShell em seu aplicativo, você deve criar uma [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objeto.</span><span class="sxs-lookup"><span data-stu-id="8d6d3-104">To host Windows PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span> <span data-ttu-id="8d6d3-105">Cada espaço de execução tem um [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto associado a ele.</span><span class="sxs-lookup"><span data-stu-id="8d6d3-105">Every runspace has an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span> <span data-ttu-id="8d6d3-106">O [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Especifica as características do espaço de execução, como qual módulos, variáveis e comandos estão disponíveis para esse espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="8d6d3-106">The [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="8d6d3-107">Criar um padrão InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="8d6d3-107">Create a default InitialSessionState</span></span>

 <span data-ttu-id="8d6d3-108">O [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)e [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) métodos podem ser usados para criar [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objetos.</span><span class="sxs-lookup"><span data-stu-id="8d6d3-108">The [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)and [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods can be used to create [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objects.</span></span> <span data-ttu-id="8d6d3-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) cria um InitialSessionState com todos os comandos internos carregado, enquanto [ System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) carrega apenas os comandos necessários para hospedar o Windows PowerShell (os comandos do módulo Microsoft.PowerShell.Core.</span><span class="sxs-lookup"><span data-stu-id="8d6d3-109">[System.Management.Automation.Runspaces.Initialsessionstate.Createdefault\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) creates an InitialSessionState with all of the built-in commands loaded, while [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) loads only the commands required to host Windows PowerShell (the commands from the Microsoft.PowerShell.Core module.</span></span>

 <span data-ttu-id="8d6d3-110">Se você quiser limitar ainda mais os comandos disponíveis no aplicativo host, você precisa criar um runspace com restrição.</span><span class="sxs-lookup"><span data-stu-id="8d6d3-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span> <span data-ttu-id="8d6d3-111">Para obter informações, consulte Criando um runspace com restrição.</span><span class="sxs-lookup"><span data-stu-id="8d6d3-111">For information, see Creating a constrained runspace.</span></span>

 <span data-ttu-id="8d6d3-112">O código a seguir mostra como criar um InitialSessionState, atribuí-lo a um runspace, adicionar comandos a esse espaço de execução, o pipeline e invocar os comandos.</span><span class="sxs-lookup"><span data-stu-id="8d6d3-112">The following code shows how to create an InitialSessionState, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span> <span data-ttu-id="8d6d3-113">Para obter mais informações sobre como adicionar e invocar comandos, consulte Adicionando e invocar comandos.</span><span class="sxs-lookup"><span data-stu-id="8d6d3-113">For more information about adding and invoking commands, see Adding and invoking commands.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8d6d3-114">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8d6d3-114">See Also</span></span>

 [<span data-ttu-id="8d6d3-115">Criando um runspace com restrição</span><span class="sxs-lookup"><span data-stu-id="8d6d3-115">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
