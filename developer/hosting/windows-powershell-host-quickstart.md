---
title: Guia de início rápido do Windows PowerShell Host | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 2c6a4bca03ee7f62371cbc296f854464167e5a62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857392"
---
# <a name="windows-powershell-host-quickstart"></a>Início rápido do Windows PowerShell Host

Para hospedar o Windows PowerShell em seu aplicativo, você deve usar o [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe. Essa classe fornece métodos que criam um pipeline de comandos e, em seguida, executem esses comandos em um runspace. A maneira mais simples para criar um aplicativo host é usar o runspace padrão. O runspace padrão contém todos os comandos do Windows PowerShell core. Se você quiser que seu aplicativo para expor somente um subconjunto dos comandos do Windows PowerShell, você deve criar um espaço de execução personalizado.

## <a name="using-the-default-runspace"></a>Usando o runspace padrão

Para começar, vamos usar o runspace padrão e usar os métodos do [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe para adicionar comandos, parâmetros, instruções e scripts para um pipeline.

### <a name="addcommand"></a>AddCommand

Você usa o [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) método da [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class para adicionar comandos ao pipeline. Por exemplo, suponha que você deseja obter a lista de processos em execução no computador. A maneira de executar esse comando é da seguinte maneira.

1. Criar uma [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) objeto.

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

Se você chamar o [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) método mais de uma vez antes de chamar o [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, o resultado do primeiro comando é canalizado para o segundo e assim por diante. Se você não quiser direcionar o resultado de um comando anterior para um comando, adicione-o chamando o [System.Management.Automation.Powershell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) em vez disso.

### <a name="addparameter"></a>AddParameter

O exemplo anterior executa um único comando sem parâmetros. Você pode adicionar parâmetros ao comando, usando o [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) método, por exemplo, o código a seguir obtém uma lista de todos os processos que são nomeados `PowerShell` em execução no máquina.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Você pode adicionar parâmetros adicionais, chamando [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repetidamente.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

Você também pode adicionar um dicionário de valores e nomes de parâmetro ao chamar o [System.Management.Automation.PowerShell.AddParameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) método.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

Você pode simular o envio em lote usando o [System.Management.Automation.PowerShell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) método, que adiciona uma instrução adicional para o final do pipeline, o código a seguir obtém uma lista de processos em execução com o nome `PowerShell`e, em seguida, obtém a lista de serviços em execução.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Você pode executar um script existente chamando o [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método. O exemplo a seguir adiciona um script para o pipeline e o executa. Este exemplo pressupõe que já existe um script chamado `MyScript.ps1` em uma pasta chamada `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Também há uma versão dos [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método que usa um parâmetro booliano denominado `useLocalScope`. Se esse parâmetro for definido como `true`, em seguida, o script é executado no escopo local. O código a seguir executará o script no escopo local.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Criar um espaço de execução personalizado

Embora o runspace padrão usado nos exemplos anteriores carrega todos os comandos do Windows PowerShell core, você pode criar um espaço de execução personalizado que carrega apenas um subconjunto especificado de todos os comandos. Você talvez queira fazer isso para melhorar o desempenho (carregar um número maior de comandos é um impacto no desempenho), ou para restringir a capacidade de executar operações do usuário. Um espaço de execução que expõe somente um número limitado de comandos é chamado de um runspace com restrição. Para criar um runspace com restrição, você deve usar o [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) e [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.

### <a name="creating-an-initialsessionstate-object"></a>Criar um objeto InitialSessionState

Para criar um espaço de execução personalizado, você deve primeiro criar uma [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto. No exemplo a seguir, usamos o [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) para criar um ruspace depois de criar um padrão [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Restringir o espaço de execução

No exemplo anterior, criamos um padrão [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto que carrega todos o principal interno do Windows PowerShell. Podemos também poderia ter chamado a [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) método para criar um objeto de InitialSessionState que carrega apenas os comandos a Mirosoft.PowerShell.Core snap-in. Para criar um runspace mais restrito, você deve criar vazio [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto chamando o [ System.Management.Automation.Runspaces.InitialSessionState.Create*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) método e, em seguida, adicionar comandos para o InitialSessionState.

Usar um espaço de execução que carrega somente os comandos que você especificar fornece um desempenho significativamente melhor.

Use os métodos das [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) classe para definir os cmdlets para o estado de sessão inicial. O exemplo a seguir cria um estado de sessão inicial vazio, em seguida, define e adiciona o `Get-Command` e `Import-Module` comandos para o estado de sessão inicial. Em seguida, criar um runspace restringido por esse estado de sessão inicial e execute os comandos nesse espaço de execução.

Crie o estado de sessão inicial.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Definir e adicionar comandos para o estado de sessão inicial.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Crie e abra o espaço de execução.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Executar um comando e mostrar o resultado.

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

Quando executado, a saída desse código será semelhante ao seguinte.

```powershell
Get-Command
Import-Module
```
