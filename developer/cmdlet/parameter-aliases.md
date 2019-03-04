---
title: Aliases de parâmetro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853312"
---
# <a name="parameter-aliases"></a>Aliases de parâmetro

Os parâmetros de cmdlets também podem ter aliases. Você pode usar os aliases em vez dos nomes de parâmetro, quando você digita ou especifica o parâmetro em um comando.

## <a name="benefits-of-using-aliases"></a>Benefícios do uso de Aliases

A adição de aliases para parâmetros fornece os seguintes benefícios.

- Você pode fornecer um atalho para que o usuário não precisa usar o nome de parâmetro completa quando o cmdlet for chamado. Por exemplo, você pode usar o alias "CN" em vez do nome do parâmetro "NomeDoComputador".

- Se você quiser fornecer nomes diferentes para o mesmo parâmetro, você pode definir vários aliases. Você talvez queira definir vários aliases, se você tiver que trabalhar com vários grupos de usuários que se referem aos mesmos dados de maneiras diferentes.

- Você pode fornecer com versões anteriores compatibilidade para os scripts existentes se o nome de um parâmetro for alterado.

- Usando o atributo de Alias, juntamente com o atributo ValueFromPipelineByName, você pode definir um parâmetro que permite que seu cmdlet associar a diferentes tipos de objeto. Por exemplo, digamos que você tinha dois objetos de tipos diferentes e o primeiro objeto tinha uma propriedade de gravador e o segundo objeto tinha uma propriedade do editor. Se seu cmdlet tinha um parâmetro que tinha aliases escritor e editor e o cmdlet aceita entrada do pipeline com base em nomes de propriedade, seu cmdlet pôde ligar aos dois objetos usando dois aliases de parâmetro.

Para obter mais informações sobre aliases que podem ser usados com parâmetros específicos, consulte [nomes de parâmetro comuns](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Definir Aliases de parâmetro

Para definir um alias para um parâmetro, declare o atributo de Alias, conforme mostrado na seguinte declaração de parâmetro. Neste exemplo, vários aliases são definidos para o mesmo parâmetro. (Para obter mais informações, consulte[como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).)

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>Consulte Também

[Nomes de parâmetro comuns](./common-parameter-names.md)

[Como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
