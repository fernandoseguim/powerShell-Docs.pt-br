---
title: Exemplo de Runspace01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: eec9c616fc6d5240db185f764a3ea2c8f9575d03
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057902"
---
# <a name="runspace01-sample"></a>Amostra Runspace01

Este exemplo mostra como usar o [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe a ser executada a [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet sincronicamente. O [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet retorna [Diagnostics](/dotnet/api/System.Diagnostics.Process) objetos para cada processo em execução no computador local. Os valores de [System.Diagnostics.Process.Processname*](/dotnet/api/System.Diagnostics.Process.ProcessName) e [System.Diagnostics.Process.Handlecount*](/dotnet/api/System.Diagnostics.Process.Handlecount) propriedades, em seguida, são extraídas de objetos retornados e exibidas em um console do janela.

## <a name="requirements"></a>Requisitos

 Este exemplo requer o Windows PowerShell 2.0.

## <a name="demonstrates"></a>Demonstra

- Criando um [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto para executar um comando.

- Adicionando um comando para o pipeline do [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

- Executar o comando de forma síncrona.

- Usando o [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objetos extrair propriedades de objetos retornados pelo comando.

## <a name="example"></a>Exemplo

 Este exemplo executa o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet de forma síncrona no runspace padrão fornecido pelo Windows PowerShell.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>Consulte Também
