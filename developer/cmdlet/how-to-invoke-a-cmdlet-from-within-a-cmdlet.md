---
title: Como invocar um Cmdlet de dentro de um Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055896"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Como invocar um cmdlet de dentro de um cmdlet

Este exemplo mostra como chamar um cmdlet de dentro de outro cmdlet, que permite que você adicionar a funcionalidade do cmdlet invocado para o cmdlet que você está desenvolvendo. Neste exemplo, o `Get-Process` cmdlet é invocado para obter os processos que estão em execução no computador local. A chamada para o `Get-Process` cmdlet é equivalente ao comando a seguir. Esse comando recupera todos os processos cujos nomes começam com os caracteres "a" a "t".

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> Você pode chamar apenas esses cmdlets que derivam diretamente de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Você não pode chamar um cmdlet que deriva de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Para invocar um cmdlet de dentro de um cmdlet

1. Certifique-se de que o assembly que define o cmdlet a ser invocado é referenciado e que apropriado `using` instrução é adicionada. Neste exemplo, os seguintes namespaces são adicionados.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. Na entrada do método do cmdlet de processamento, crie uma nova instância do cmdlet a ser invocado. Neste exemplo, um objeto do tipo [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) é criado junto com a cadeia de caracteres que contém os argumentos que são usados quando o cmdlet é invocado.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Chame o [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método para invocar o `Get-Process` cmdlet.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Exemplo

Neste exemplo, o `Get-Process` cmdlet é invocado de dentro de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método de um cmdlet.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
