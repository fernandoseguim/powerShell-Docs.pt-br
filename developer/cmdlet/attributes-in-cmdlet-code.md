---
title: Atributos no código do Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853782"
---
# <a name="attributes-in-cmdlet-code"></a>Atributos no código do cmdlet

Para usar a funcionalidade comum fornecida pelo Windows PowerShell, as classes e propriedades públicas definidas no código do cmdlet são decoradas com atributos. Por exemplo, a definição de classe a seguir usa o atributo de Cmdlet para identificar a classe do Microsoft .NET Framework na qual o **Get-Proc** cmdlet é implementado. (Esse cmdlet é usado como exemplo neste documento e é semelhante ao `Get-Process` cmdlet fornecido pelo Windows PowerShell.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Esses atributos são considerados metadados porque sua implementação é separada da implementação do código do cmdlet. Quando o tempo de execução do Windows PowerShell executa o cmdlet, ele reconhece os atributos e, em seguida, executa a ação apropriada para cada atributo.

Embora você talvez queira implementar sua própria versão da funcionalidade fornecida por meio desses atributos, um cmdlet bom design usa essas funcionalidades comuns.

Para obter mais informações sobre os diferentes atributos que podem ser declaradas em seus cmdlets, consulte [tipos de atributo](./attribute-types.md).

## <a name="see-also"></a>Consulte Também

[Tipos de atributo](./attribute-types.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
