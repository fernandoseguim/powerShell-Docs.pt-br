---
title: Tipos de parâmetros do Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: 59921a92661482b8d518b82f490c9879643543bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859862"
---
# <a name="types-of-cmdlet-parameters"></a>Tipos de parâmetros de cmdlet

Este tópico descreve os diferentes tipos de parâmetros que você pode declarar nos cmdlets. Parâmetros do cmdlet podem ser posicional, nomeado, obrigatória, opcional ou parâmetros de opção.

## <a name="positional-and-named-parameters"></a>Parâmetros posicionais e nomeados

Todos os parâmetros de cmdlet são parâmetros nomeados ou posicionais. Um parâmetro nomeado exige que você digite o nome do parâmetro e o argumento ao chamar o cmdlet. Um parâmetro posicional requer apenas que você digite os argumentos na ordem relativa. O sistema, em seguida, mapeia o primeiro argumento sem nome para o primeiro parâmetro posicional. O sistema mapeia o segundo argumento sem nome para o segundo parâmetro sem nome e assim por diante. Por padrão, todos os parâmetros de cmdlet são parâmetros nomeados.

Para definir um parâmetro nomeado, omita a `Position` palavra-chave em de **parâmetro** atributo de declaração, conforme mostrado na seguinte declaração de parâmetro.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Para definir um parâmetro posicional, adicione o `Position` palavra-chave no parâmetro de declaração do atributo e, em seguida, especificar uma posição. No exemplo a seguir, o `UserName` parâmetro é declarado como um parâmetro posicional com posição 0. Isso significa que o primeiro argumento da chamada será automaticamente associado a esse parâmetro.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> Cmdlet bom design recomenda que os parâmetros usados com mais ser declarados como parâmetros posicionais para que o usuário não precisa digitar o nome de parâmetro quando o cmdlet é executado.

Parâmetros posicionais e nomeados aceitam argumentos únicos ou vários argumentos separados por vírgulas. São permitidos vários argumentos somente se o parâmetro aceita uma coleção, como uma matriz de cadeias de caracteres. Você pode misturar os parâmetros posicionais e nomeados no mesmo cmdlet. Nesse caso, o sistema recupera os argumentos nomeados primeiro e, em seguida, tenta mapear o restante sem nome argumentos para os parâmetros posicionais.

Os comandos a seguir mostram as diferentes maneiras em que você pode especificar único e vários argumentos para os parâmetros do `Get-Command` cmdlet. Observe que, nas últimas duas amostras **-nome** não precisa ser especificado porque o `Name` parâmetro é definido como um parâmetro posicional.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Parâmetros obrigatórios e opcionais

Você também pode definir parâmetros do cmdlet como parâmetros obrigatórios ou opcionais. (Um parâmetro obrigatório deve ser especificado antes do tempo de execução do Windows PowerShell invoca o cmdlet.)  Por padrão, os parâmetros são definidos como opcionais.

Para definir um parâmetro obrigatório, adicione a `Mandatory` palavra-chave no parâmetro de declaração de atributo e defini-lo como `true`, conforme mostrado na seguinte declaração de parâmetro.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Para definir um parâmetro opcional, omita a `Mandatory` palavra-chave em de **parâmetro** atributo de declaração, conforme mostrado na seguinte declaração de parâmetro.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Parâmetros de opção

O Windows PowerShell fornece um [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) tipo que permite que você definir um parâmetro cujo valor é definido automaticamente como `false` se o parâmetro não for especificado quando o cmdlet chamado. Sempre que possível, use os parâmetros de opção no lugar de parâmetros booleanos.

Considere o exemplo a seguir. Por padrão, vários cmdlets do Windows PowerShell não passe um objeto de saída pelo pipeline. No entanto, esses cmdlets têm um `PassThru` Troque o parâmetro que substitui o comportamento padrão. Se o `PassThru` parâmetro for especificado quando esses cmdlets são chamados, o cmdlet retorna um objeto de saída para o pipeline.

Se você precisa que o parâmetro tenha um valor padrão de `true` quando o parâmetro não for especificado na chamada, considere reverter o sentido do parâmetro. Para obter exemplo, em vez de definir o atributo de parâmetro para um valor booleano `true`, declarar a propriedade como o [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) digite e, em seguida, defina o valor padrão do parâmetro para `false`.

Para definir um parâmetro de opção, declarar a propriedade como o [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) de tipo, conforme mostrado no exemplo a seguir.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Para fazer com que o cmdlet agir sobre o parâmetro quando for especificado, use a seguinte estrutura dentro de uma entrada de métodos de processamento.

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>Consulte Também

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
