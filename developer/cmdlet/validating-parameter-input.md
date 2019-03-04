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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858842"
---
# <a name="validating-parameter-input"></a>Validação de entrada de parâmetro

Windows PowerShell pode validar os argumentos passados para os parâmetros de cmdlet de várias maneiras. Windows PowerShell pode validar o comprimento, intervalo e o padrão de caracteres do argumento. Ele pode validar o número de argumentos disponíveis (a contagem). Essas regras de validação são definidas por atributos de validação que são declarados com o atributo de parâmetro em propriedades públicas da classe do cmdlet.

Para validar um argumento de parâmetro, o tempo de execução do Windows PowerShell usa as informações fornecidas pelos atributos de validação para confirmar se o valor do parâmetro antes que o cmdlet é executado. Se a entrada de parâmetro não for válida, o usuário recebe uma mensagem de erro. Cada parâmetro de validação define uma regra de validação que é imposta pelo Windows PowerShell.

Windows PowerShell impõe as regras de validação com base nos seguintes atributos.

ValidateCount Especifica o número mínimo e máximo de argumentos que aceite um parâmetro. Para obter mais informações sobre a sintaxe usada para declarar esse atributo, consulte [declaração de atributo ValidateCount](./validatecount-attribute-declaration.md).

ValidateLength Especifica o número mínimo e máximo de caracteres no argumento do parâmetro. Para obter mais informações sobre a sintaxe usada para declarar esse atributo, consulte [declaração de atributo ValidateLength](./validatelength-attribute-declaration.md).

ValidatePattern Especifica uma expressão regular que valida o argumento do parâmetro. Para obter mais informações sobre a sintaxe usada para declarar esse atributo, consulte [declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md).

ValidateRange Especifica os valores mínimos e máximo do argumento do parâmetro. Para obter mais informações sobre a sintaxe usada para declarar esse atributo, consulte [declaração de atributo ValidateRange](./validaterange-attribute-declaration.md).

ValidateSet Especifica os valores válidos para o argumento do parâmetro. Para obter mais informações sobre a sintaxe usada para declarar esse atributo, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Consulte Também

[Como validar a entrada de parâmetro](./how-to-validate-parameter-input.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
