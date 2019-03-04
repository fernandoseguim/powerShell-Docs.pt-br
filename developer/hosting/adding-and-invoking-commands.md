---
title: Adicionando e invocar comandos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 31371797ee57f07075da3436e0b42b2ca01aaffd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857342"
---
# <a name="adding-and-invoking-commands"></a>Adicionar e invocar comandos

Depois de criar um espaço de execução, você pode adicionar PowerShellcommands do Windows e scripts para um pipeline e, em seguida, invocar os pipelines de forma síncrona ou assíncrona.

## <a name="creating-a-pipeline"></a>Criar um pipeline

 O [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe fornece vários métodos para adicionar comandos, parâmetros e scripts para o pipeline. Você pode invocar o pipeline de forma síncrona, chamando uma sobrecarga da [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, ou de forma assíncrona, chamando uma sobrecarga da [ System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) e, em seguida, o [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.

### <a name="addcommand"></a>AddCommand

1. Criar uma [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Adicione o comando que você deseja executar.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Invocar o comando.

   ```csharp
   ps.Invoke();
   ```

 Se você chamar o [System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) método mais de uma vez antes de chamar o [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, o resultado do primeiro comando é canalizado para o segundo e assim por diante. Se você não quiser direcionar o resultado de um comando anterior para um comando, adicione-o chamando o [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) em vez disso.

### <a name="addparameter"></a>AddParameter

 O exemplo anterior executa um único comando sem parâmetros. Você pode adicionar parâmetros ao comando, usando o [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) método, por exemplo, o código a seguir obtém uma lista de todos os processos que são nomeados `PowerShell` em execução no máquina.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 Você pode adicionar parâmetros adicionais, chamando [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repetidamente.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 Você também pode adicionar um dicionário de valores e nomes de parâmetro ao chamar o [System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) método.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 Você pode simular o envio em lote usando o [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) método, que adiciona uma instrução adicional para o final do pipeline, o código a seguir obtém uma lista de processos em execução com o nome `PowerShell`e, em seguida, obtém a lista de serviços em execução.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 Você pode executar um script existente chamando o [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método. O exemplo a seguir adiciona um script para o pipeline e o executa. Este exemplo pressupõe que já existe um script chamado `MyScript.ps1` em uma pasta chamada `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Também há uma versão dos [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método que usa um parâmetro booliano denominado `useLocalScope`. Se esse parâmetro for definido como `true`, em seguida, o script é executado no escopo local. O código a seguir executará o script no escopo local.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Invocar um pipeline de forma síncrona

 Depois de adicionar elementos ao pipeline, você invocá-lo. Para invocar o pipeline de forma síncrona, você pode chamar uma sobrecarga da [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método. O exemplo a seguir mostra como chamar sincronamente um pipeline.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a>Invocar um pipeline de forma assíncrona

 Invocar um pipeline de forma assíncrona, chamando uma sobrecarga da [System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) para criar um [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) objeto e, em seguida, chamar o [ System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.

 O exemplo a seguir mostra como invocar um pipeline asynchronoulsy.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediatly
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a>Consulte Também

 [Criando um InitialSessionState](./creating-an-initialsessionstate.md)

 [Criando um runspace com restrição](./creating-a-constrained-runspace.md)
