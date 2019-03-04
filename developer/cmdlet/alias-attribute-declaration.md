---
title: Declaração de atributo de alias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855042"
---
# <a name="alias-attribute-declaration"></a>Declaração de atributo de alias

O atributo de Alias permite que o usuário especifique nomes diferentes para um parâmetro de cmdlet. Aliases podem ser usados para fornecer os atalhos para um nome de parâmetro, ou eles podem fornecer nomes diferentes que são apropriados para cenários diferentes.

## <a name="syntax"></a>Sintaxe

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parâmetros

`aliasName` (String[]) Necessário. Especifica um conjunto de nomes separados por vírgulas de alias para o parâmetro de cmdlet.

## <a name="remarks"></a>Comentários

- O atributo de Alias é usado com o atributo de parâmetro quando você especificar um parâmetro de cmdlet. Para obter mais informações sobre como declarar esses atributos, consulte [como declarar parâmetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).

- Cada nome de alias deve ser exclusivo dentro de um cmdlet. Windows PowerShell não procura nomes de alias duplicado.

- O atributo de Alias é usado uma vez para cada parâmetro em um cmdlet.

- O atributo de Alias é definido pela [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) classe.

## <a name="see-also"></a>Consulte Também

[Aliases de parâmetro](./parameter-aliases.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
