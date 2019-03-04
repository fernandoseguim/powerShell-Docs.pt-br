---
title: Declaração de atributo ValidatePattern | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858872"
---
# <a name="validatepattern-attribute-declaration"></a>Declaração de atributo ValidatePattern

O atributo ValidatePattern Especifica um padrão de expressão regular que valida o argumento de um parâmetro de cmdlet. Esse atributo também pode ser usado por funções do Windows PowerShell.

Quando ValidatePattern é chamado dentro de um cmdlet, o tempo de execução do Windows PowerShell converte o argumento do parâmetro de cmdlet em uma cadeia de caracteres e, em seguida, compara o padrão fornecido pelo atributo ValidatePattern essa cadeia de caracteres. O cmdlet é executado somente se corresponderem a representação de cadeia de caracteres convertida de argumento e o padrão fornecido. Se eles não coincidirem, um erro é gerado pelo tempo de execução do Windows PowerShell.

## <a name="syntax"></a>Sintaxe

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parâmetros

`RegexString` ([System. String](/dotnet/api/System.String)) necessário. Especifica uma expressão regular que valida o argumento do parâmetro.

Opções ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) parâmetro nomeado opcional. Especifica uma combinação bit a bit dos [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) sinalizadores que especificam opções de expressões regulares.

## <a name="remarks"></a>Comentários

- Esse atributo pode ser usado apenas uma vez por parâmetro.

- Você pode usar o `Option` parâmetro do atributo para definir ainda mais o padrão. Por exemplo, você pode fazer o padrão de maiusculas e minúsculas.

- Se esse atributo é aplicado a uma coleção, cada elemento da coleção deve corresponder ao padrão.

- O atributo ValidatePattern é definido pela [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) classe.

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
