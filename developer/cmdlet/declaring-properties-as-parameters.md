---
title: Declarando propriedades como parâmetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861372"
---
# <a name="declaring-properties-as-parameters"></a>Declarar propriedades como parâmetros

Este tópico fornece informações básicas, que você deve compreender antes de você declarar os parâmetros de um cmdlet.

Para declarar os parâmetros de um cmdlet em sua classe do cmdlet, definir as propriedades públicas que representam cada parâmetro e, em seguida, adicione um ou mais atributos de parâmetro para cada propriedade. O tempo de execução do Windows PowerShell usa os atributos de parâmetro para identificar a propriedade como um parâmetro de cmdlet. A sintaxe básica para declarar o atributo de parâmetro é `[Parameter()]`.

Aqui está um exemplo de uma propriedade definida como um parâmetro obrigatório.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Aqui estão algumas coisas a serem lembrados sobre parâmetros.

- Um parâmetro deve ser explicitamente marcado como público. Parâmetros que não são marcados como padrão público para interno e não serão encontrados pelo tempo de execução do Windows PowerShell.

- Parâmetros devem ser definidos como tipos do Microsoft .NET Framework para fornecer melhor validação de parâmetro. Por exemplo, os parâmetros que são restritos a um valor fora do conjunto de valores devem ser definidos como um tipo de enumeração. Parâmetros que usam um valor de identificador de recurso uniforme (URI) devem ser do tipo [System. URI](/dotnet/api/System.Uri).

- Evite parâmetros de cadeias de caracteres básicas para propriedades de texto de forma tudo, exceto livre.

- Você pode adicionar um parâmetro para qualquer número de conjuntos de parâmetros. Para obter mais informações sobre conjuntos de parâmetros, consulte [conjuntos de parâmetros do Cmdlet](./cmdlet-parameter-sets.md).

Windows PowerShell também fornece um conjunto de parâmetros comuns que ficam disponíveis automaticamente para cada cmdlet. Para obter mais informações sobre esses parâmetros e seus aliases, consulte [comum de parâmetros do Cmdlet](./common-parameter-names.md).

## <a name="see-also"></a>Consulte Também

[Parâmetros comuns de cmdlet](./common-parameter-names.md)

[Tipos de parâmetro de Cmdlet](./types-of-cmdlet-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
