---
title: Como validar um conjunto de argumentos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861362"
---
# <a name="how-to-validate-an-argument-set"></a>Como validar um conjunto de argumentos

Este exemplo mostra como especificar uma regra de validação que o tempo de execução do Windows PowerShell pode usar para verificar o argumento do parâmetro antes que o cmdlet é executado. Essa regra de validação fornece um conjunto de valores válidos para o argumento do parâmetro.

> [!NOTE]
> Para obter mais informações sobre a classe que define esse atributo, consulte [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).

## <a name="to-validate-an-argument-set"></a>Para validar um conjunto de argumentos

- Adicione o atributo ValidateSet conforme mostrado no código a seguir. Este exemplo especifica um conjunto de três valores possíveis para o `UserName` parâmetro.

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

Para obter mais informações sobre como declarar esse atributo, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Declaração de atributo ValidateSet](./validateset-attribute-declaration.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md) (Escrevendo um Cmdlet do Windows PowerShell)
