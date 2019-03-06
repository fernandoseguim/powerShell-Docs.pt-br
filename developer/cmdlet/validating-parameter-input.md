---
title: Validação de parâmetro de entrada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429832"
---
# <a name="validating-parameter-input"></a>Validação de entrada de parâmetro

PowerShell pode validar os argumentos passados para os parâmetros de cmdlet de várias maneiras.
PowerShell pode validar o comprimento, intervalo e o padrão de caracteres do argumento.
Ele pode validar o número de argumentos disponíveis (a contagem).
Essas regras de validação são definidas por atributos de validação que são declarados com o atributo de parâmetro em propriedades públicas da classe do cmdlet.

Para validar um argumento de parâmetro, o tempo de execução do PowerShell usa as informações fornecidas pelos atributos de validação para confirmar se o valor do parâmetro antes que o cmdlet é executado.
Se a entrada de parâmetro não for válida, o usuário recebe uma mensagem de erro.
Cada parâmetro de validação define uma regra de validação que é imposta pelo PowerShell.

PowerShell impõe as regras de validação com base nos seguintes atributos.

### <a name="validatecount"></a>ValidateCount

Especifica o número mínimo e máximo de argumentos que aceite um parâmetro.
Para obter mais informações, consulte [declaração de atributo ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Especifica o número mínimo e máximo de caracteres no argumento do parâmetro.
Para obter mais informações, consulte [declaração de atributo ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Especifica uma expressão regular que valida o argumento do parâmetro.
Para obter mais informações, consulte [declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Especifica os valores mínimos e máximo do argumento do parâmetro.
Para obter mais informações, consulte [declaração de atributo ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Especifica os valores válidos para o argumento do parâmetro.
Para obter mais informações, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Consulte Também

[Como validar a entrada de parâmetro](./how-to-validate-parameter-input.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
