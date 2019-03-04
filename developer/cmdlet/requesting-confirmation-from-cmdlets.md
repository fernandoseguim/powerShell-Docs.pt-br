---
title: Solicitando a confirmação dos Cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: ec441831f5e3231a44c9875d1b6d2bf6280a6965
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853392"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Solicitar confirmação por meio de cmdlets

Cmdlets deve solicitar uma confirmação quando eles estão prestes a fazer uma alteração no sistema que está fora do ambiente do Windows PowerShell. Por exemplo, se um cmdlet estiver prestes a adicionar uma conta de usuário ou interromper um processo, o cmdlet deve requerer confirmação do usuário antes de continuar. Por outro lado, se um cmdlet estiver prestes a alterar uma variável do Windows PowerShell, o cmdlet não precisa requerer confirmação.

Para fazer uma solicitação de confirmação, o cmdlet deve indicar que ele dá suporte a solicitações de confirmação, e ela deve chamar o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos (opcionais) para exibir uma mensagem de solicitação de confirmação.

## <a name="supporting-confirmation-requests"></a>Suporte a solicitações de confirmação

Para dar suporte a solicitações de confirmação, o cmdlet deve definir a `SupportsShouldProcess` parâmetro do atributo ao Cmdlet `true`. Isso permite que o `Confirm` e `WhatIf` parâmetros de cmdlet são fornecidos pelo Windows PowerShell. O `Confirm` parâmetro permite ao usuário controlar se a solicitação de confirmação é exibida. O `WhatIf` parâmetro permite que o usuário determinar se o cmdlet deve exibir uma mensagem ou executar sua ação. Não adicione manualmente os `Confirm` e `WhatIf` parâmetros para um cmdlet.

O exemplo a seguir mostra uma declaração de atributo do Cmdlet que dá suporte a solicitações de confirmação.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Chamar os métodos de solicitação de confirmação

O código do cmdlet, chame o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método antes da operação que modifique o sistema é executada. O cmdlet de design de modo que, se a chamada retorna um valor de `false`, a operação não é executada e o cmdlet processa a próxima operação.

## <a name="calling-the-shouldcontinue-method"></a>Chamar o método ShouldContinue

A maioria dos cmdlets solicitar confirmação usando apenas o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. No entanto, alguns casos podem exigir confirmação adicional. Nesses casos, complementar o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamar com uma chamada para o [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método. Isso permite que o cmdlet ou o provedor para obter um melhor controle do escopo de **Sim para tudo** resposta para o prompt de confirmação.

Se um cmdlet chama o [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método, o cmdlet também deve fornecer um `Force` Troque o parâmetro. Se o usuário especifica `Force` quando o usuário invoca o cmdlet, o cmdlet ainda deve chamar [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), mas deve ignorar a chamada para [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) lançará uma exceção quando ele é chamado de um ambiente não interativo em que o usuário não pode ser solicitado. Adicionando um `Force` parâmetro garante que o comando ainda poderão ser executado quando ele é invocado em um ambiente não interativo.

O exemplo a seguir mostra como chamar [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

O comportamento de um [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamada pode variar dependendo do ambiente em que o cmdlet é invocado. Usando as diretrizes anteriores ajudará a garantir que o cmdlet se comporte de maneira consistente com outros cmdlets, independentemente do ambiente de host.

Para obter um exemplo de chamada a [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, consulte [como solicitar confirmações](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Especifique o nível de impacto

Quando você cria o cmdlet, especifique o nível de impacto (a severidade) da alteração. Para fazer isso, defina o valor da `ConfirmImpact` parâmetro do atributo Cmdlet como alta, média ou baixa. Você pode especificar um valor para `ConfirmImpact` somente quando você também especifica a `SupportsShouldProcess` parâmetro para o cmdlet.

Para a maioria dos cmdlets, você não precisa especificar explicitamente `ConfirmImpact`.  Em vez disso, use a configuração padrão do parâmetro, que é meio. Se você definir `ConfirmImpact` como alta, a operação será confirmada por padrão. Reserve essa configuração para ações altamente prejudicial, como reformatar um volume de disco rígido.

## <a name="calling-non-confirmation-methods"></a>Chamando métodos de não confirmação

Se o cmdlet ou o provedor deve enviar uma mensagem, mas não solicitar confirmação, ele pode chamar os três métodos a seguir. Evite usar o [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método para enviar mensagens de um desses tipos, porque [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) saída é intermisturada com a saída normal de seu cmdlet ou o provedor, que dificulta escrever script.

- Para o usuário de cuidado e continuar com a operação, o cmdlet ou o provedor pode chamar o [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método.

- Para fornecer informações adicionais que o usuário pode recuperar usando o `Verbose` parâmetro, o cmdlet ou o provedor pode chamar o [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método.

- Para fornecer detalhes de nível de depuração para outros desenvolvedores ou para suporte ao produto, o cmdlet ou o provedor pode chamar o [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método. O usuário pode recuperar essas informações usando o `Debug` parâmetro.

Cmdlets e provedores primeiro chamam os seguintes métodos para solicitar uma confirmação antes de tentar executar uma operação que altera um sistema fora do Windows PowerShell:

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Eles fazem isso por meio da chamada a [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, que solicita que o usuário confirme a operação com base em como o usuário chamou o comando.

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
