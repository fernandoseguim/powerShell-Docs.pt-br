---
title: Declaração de atributo de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058021"
---
# <a name="cmdlet-attribute-declaration"></a>Declaração de atributo de cmdlet

O atributo de Cmdlet identifica uma classe do Microsoft .NET Framework como um cmdlet e especifica o verbo e substantivo usado para invocar o cmdlet.

## <a name="syntax"></a>Sintaxe

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parâmetros

`VerbName` ([System. String](/dotnet/api/System.String)) necessário. Especifica o verbo do cmdlet. Esse verbo Especifica a ação executada pelo cmdlet. Para obter mais informações sobre os verbos aprovados do cmdlet, consulte [nomes de verbos do Cmdlet](./approved-verbs-for-windows-powershell-commands.md) e [diretrizes de desenvolvimento necessárias](./required-development-guidelines.md).

`NounName` ([System. String](/dotnet/api/System.String)) necessário. Especifica o substantivo do cmdlet. Este substantivo Especifica os recursos que o cmdlet atua. Para obter mais informações sobre nomes de cmdlet, consulte [Cmdlet declaração](./cmdlet-class-declaration.md) e [altamente incentivados diretrizes de desenvolvimento](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System. Boolean](/dotnet/api/System.Boolean)) parâmetro nomeado opcional. `True` indica que o cmdlet oferece suporte a chamadas para o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, que fornece uma maneira para avisar o usuário antes de uma ação que altera o sistema é executada o cmdlet. `False`, o valor padrão, indica que o cmdlet não dá suporte a chamadas para o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. Para obter mais informações sobre solicitações de confirmação, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) parâmetro nomeado opcional. Especifica quando a ação do cmdlet deve ser confirmada por uma chamada para o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) só será chamado quando o valor de ConfirmImpact do cmdlet (por padrão, médio) é igual ou maior que o valor da `$ConfirmPreference` variável. Esse parâmetro deve ser especificado somente quando o `SupportsShouldProcess` parâmetro for especificado.

`DefaultParameterSetName` ([System. String](/dotnet/api/System.String)) parâmetro nomeado opcional. Especifica que o parâmetro padrão definido que o tempo de execução do Windows PowerShell tenta usar quando ele não pode determinar qual parâmetro definido para usar. Observe que essa situação pode ser eliminada, fazendo com que o parâmetro unique de cada parâmetro de definir um parâmetro obrigatório.

Há um caso em que o Windows PowerShell não é possível usar o parâmetro padrão definido, mesmo se for especificado um nome de conjunto de parâmetro padrão. O tempo de execução do Windows PowerShell não pode distinguir entre conjuntos de parâmetros com base apenas no tipo de objeto. Por exemplo, se você tiver um conjunto de parâmetros que usa uma cadeia de caracteres como o caminho do arquivo e outro conjunto que tem um **FileInfo** objeto diretamente, o Windows PowerShell não é possível determinar qual parâmetro definido para usar com base nos valores passados para o cmdlet, nem usa o conjunto de parâmetros padrão. Nesse caso, mesmo se você especificar o que nome do conjunto de um parâmetro padrão, o Windows PowerShell gera uma mensagem de erro de conjunto de parâmetro ambíguo.

`SupportsTransactions` ([System. Boolean](/dotnet/api/System.Boolean)) parâmetro nomeado opcional. `True` indica que o cmdlet pode ser usado em uma transação. Quando `True` for especificado, o tempo de execução do Windows PowerShell adiciona a `UseTransaction` parâmetro à lista de parâmetros do cmdlet. `False`, o valor padrão, indica que o cmdlet não pode ser usado dentro de uma transação.

## <a name="remarks"></a>Comentários

- Juntos, o verbo e substantivo são usados para identificar seu cmdlet registrado e invoque o cmdlet dentro de um script.

- Quando o cmdlet é invocado do console do Windows PowerShell, o comando se parece com o seguinte comando:

**VerbName-NounName**

- Todos os cmdlets que alteram recursos fora do Windows PowerShell deve incluir a `SupportsShouldProcess` palavra-chave quando o atributo do Cmdlet é declarado, que permite que o cmdlet chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método antes que o cmdlet executa sua ação. Se o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamar retorna `false`, a ação não deve ser tomada. Para obter mais informações sobre as solicitações de confirmação geradas pelo [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamam, consulte [solicitando confirmação](./requesting-confirmation-from-cmdlets.md).

O `Confirm` e `WhatIf` parâmetros de cmdlet estão disponíveis apenas para cmdlets que suportam [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamadas.

## <a name="example"></a>Exemplo

A definição de classe a seguir usa o atributo de Cmdlet para identificar a classe do .NET Framework para um **Get-Proc** cmdlet que recupera informações sobre os processos em execução no computador local.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Para obter mais informações sobre o **Get-Proc** cmdlet, consulte [GetProc Tutorial](./getproc-tutorial.md).

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
